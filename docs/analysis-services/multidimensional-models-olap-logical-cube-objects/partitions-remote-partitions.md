---
title: リモート パーティション |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3f7729fc1ddeb95c4ab9c780dfc6c48c253666f0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68209300"
---
# <a name="partitions---remote-partitions"></a>パーティション - リモート パーティション
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Microsoft の別のインスタンスにリモート パーティションのデータが格納されている[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]パーティションとその親キューブの定義 (メタデータ) が含まれているインスタンスよりもします。 リモート パーティションは、パーティションとその親キューブが定義されているインスタンスと同じ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスで管理されます。  
  
> [!NOTE]
>  リモート パーティションを保存するには、コンピューターがのインスタンスをいる必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]インストールし、パーティションが定義されているインスタンスと同じサービス パック レベルを実行します。 以前のバージョンの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンス上でのリモート パーティションはサポートされていません。  
  
 リモート パーティションがメジャー グループに含まれている場合、キューブのメモリおよび CPU 使用率は、メジャー グループ内のすべてのパーティション間で分散されます。 たとえば、リモート パーティションが単独で、または親キューブの処理の一部として処理される場合、そのパーティションのメモリおよび CPU 使用率の大部分は [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のリモート インスタンスで発生します。  
  
> [!NOTE]  
>  リモート パーティションを含んでいるキューブには、書き込み許可ディメンションを含めることができます。ただし、これはキューブのパフォーマンスに影響を及ぼす可能性があります。 書き込み許可ディメンションの詳細については、次を参照してください。 [Write-Enabled ディメンション](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)します。  
  
## <a name="storage-modes-for-remote-partitions"></a>リモート パーティションのストレージ モード  
 リモート パーティションでは、ローカル パーティションで使用する多次元 OLAP (MOLAP)、ハイブリッド OLAP (HOLAP)、リレーショナル OLAP (ROLAP) のストレージ型のいずれかを使用できます。 リモート パーティションでは、プロアクティブ キャッシュも使用できます。 リモート パーティションのストレージ モードに応じて、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のリモート インスタンスに次のデータが格納されます。  
  
|||  
|-|-|  
|ストレージ型|データ|  
|[MOLAP]|パーティションの集計と、パーティションのソース データのコピー|  
|HOLAP|パーティションの集計|  
|[ROLAP]|パーティション データなし|  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の複数のインスタンスに格納された複数の MOLAP パーティションまたは HOLAP パーティションがメジャー グループに含まれる場合、キューブでは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のそれらのインスタンス間でメジャー グループのデータを分散します。  
  
## <a name="merging-remote-partitions"></a>リモート パーティションのマージ  
 リモート パーティションは、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の同一のリモート インスタンスに格納されている他のリモート パーティションとのみマージできます。 パーティションのマージの詳細については、次を参照してください。 [Analysis Services でのパーティションのマージ&#40;SSAS - 多次元&#41;](../../analysis-services/multidimensional-models/merge-partitions-in-analysis-services-ssas-multidimensional.md)します。  
  
## <a name="archiving-and-restoring-remote-partitions"></a>リモート パーティションのアーカイブと復元  
 リモート パーティションのデータのアーカイブまたは復元は、リモート パーティションを格納するデータベースをアーカイブまたは復元するときに行えます。 リモート パーティションを復元せずにデータベースを復元する場合、リモート パーティションを処理しないとパーティションのデータを使用できません。 アーカイブとデータベースの復元の詳細については、次を参照してください。 [Analysis Services データベースの復元とバックアップ](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md)します。  
  
## <a name="see-also"></a>参照  
 [リモート パーティションの作成と管理 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/create-and-manage-a-remote-partition-analysis-services.md)   
 [処理の Analysis Services オブジェクト](../../analysis-services/multidimensional-models/processing-analysis-services-objects.md)  
  
  
