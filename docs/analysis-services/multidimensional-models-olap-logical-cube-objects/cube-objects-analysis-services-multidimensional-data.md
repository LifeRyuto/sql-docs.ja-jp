---
title: キューブ オブジェクト (Analysis Services - 多次元データ) |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: cada8410f608816272b159c66196fb761e510abe
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68181008"
---
# <a name="cube-objects-analysis-services---multidimensional-data"></a>Cube オブジェクト (Analysis Services - 多次元データ)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
    
## <a name="introducing-cube-objects"></a>Cube オブジェクトの導入  
 簡単な <xref:Microsoft.AnalysisServices.Cube> オブジェクトは、基本情報、ディメンション、およびメジャー グループで構成されます。 基本情報には、キューブの名前、キューブの既定のメジャー、データ ソース、ストレージ モードなどが含まれます。  
  
 Dimensions コレクションには、データベースのディメンション コレクションのキューブで使用される、実際のディメンションのセットが含まれています。 すべてのディメンションは、キューブ内で参照される前に、データベースのディメンション コレクション内で定義されている必要があります。 プライベート ディメンションでは使用できない[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]します。  
  
 メジャー グループは、キューブ内のメジャーのセットです。 メジャー グループは、共通のデータ ソース ビューと共通のディメンション セットを持つ、メジャーのコレクションです。 メジャー グループは、メジャーの処理単位です。メジャー グループは個別に処理されてから参照できます。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|||  
|-|-|  
|トピック||  
|[アクション &#40;Analysis Services - 多次元データ&#41;](../../analysis-services/multidimensional-models/actions-analysis-services-multidimensional-data.md)||  
|[集計と集計デザイン](../../analysis-services/multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md)||  
|[計算](../../analysis-services/multidimensional-models-olap-logical-cube-objects/calculations.md)||  
|[キューブ セル&#40;Analysis Services - 多次元データ&#41;](../../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-cells-analysis-services-multidimensional-data.md)||  
|[キューブ プロパティ - 多次元モデルのプログラミング](../../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-properties-multidimensional-model-programming.md)||  
|[キューブのストレージ&#40;Analysis Services - 多次元データ&#41;](../../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-storage-analysis-services-multidimensional-data.md)||  
|[キューブの翻訳](../../analysis-services/multidimensional-models-olap-logical-cube-objects/cube-translations.md)||  
|[ディメンション リレーションシップ](../../analysis-services/multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)||  
|[多次元モデルの主要業績評価指標 &#40;KPI&#41;](../../analysis-services/multidimensional-models/key-performance-indicators-kpis-in-multidimensional-models.md)||  
|[メジャーおよびメジャー グループ](../../analysis-services/multidimensional-models/measures-and-measure-groups.md)||  
|[パーティション (Analysis Services - 多次元データ)](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)||  
|[パースペクティブ](../../analysis-services/multidimensional-models-olap-logical-cube-objects/perspectives.md)||  
  
  
