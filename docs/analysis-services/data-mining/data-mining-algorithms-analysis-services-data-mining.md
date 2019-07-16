---
title: データ マイニング アルゴリズム (Analysis Services - データ マイニング) |Microsoft Docs
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 55b46feab1170d5db9689e9347a37f7353263791
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68183794"
---
# <a name="data-mining-algorithms-analysis-services---data-mining"></a>データ マイニング アルゴリズム (Analysis Services - データ マイニング)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  データ マイニング (機械学習) の *アルゴリズム* は、データからモデルを作成するヒューリスティクスと計算のセットです。 モデルを作成するために、データ マイニング アルゴリズムは、まず提供されたデータを分析し、特定の種類のパターンまたは傾向を探します。 この分析を繰り返し実行した結果を使用して、マイニング モデルを作成するための最適化されたパラメーターが定義されます。 これらのパラメーターはデータセット全体に適用され、実用的なパターンおよび詳細な統計情報が抽出されます。  
  
 アルゴリズムによってデータから作成されるマイニング モデルは、次のようにさまざまな形式を取ります。  
  
-   データセット内のケースの関係を説明するクラスターのセット  
  
-   結果を予測し、基準を変更するとその結果がどのように影響を受けるのかを示すデシジョン ツリー  
  
-   売上を予想する数学的モデル  
  
-   複数の製品を 1 つのトランザクションにグループ化する方法、およびそれらの製品がまとめて購入される確率を示すルールのセット  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ マイニングで提供されるアルゴリズムは、パターンをデータから派生する最も一般的かつ詳細な研究に基づいた方法です。 1 つの例を挙げると、K-Means クラスタリングは最も古いクラスタリング アルゴリズムの 1 つであり、さまざまな多数のツールで、さまざまな実装およびオプションと共に広く使用されています。 ただし、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ マイニングで使用される K-Means クラスタリングの特定の実装は、Microsoft Research によって開発され、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]でのパフォーマンスのために最適化されます。 Microsoft データ マイニング アルゴリズムはすべて、提供された API を使用して広範にカスタマイズしたり、十分にプログラムすることができます。 また、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]でデータ マイニング コンポーネントを使用してモデルの作成、トレーニング、再トレーニングを自動化することもできます。  
  
 さらに、OLE DB for Data Mining 仕様に準拠するサードパーティ製アルゴリズムを使用することも、またはサービスとして登録してから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ マイニング フレームワーク内で使用できるカスタム アルゴリズムを開発することもできます。  
  
## <a name="choosing-the-right-algorithm"></a>適切なアルゴリズムの選択  
 特定の分析タスクに使用する最適なアルゴリズムを選択するのが困難な場合があります。 異なるアルゴリズムを使用して同じビジネス タスクを実行できる一方、各アルゴリズムによって異なる結果が生成されたり、一部のアルゴリズムでは複数の種類の結果が生成されたりする場合があります。 たとえば、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] デシジョン ツリー アルゴリズムは、予測だけでなく、データセット内の列の数を減らす方法としても使用できます。これは、デシジョン ツリーが、最終的なマイニング モデルに影響を与えない列を識別できるためです。  
  
### <a name="choosing-an-algorithm-by-type"></a>種類別アルゴリズムの選択  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ マイニングには、次の種類のアルゴリズムが含まれます。  
  
-   **分類アルゴリズム** 。データセット内の他の属性に基づいて、1 つまたは複数の離散変数を予測します。  
  
-   **回帰アルゴリズム** 。データセット内の他の属性に基づいて、利益や損失などの 1 つまたは複数の連続数値変数を予測します。  
  
-   **分割アルゴリズム** 。データを、類似したプロパティを持つアイテムのグループまたはクラスターに分割します。  
  
-   **アソシエーション アルゴリズム** 。データセット内の異なる属性間の相関関係を検出します。 この種類のアルゴリズムの最も一般的な使用例は、マーケット バスケット分析で使用するアソシエーション ルールの作成です。  
  
-   **シーケンス分析アルゴリズム** 。Web サイトの一連のクリック、マシン保守に先行するログ イベントなど、データ内の頻度の高いシーケンスまたはエピソードを要約します。  
  
 ただし、ソリューションが複数ある中で、1 つのアルゴリズムに限定される必要はありません。 経験豊富なアナリストであれば、ある 1 つのアルゴリズムを使用して最も効果的な入力 (つまり変数) を判断し、次に別のアルゴリズムを適用してそのデータに基づいて特定の結果を予測するものです。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ マイニングでは、1 つのマイニング構造上に複数のモデルを構築できます。そのため、1 つのデータ マイニング ソリューション内でクラスタリング アルゴリズム、デシジョン ツリー モデル、および Naïve Bayes モデルを使用して、データに関するさまざまなビューを得ることができます。 また、1 つのソリューション内で複数のアルゴリズムを使用して、個別のタスクを実行することもできます。たとえば、回帰を使用して財務予測を取得したり、ニューラル ネットワーク アルゴリズムを使用して予測に影響を及ぼす因子を分析したりできます。  
  
### <a name="choosing-an-algorithm-by-task"></a>タスク別アルゴリズムの選択  
 特定のタスクで使用するアルゴリズムの選択の参考として、各アルゴリズムが長年使用されてきたタスクを次の表に示します。  
  
|タスクの例|使用する Microsoft アルゴリズム|  
|-----------------------|---------------------------------|  
|**不連続属性の予測:**<br /><br /> 見込み客リスト内の顧客について、見込みがあるかないかをフラグで示します。<br /><br /> あるサーバーに半年以内に障害が発生する確率を計算します。<br /><br /> 患者の転帰を分類し、関連因子を探ります。|[Microsoft デシジョン ツリー アルゴリズム](../../analysis-services/data-mining/microsoft-decision-trees-algorithm.md)<br /><br /> [Microsoft Naive Bayes アルゴリズム](../../analysis-services/data-mining/microsoft-naive-bayes-algorithm.md)<br /><br /> [Microsoft クラスタリング アルゴリズム](../../analysis-services/data-mining/microsoft-clustering-algorithm.md)<br /><br /> [Microsoft ニューラル ネットワーク アルゴリズム](../../analysis-services/data-mining/microsoft-neural-network-algorithm.md)|  
|**連続属性の予測:**<br /><br /> 翌年の売上を予測します。<br /><br /> 過去の歴史的、季節的傾向を考慮に入れて、来場者を予測します。<br /><br /> 人口統計を考慮に入れて、リスク スコアを生成します。|[Microsoft デシジョン ツリー アルゴリズム](../../analysis-services/data-mining/microsoft-decision-trees-algorithm.md)<br /><br /> [Microsoft タイム シリーズ アルゴリズム](../../analysis-services/data-mining/microsoft-time-series-algorithm.md)<br /><br /> [Microsoft 線形回帰アルゴリズム](../../analysis-services/data-mining/microsoft-linear-regression-algorithm.md)|  
|**シーケンスの予測:**<br /><br /> ある企業の Web サイトのクリックストリーム分析を実行します。<br /><br /> サーバーの障害につながる要因を分析します。<br /><br /> 外来患者の来院中の一連の行動を把握し分析して、共通する行動に関するベスト プラクティスを組み立てます。|[Microsoft シーケンス クラスタリング アルゴリズム](../../analysis-services/data-mining/microsoft-sequence-clustering-algorithm.md)|  
|**トランザクション内の共通アイテムのグループの検出:**<br /><br /> マーケット バスケット分析を使用して、製品の配置を決定します。<br /><br /> ある顧客に追加購入を勧める製品を提案します。<br /><br /> ある 1 件のイベントへの来場者の調査データを分析して、相関関係のある行動またはブースを特定し、今後の活動計画を立てます。|[Microsoft アソシエーション アルゴリズム](../../analysis-services/data-mining/microsoft-association-algorithm.md)<br /><br /> [Microsoft デシジョン ツリー アルゴリズム](../../analysis-services/data-mining/microsoft-decision-trees-algorithm.md)|  
|**類似アイテムのグループの検出:**<br /><br /> 人口統計や行動などの属性に基づいて、患者リスク プロファイル グループを作成します。<br /><br /> ユーザーを閲覧パターンと購買パターンで分析します。<br /><br /> 同じような使用状況特性を持つサーバーを特定します。|[Microsoft クラスタリング アルゴリズム](../../analysis-services/data-mining/microsoft-clustering-algorithm.md)<br /><br /> [Microsoft シーケンス クラスタリング アルゴリズム](../../analysis-services/data-mining/microsoft-sequence-clustering-algorithm.md)|  
  
## <a name="related-content"></a>関連コンテンツ  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ マイニングに用意されている各データ マイニング アルゴリズムの学習用リソースのリンクを次の表に示します。  
  
|||  
|-|-|  
|**基本的なアルゴリズムの説明**|アルゴリズムが行うことと機能のしくみについて説明し、そのアルゴリズムが役に立つ可能性のあるビジネス シナリオの概要を説明します。|  
||[Microsoft アソシエーション アルゴリズム](../../analysis-services/data-mining/microsoft-association-algorithm.md)<br /><br /> [Microsoft クラスタリング アルゴリズム](../../analysis-services/data-mining/microsoft-clustering-algorithm.md)<br /><br /> [Microsoft デシジョン ツリー アルゴリズム](../../analysis-services/data-mining/microsoft-decision-trees-algorithm.md)<br /><br /> [Microsoft 線形回帰アルゴリズム](../../analysis-services/data-mining/microsoft-linear-regression-algorithm.md)<br /><br /> [Microsoft ロジスティック回帰アルゴリズム](../../analysis-services/data-mining/microsoft-logistic-regression-algorithm.md)<br /><br /> [Microsoft Naive Bayes アルゴリズム](../../analysis-services/data-mining/microsoft-naive-bayes-algorithm.md)<br /><br /> [Microsoft ニューラル ネットワーク アルゴリズム](../../analysis-services/data-mining/microsoft-neural-network-algorithm.md)<br /><br /> [Microsoft シーケンス クラスタリング アルゴリズム](../../analysis-services/data-mining/microsoft-sequence-clustering-algorithm.md)<br /><br /> [Microsoft タイム シリーズ アルゴリズム](../../analysis-services/data-mining/microsoft-time-series-algorithm.md)|  
|**テクニカル リファレンス**|アルゴリズムの実装について、必要に応じて学術的参考文献を示しながら、技術的詳細を説明します。 アルゴリズムの動作を制御したり、モデルの結果をカスタマイズしたりするために設定できるパラメーターを列挙します。 データ要件について説明し、可能であればパフォーマンスのヒントを提供します。|  
||[Microsoft アソシエーション アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-association-algorithm-technical-reference.md)<br /><br /> [Microsoft クラスタリング アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-clustering-algorithm-technical-reference.md)<br /><br /> [Microsoft デシジョン ツリー アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-decision-trees-algorithm-technical-reference.md)<br /><br /> [Microsoft 線形回帰アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-linear-regression-algorithm-technical-reference.md)<br /><br /> [Microsoft ロジスティック回帰アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-logistic-regression-algorithm-technical-reference.md)<br /><br /> [Microsoft Naive Bayes アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-naive-bayes-algorithm-technical-reference.md)<br /><br /> [Microsoft ニューラル ネットワーク アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-neural-network-algorithm-technical-reference.md)<br /><br /> [Microsoft シーケンス クラスタリング アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-sequence-clustering-algorithm-technical-reference.md)<br /><br /> [Microsoft タイム シリーズ アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)|  
|**モデル コンテンツ**|各種類のデータ マイニング モデル内で情報がどのように構造化されるのか、および各ノードに格納された情報を解釈する方法について説明します。|  
||[アソシエーション モデルのマイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/mining-model-content-for-association-models-analysis-services-data-mining.md)<br /><br /> [クラスター モデルのマイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/mining-model-content-for-clustering-models-analysis-services-data-mining.md)<br /><br /> [デシジョン ツリー モデルのマイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/mining-model-content-for-decision-tree-models-analysis-services-data-mining.md)<br /><br /> [線形回帰モデルのマイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/mining-model-content-for-linear-regression-models-analysis-services-data-mining.md)<br /><br /> [ロジスティック回帰モデルのマイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/mining-model-content-for-logistic-regression-models.md)<br /><br /> [Naive Bayes モデルのマイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/mining-model-content-for-naive-bayes-models-analysis-services-data-mining.md)<br /><br /> [ニューラル ネットワーク モデルのマイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/mining-model-content-for-neural-network-models-analysis-services-data-mining.md)<br /><br /> [シーケンス クラスター モデルのマイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/mining-model-content-for-sequence-clustering-models.md)<br /><br /> [タイム シリーズ モデルのマイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/mining-model-content-for-time-series-models-analysis-services-data-mining.md)|  
|**データ マイニング クエリ**|各モデルの種類で使用できる複数のクエリを紹介します。 たとえば、モデル内のパターンをさらに理解できるようにするコンテンツ クエリや、それらのパターンに基づいて予測できるよう支援する予測クエリなどがあります。|  
||[結合モデルのクエリ例](../../analysis-services/data-mining/association-model-query-examples.md)<br /><br /> [クラスタリング モデルのクエリ例](../../analysis-services/data-mining/clustering-model-query-examples.md)<br /><br /> [デシジョン ツリー モデルのクエリ例](../../analysis-services/data-mining/decision-trees-model-query-examples.md)<br /><br /> [線形回帰モデルのクエリ例](../../analysis-services/data-mining/linear-regression-model-query-examples.md)<br /><br /> [ロジスティック回帰モデルのクエリ例](../../analysis-services/data-mining/logistic-regression-model-query-examples.md)<br /><br /> [Naive Bayes Model Query Examples](../../analysis-services/data-mining/naive-bayes-model-query-examples.md)<br /><br /> [ニューラル ネットワーク モデルのクエリ例](../../analysis-services/data-mining/neural-network-model-query-examples.md)<br /><br /> [シーケンス クラスター モデルのクエリの例](../../analysis-services/data-mining/sequence-clustering-model-query-examples.md)<br /><br /> [Time Series Model Query Examples](../../analysis-services/data-mining/time-series-model-query-examples.md)|  
  
## <a name="related-tasks"></a>Related Tasks  
  
|**トピック**|**[説明]**|  
|---------------|---------------------|  
|あるデータ マイニング モデルで使用されるアルゴリズムを判断します。|[マイニング モデルの作成に使用されたパラメーターのクエリ](../../analysis-services/data-mining/query-the-parameters-used-to-create-a-mining-model.md)|  
|カスタム プラグイン アルゴリズムを作成します。|[プラグイン アルゴリズム](../../analysis-services/data-mining/plugin-algorithms.md)|  
|アルゴリズム固有のビューアーを使用して、モデルを調査します。|[データ マイニング モデル ビューアー](../../analysis-services/data-mining/data-mining-model-viewers.md)|  
|汎用のテーブル フォーマットを使用して、モデルのコンテンツを表示します。|[Microsoft 汎用コンテンツ ツリー ビューアーを使用したモデルの参照](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)|  
|データをセットアップし、アルゴリズムを使用してモデルを作成する方法について学びます。|[マイニング構造 &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)<br /><br /> [マイニング モデル (Analysis Services - データ マイニング)](../../analysis-services/data-mining/mining-models-analysis-services-data-mining.md)|  
  
## <a name="see-also"></a>関連項目  
 [データ マイニング ツール](../../analysis-services/data-mining/data-mining-tools.md)  
  
  
