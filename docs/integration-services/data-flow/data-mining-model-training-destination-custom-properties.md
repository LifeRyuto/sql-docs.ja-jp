---
title: データ マイニング モデル トレーニング変換先のカスタム プロパティ | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: f0a70216-fdac-44ae-af29-35f65626217c
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 1dfad3ec6e575529026aa7aa93468be97cd7955e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "65727020"
---
# <a name="data-mining-model-training-destination-custom-properties"></a>データ マイニング モデル トレーニング変換先のカスタム プロパティ

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  データ マイニング モデル トレーニング変換先には、カスタム プロパティと、すべてのデータ フロー コンポーネントとの共通プロパティの両方があります。  
  
 次の表は、データ マイニング モデル トレーニング変換先のカスタム プロパティを示しています。 すべてのプロパティは読み取り/書き込み可能です。  
  
|プロパティ|データ型|[説明]|  
|--------------|---------------|-----------------|  
|ASConnectionId|String|接続マネージャーの一意識別子。|  
|ASConnectionString|String|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスまたは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトへの接続文字列。|  
|ObjectRef|String|この変換が使用するデータ マイニング構造を指定する XML タグ。|  
  
 データ マイニング モデル トレーニング変換先の入力および入力列には、カスタム プロパティはありません。  
  
 詳細については、「 [データ マイニング モデル トレーニング変換先](../../integration-services/data-flow/data-mining-model-training-destination.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Common Properties](https://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
  
