---
title: マイニング モデルとマイニング構造のカスタマイズ |Microsoft Docs
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7c4c951d294ab57e19b4114380fd4692b9fc8151
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68183773"
---
# <a name="customize-mining-models-and-structure"></a>マイニング モデルとマイニング構造のカスタマイズ
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  現在のビジネス ニーズに合ったアルゴリズムを選択した後、マイニング モデルを次の方法でカスタマイズできます。モデルをカスタマイズすると、より良い結果を得られる場合があります。  
  
-   モデルで使用するデータ列、または列の使用法や、コンテンツの種類、分離メソッドを変更する。  
  
-   マイニング モデルに対するフィルターを作成して、モデルのトレーニングに使用するデータを制限する。  
  
-   データを分析するために使用されたアルゴリズムを変更する。  
  
-   アルゴリズム パラメーターを設定して、しきい値やツリーの分割などの重要な条件を制御する。  
  
 このトピックでは、これらのオプションについて説明します。  
  
## <a name="changing-data-used-by-the-model"></a>モデルで使用するデータの変更  
 モデルで使用するデータ列や、そのデータの使用方法および処理方法に関する決定は、分析の結果に大きく影響します。 以下のトピックには、それらの選択に役立つ情報が含まれています。  
  
### <a name="using-feature-selection"></a>機能の選択の使用  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のほとんどのデータ マイニング アルゴリズムでは、 *機能の選択* というプロセスを使用して、最も役に立つ属性のみを選択してモデルに追加します。 列や属性の数を減らすと、パフォーマンスやモデルの品質を向上させることができます。 使用できる機能の選択の方法は、選択するアルゴリズムによって異なります。  
  
 [機能の選択 (データ マイニング)](../../analysis-services/data-mining/feature-selection-data-mining.md)  
  
### <a name="changing-usage"></a>使用方法の変更  
 マイニング モデルに含まれる列と各列の使用方法を変更できます。 予期したとおりの結果が得られない場合は、入力として使用した列を調べて、選択した列が適切かどうかを検討する必要があります。さらに、データの処理を向上させるためにできることがあるかどうかについても検討します。たとえば、次のようなことが考えられます。  
  
-   誤って数値としてラベルが付けられたカテゴリ変数を特定する。  
  
-   カテゴリを追加して、属性の数を減らし、相関関係をわかりやすくする。  
  
-   数値をビン分割または分離する方法を変更する。  
  
-   一意の値が多数含まれている列や実際には参照データであるが分析に適さない列 (住所、ミドル ネームなど) を削除する。  
  
 列をマイニング構造から物理的に削除する必要はありません。列としてのフラグを設定することができますのみ**無視**します。 列はマイニング モデルから削除されますが、その列は引き続き構造内の他のマイニング モデルで使用することや、ドリルスルー クエリで参照することができます。  
  
### <a name="creating-aliases-for-model-columns"></a>モデル列の別名の作成  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] でマイニング モデルを作成すると、マイニング構造内の列と同じ名前が使用されます。 マイニング モデルのすべての列に、別名を追加できます。 こうすると、列の内容や使用法がわかりやすくなったり、名前が短くなるためクエリを作成しやすくなったりします。 別名は、列のコピーを作成し、わかりやすい名前を付ける場合にも便利です。  
  
 別名を作成するには、マイニング モデル列の **Name** プロパティを編集します。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で元の名前は列の ID として引き続き使用され、 **Name** に入力した新しい値が列の別名となります。この別名は、グリッド内で列の使用法の横にかっこで囲まれて表示されます。  
  
 ![エイリアスのマイニング モデル列](../../analysis-services/data-mining/media/modelcolumnalias-income.gif "エイリアスでは、マイニング モデル列")  
  
 この図には、すべて収入に関連したマイニング構造列の複数のコピーを持つ関連モデルを示しています。 構造列のコピーは、それぞれ異なる方法で分離されています。 図のモデルでは、それぞれ異なる列をマイニング構造から使用していますが、モデル間で列を比較しやすくするため、各モデルの列名を **[収入]** に変更しました。  
  
### <a name="adding-filters"></a>フィルターの追加  
 マイニング モデルにはフィルターを追加できます。 フィルターは、モデル ケース内のデータをあるサブセットに制限する一連の WHERE 条件です。 フィルターは、モデルのトレーニング時に使用します。必要に応じて、モデルのテスト時や、精度チャートの作成時にも使用できます。  
  
 フィルターを追加することによって、マイニング構造を再利用して、広範なデータのサブセットに基づくモデルを作成できます。 また、フィルターを使用して、特定の行を除外し、分析の質を高めることもできます。  
  
 詳細については、「[マイニング モデルのフィルター選択 (Analysis Services - データ マイニング)](../../analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)」を参照してください。  
  
## <a name="changing-the-algorithm"></a>アルゴリズムの変更  
 マイニング構造に追加した新しいモデルが同じデータ セットを共有していても、(データでサポートされている) 別のアルゴリズムを使用することや、アルゴリズムのパラメーターを変更することで、異なる結果を得ることができます。 また、モデリング フラグを設定することもできます。  
  
 アルゴリズムの選択によって、どのような結果が得られるかが決まります。 特定のアルゴリズムがどのように動作し、どのようなビジネス シナリオで役立つかについては、「 [データ マイニング アルゴリズム (Analysis Services - データ マイニング)](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)というフラグを列に設定するだけです。  
  
 各アルゴリズムの要件、制限、およびサポートされているカスタマイズの詳細については、各アルゴリズムのテクニカル リファレンス トピックを参照してください。  
  
|||  
|-|-|  
|[Microsoft デシジョン ツリー アルゴリズム](../../analysis-services/data-mining/microsoft-decision-trees-algorithm.md)|[Microsoft タイム シリーズ アルゴリズム](../../analysis-services/data-mining/microsoft-time-series-algorithm.md)|  
|[Microsoft クラスタリング アルゴリズム](../../analysis-services/data-mining/microsoft-clustering-algorithm.md)|[Microsoft ニューラル ネットワーク アルゴリズム](../../analysis-services/data-mining/microsoft-neural-network-algorithm.md)|  
|[Microsoft Naive Bayes アルゴリズム](../../analysis-services/data-mining/microsoft-naive-bayes-algorithm.md)|[Microsoft ロジスティック回帰アルゴリズム](../../analysis-services/data-mining/microsoft-logistic-regression-algorithm.md)|  
|[Microsoft アソシエーション アルゴリズム](../../analysis-services/data-mining/microsoft-association-algorithm.md)|[Microsoft 線形回帰アルゴリズム](../../analysis-services/data-mining/microsoft-linear-regression-algorithm.md)|  
|[Microsoft シーケンス クラスタリング アルゴリズム](../../analysis-services/data-mining/microsoft-sequence-clustering-algorithm.md)||  
  
## <a name="customizing-algorithm-parameters"></a>アルゴリズム パラメーターのカスタマイズ  
 各アルゴリズムでは、アルゴリズムの動作をカスタマイズしたり、モデルの結果を細かく調整したりするために使用できるパラメーターがサポートされています。 各パラメーターの使用方法については、以下のトピックを参照してください。  
  
 これらのトピックには、それぞれのアルゴリズムに基づくモデルで使用できる予測関数の一覧も含まれています。  
  
|プロパティ名|対象|  
|-------------------|----------------|  
|AUTO_DETECT_PERIODICITY|[Microsoft タイム シリーズ アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)|  
|CLUSTER_COUNT|[Microsoft クラスタリング アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-clustering-algorithm-technical-reference.md)<br /><br /> [Microsoft シーケンス クラスタリング アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-sequence-clustering-algorithm-technical-reference.md)|  
|CLUSTER_SEED|[Microsoft クラスタリング アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-clustering-algorithm-technical-reference.md)|  
|CLUSTERING_METHOD|[Microsoft クラスタリング アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-clustering-algorithm-technical-reference.md)|  
|COMPLEXITY_PENALTY|[Microsoft デシジョン ツリー アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-decision-trees-algorithm-technical-reference.md)<br /><br /> [Microsoft タイム シリーズ アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)|  
|FORCE_REGRESSOR|[Microsoft デシジョン ツリー アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-decision-trees-algorithm-technical-reference.md)<br /><br /> [Microsoft 線形回帰アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-linear-regression-algorithm-technical-reference.md)<br /><br /> [モデリング フラグ (データ マイニング)](../../analysis-services/data-mining/modeling-flags-data-mining.md)|  
|FORECAST_METHOD|[Microsoft タイム シリーズ アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)|  
|HIDDEN_NODE_RATIO|[Microsoft ニューラル ネットワーク アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-neural-network-algorithm-technical-reference.md)|  
|HISTORIC_MODEL_COUNT|[Microsoft タイム シリーズ アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)|  
|HISTORICAL_MODEL_GAP|[Microsoft タイム シリーズ アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)|  
|HOLDOUT_PERCENTAGE|[Microsoft ロジスティック回帰アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-logistic-regression-algorithm-technical-reference.md)<br /><br /> [Microsoft ニューラル ネットワーク アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-neural-network-algorithm-technical-reference.md)<br /><br /> 注:このパラメーターは、マイニング構造に適用される提示データ割合値と異なります。|  
|HOLDOUT_SEED|[Microsoft ロジスティック回帰アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-logistic-regression-algorithm-technical-reference.md)<br /><br /> [Microsoft ニューラル ネットワーク アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-neural-network-algorithm-technical-reference.md)<br /><br /> 注:このパラメーターは、マイニング構造に適用される提示データのシード値と異なります。|  
|INSTABILITY_SENSITIVITY|[Microsoft タイム シリーズ アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)|  
|MAXIMUM_INPUT_ATTRIBUTES|[Microsoft クラスタリング アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-clustering-algorithm-technical-reference.md)<br /><br /> [Microsoft デシジョン ツリー アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-decision-trees-algorithm-technical-reference.md)<br /><br /> [Microsoft 線形回帰アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-linear-regression-algorithm-technical-reference.md)<br /><br /> [Microsoft Naive Bayes アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-naive-bayes-algorithm-technical-reference.md)<br /><br /> [Microsoft ニューラル ネットワーク アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-neural-network-algorithm-technical-reference.md)<br /><br /> [Microsoft ロジスティック回帰アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-logistic-regression-algorithm-technical-reference.md)|  
|MAXIMUM_ITEMSET_COUNT|[Microsoft アソシエーション アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-association-algorithm-technical-reference.md)|  
|MAXIMUM_ITEMSET_SIZE|[Microsoft アソシエーション アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-association-algorithm-technical-reference.md)|  
|MAXIMUM_OUTPUT_ATTRIBUTES|[Microsoft デシジョン ツリー アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-decision-trees-algorithm-technical-reference.md)<br /><br /> [Microsoft 線形回帰アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-linear-regression-algorithm-technical-reference.md)<br /><br /> [Microsoft ロジスティック回帰アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-logistic-regression-algorithm-technical-reference.md)<br /><br /> [Microsoft Naive Bayes アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-naive-bayes-algorithm-technical-reference.md)<br /><br /> [Microsoft Neural Network Algorithm Technical Reference](../../analysis-services/data-mining/microsoft-neural-network-algorithm-technical-reference.md)|  
|MAXIMUM_SEQUENCE_STATES|[Microsoft シーケンス クラスタリング アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-sequence-clustering-algorithm-technical-reference.md)|  
|MAXIMUM_SERIES_VALUE|[Microsoft タイム シリーズ アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)|  
|MAXIMUM_STATES|[Microsoft クラスタリング アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-clustering-algorithm-technical-reference.md)<br /><br /> [Microsoft ニューラル ネットワーク アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-neural-network-algorithm-technical-reference.md)<br /><br /> [Microsoft シーケンス クラスタリング アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-sequence-clustering-algorithm-technical-reference.md)|  
|MAXIMUM_SUPPORT|[Microsoft アソシエーション アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-association-algorithm-technical-reference.md)|  
|MINIMUM_IMPORTANCE|[Microsoft アソシエーション アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-association-algorithm-technical-reference.md)|  
|MINIMUM_ITEMSET_SIZE|[Microsoft アソシエーション アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-association-algorithm-technical-reference.md)|  
|MINIMUM_DEPENDENCY_PROBABILITY|[Microsoft Naive Bayes アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-naive-bayes-algorithm-technical-reference.md)|  
|MINIMUM_PROBABILITY|[Microsoft アソシエーション アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-association-algorithm-technical-reference.md)|  
|MINIMUM_SERIES_VALUE|[Microsoft タイム シリーズ アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)|  
|MINIMUM_SUPPORT|[Microsoft アソシエーション アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-association-algorithm-technical-reference.md)<br /><br /> [Microsoft クラスタリング アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-clustering-algorithm-technical-reference.md)<br /><br /> [Microsoft デシジョン ツリー アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-decision-trees-algorithm-technical-reference.md)<br /><br /> [Microsoft シーケンス クラスタリング アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-sequence-clustering-algorithm-technical-reference.md)<br /><br /> [Microsoft タイム シリーズ アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)|  
|MISSING_VALUE_SUBSTITUTION|[Microsoft タイム シリーズ アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)|  
|MODELLING_CARDINALITY|[Microsoft クラスタリング アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-clustering-algorithm-technical-reference.md)|  
|PERIODICITY_HINT|[Microsoft タイム シリーズ アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)|  
|PREDICTION_SMOOTHING|[Microsoft タイム シリーズ アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)|  
|SAMPLE_SIZE|[Microsoft クラスタリング アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-clustering-algorithm-technical-reference.md)<br /><br /> [Microsoft ロジスティック回帰アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-logistic-regression-algorithm-technical-reference.md)<br /><br /> [Microsoft ニューラル ネットワーク アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-neural-network-algorithm-technical-reference.md)|  
|SCORE_METHOD|[Microsoft デシジョン ツリー アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-decision-trees-algorithm-technical-reference.md)|  
|SPLIT_METHOD|[Microsoft デシジョン ツリー アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-decision-trees-algorithm-technical-reference.md)|  
|STOPPING_TOLERANCE|[Microsoft クラスタリング アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-clustering-algorithm-technical-reference.md)|  
  
## <a name="see-also"></a>関連項目  
 [データ マイニング アルゴリズム &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [物理アーキテクチャ (Analysis Services - データ マイニング)](../../analysis-services/data-mining/physical-architecture-analysis-services-data-mining.md)  
  
  
