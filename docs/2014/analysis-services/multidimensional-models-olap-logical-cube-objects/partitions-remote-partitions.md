---
title: リモート パーティション |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- storage [Analysis Services], partitions
- archiving remote partitions [Analysis Services]
- partitions [Analysis Services], remote
- restoring remote partitions [Analysis Services]
- backing up remote partitions [Analysis Services]
- partitions [Analysis Services], storage
- storing data [Analysis Services], partitions
- MasterDataSourceID property
- remote partitions [Analysis Services]
ms.assetid: 63f5d9f5-c6b6-4ceb-94fe-7b6c396d10bb
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 09231b03e784c142ab8b99ed31c2c4c88f6e72d7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48051922"
---
# <a name="remote-partitions"></a>リモート パーティション
  Microsoft の別のインスタンスにリモート パーティションのデータが格納されている[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]パーティションとその親キューブの定義 (メタデータ) が含まれているインスタンスよりもします。 リモート パーティションは、パーティションとその親キューブが定義されているインスタンスと同じ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスで管理されます。  
  
> [!NOTE]  
>  リモート パーティションを保存するには、コンピューターがのインスタンスをいる必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]インストールし、パーティションが定義されているインスタンスと同じサービス パック レベルを実行します。 以前のバージョンの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンス上でのリモート パーティションはサポートされていません。  
  
 リモート パーティションがメジャー グループに含まれている場合、キューブのメモリおよび CPU 使用率は、メジャー グループ内のすべてのパーティション間で分散されます。 たとえば、リモート パーティションが単独で、または親キューブの処理の一部として処理される場合、そのパーティションのメモリおよび CPU 使用率の大部分は [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のリモート インスタンスで発生します。  
  
> [!NOTE]  
>  リモート パーティションを含んでいるキューブには、書き込み許可ディメンションを含めることができます。ただし、これはキューブのパフォーマンスに影響を及ぼす可能性があります。 書き込み許可ディメンションの詳細については、[Write-Enabled ディメンション](../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)を参照してください。  
  
## <a name="storage-modes-for-remote-partitions"></a>リモート パーティションのストレージ モード  
 リモート パーティションでは、ローカル パーティションで使用する多次元 OLAP (MOLAP)、ハイブリッド OLAP (HOLAP)、リレーショナル OLAP (ROLAP) のストレージ型のいずれかを使用できます。 リモート パーティションでは、プロアクティブ キャッシュも使用できます。 リモート パーティションのストレージ モードに応じて、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のリモート インスタンスに次のデータが格納されます。  
  
|||  
|-|-|  
|ストレージ型|data|  
|[MOLAP]|パーティションの集計と、パーティションのソース データのコピー|  
|HOLAP|パーティションの集計|  
|[ROLAP]|パーティション データなし|  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の複数のインスタンスに格納された複数の MOLAP パーティションまたは HOLAP パーティションがメジャー グループに含まれる場合、キューブでは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のそれらのインスタンス間でメジャー グループのデータを分散します。  
  
## <a name="merging-remote-partitions"></a>リモート パーティションのマージ  
 リモート パーティションは、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の同一のリモート インスタンスに格納されている他のリモート パーティションとのみマージできます。 パーティションのマージの詳細については、[Analysis Services でのパーティションのマージ&#40;SSAS - 多次元&#41;](../multidimensional-models/merge-partitions-in-analysis-services-ssas-multidimensional.md)を参照してください。  
  
## <a name="archiving-and-restoring-remote-partitions"></a>リモート パーティションのアーカイブと復元  
 リモート パーティションのデータのアーカイブまたは復元は、リモート パーティションを格納するデータベースをアーカイブまたは復元するときに行えます。 リモート パーティションを復元せずにデータベースを復元する場合、リモート パーティションを処理しないとパーティションのデータを使用できません。 アーカイブとデータベースの復元の詳細については、[Analysis Services データベースの復元とバックアップ](../multidimensional-models/backup-and-restore-of-analysis-services-databases.md)を参照してください。  
  
## <a name="see-also"></a>参照  
 [作成し、管理、リモート パーティション&#40;Analysis Services&#41;](../multidimensional-models/create-and-manage-a-remote-partition-analysis-services.md)   
 [処理の Analysis Services オブジェクト](../multidimensional-models/processing-analysis-services-objects.md)  
  
  
