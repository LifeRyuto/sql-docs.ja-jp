---
title: データ マイニング オブジェクトの処理 |Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 017f1d751e81fa80b8a7e4c2655fd1de59459fed
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68209723"
---
# <a name="processing-data-mining-objects"></a>データ マイニング オブジェクトの処理
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  データ マイニング オブジェクトは、処理されるまでは単なる空のコンテナーです。 データ マイニング モデルの*処理* は *トレーニング*とも呼ばれます。  
  
 **マイニング構造の処理。** マイニング構造では、列バインドと使用方法のメタデータで定義されている外部データ ソースからデータを取得し、データを読み取ります。 このデータの全体が読み取られて分析され、さまざまな統計情報が抽出されます。 Analysis Services では、データ マイニング アルゴリズムによる分析に適した、簡潔な表現のデータがローカル キャッシュに格納されます。 モデルを処理した後、このキャッシュを保持することも削除することもできます。 既定では、キャッシュが保存されます。 詳細については、「 [Process a Mining Structure](../../analysis-services/data-mining/process-a-mining-structure.md)」 (マイニング構造の処理) を参照してください。  
  
 **マイニング モデルの処理。** マイニング モデルでは、空の場合、それが処理されるまでにのみの定義を含むです。 マイニング モデルを処理するには、基になるマイニング構造の処理が完了している必要があります。 マイニング モデルは、マイニング構造のキャッシュからデータを取得し、モデルに対して作成されたフィルターがあれば適用した後、データセットをアルゴリズムに渡してパターンを検出します。 処理後のモデルには、データ自体ではなく処理結果だけが保存されます。 詳細については、「 [Process a Mining Model](../../analysis-services/data-mining/process-a-mining-model.md)」 (マイニング モデルの処理) を参照してください。  
  
 次の図は、マイニング構造とマイニング モデルの処理時のデータ フローを示しています。  
  
 ![データの処理: ソース、構造モデル、](../../analysis-services/data-mining/media/dmcon-modelarch.gif "データの処理: ソース、モデルの構造")  
  
## <a name="viewing-the-results-of-processing"></a>処理結果の表示  
 処理後のマイニング構造には、統計分析に使用できる、簡潔な表現のデータが含まれています。 キャッシュが消去されていない場合、このキャッシュ内のデータには次の方法でアクセスできます。  
  
-   モデルに対するデータ マイニング拡張機能 (DMX) クエリを作成し、構造にドリルスルーします。 詳細については、「[SELECT FROM &#60;model&#62;.CASES (DMX)](../../dmx/select-from-model-cases-dmx.md)」を参照してください。  
  
-   構造に基づいてモデルを参照し、ユーザー インターフェイスでいずれかのオプションを使用して構造ケースにドリルスルーします。 詳細については、「 [Data Mining Model Viewers](../../analysis-services/data-mining/data-mining-model-viewers.md)」 (データ マイニング モデル ビューアー) または「 [マイニング モデルからケース データへのドリルスルー](../../analysis-services/data-mining/drill-through-to-case-data-from-a-mining-model.md)」を参照してください。  
  
-   構造ケースに対する DMX クエリを作成します。 詳細については、「[SELECT FROM &#60;structure&#62;.CASES](../../dmx/select-from-structure-cases.md)」を参照してください。  
  
 処理後のマイニング モデルには、分析によって生成されたパターンと、モデルの結果からキャッシュ内のトレーニング データへのマッピングだけが含まれています。 モデルの結果 ( *モデル コンテンツ*) に対して参照やクエリを実行できます。また、キャッシュされている場合は、モデル ケースや構造ケースに対してクエリを実行することもできます。  
  
 各マイニング モデルのモデル コンテンツは、作成に使用されたアルゴリズムによって異なります。 たとえば、クラスター モデルとデシジョン ツリー モデルでは、まったく同じデータを使用した場合でも、モデル コンテンツが大きく異なります。 詳細については、「[マイニング モデル コンテンツ (Analysis Services - データ マイニング)](../../analysis-services/data-mining/mining-model-content-analysis-services-data-mining.md)」を参照してください。  
  
## <a name="processing-requirements"></a>処理の要件  
 処理の要件は、マイニング モデルがリレーショナル データのみに基づいているか多次元データ ソースに基づいているかに応じて異なる場合があります。  
  
 リレーショナル データソースの処理には、トレーニング データを作成し、そのデータでマイニング アルゴリズムを実行することだけが必要です。 ただし、マイニング モデルがディメンション、メジャーなどの OLAP オブジェクトに基づいている場合は、基になるデータが処理済みの状態であることが必要です。 これには、多次元オブジェクトを処理して、マイニング モデルを作成する必要があります。  
  
 詳細については、「[処理の要件および注意事項 &#40;データ マイニング&#41;](../../analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [ドリルスルー クエリ &#40;データ マイニング&#41;](../../analysis-services/data-mining/drillthrough-queries-data-mining.md)   
 [マイニング構造 &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)   
 [マイニング モデル &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/mining-models-analysis-services-data-mining.md)   
 [論理アーキテクチャ &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/logical-architecture-analysis-services-data-mining.md)  
  
  
