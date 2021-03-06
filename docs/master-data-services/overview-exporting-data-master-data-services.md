---
title: Exporting Data
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- exporting data [Master Data Services]
- subscription views [Master Data Services]
- subscription views [Master Data Services], about subscription views
ms.assetid: 8b74409a-ea70-45f8-84c7-da6905e4901a
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c0376e28c1d75585795b53373a10f4798347746a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "73728990"
---
# <a name="overview-exporting-data-master-data-services"></a>概要: データのエクスポート (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  この記事では、サブスクリプション ビュー形式の種類と、モデル オブジェクトが変更されたためにビューを編集する必要がある場合を判断する方法について説明します。  
  
 サブスクリプション ビューを作成して、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データを [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のようなサブスクライブ システムにエクスポートします。 サブスクライブ システムを使用して、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースのデータを表示します。  サブスクライブ ビューを作成する方法については、「 [サブスクリプション ビューを作成してデータをエクスポートする (マスター データ サービス)](../master-data-services/create-a-subscription-view-to-export-data-master-data-services.md)  
  
 表示の詳細については、「[表示](../relational-databases/views/views.md)」を参照してください。  
  
## <a name="subscription-view-formats"></a>サブスクリプション ビュー形式  
 
  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]でビューを作成する場合は、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] によって提供される一連の標準ビュー形式から選択します。 これらの形式を使用して、以下を表示するビューを作成できます。  
  
-   すべてのリーフ メンバーとその属性  
  
-   すべての統合メンバーとその属性  
  
-   すべてのコレクションとその属性  
  
-   コレクションに明示的に追加されたメンバー  
  
-   親子形式またはレベル形式の派生階層内のメンバー  
  
-   エンティティのすべての明示的階層内のメンバー (親子形式またはレベル形式)  
  
## <a name="subscription-views-can-become-out-of-date"></a>サブスクリプション ビューが古くなる可能性  
 エンティティまたは階層のサブスクリプション ビューを作成後、関連付けられたモデル オブジェクトへの変更が自動的にビューに反映されるわけではありません。 モデル オブジェクトに対する変更を反映するには、必要に応じて [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] でサブスクリプション ビューを再生成する必要があります。 モデル オブジェクトが変更されると、 **[エクスポート]** ページの **[変更]** 列が **[True]** に更新されます。 **True**は、サブスクリプションビューを編集して保存する必要があることを示します。これにより、ビューが再生成されます。  
  
## <a name="related-tasks"></a>Related Tasks  
  
|タスクの説明|トピック|  
|----------------------|-----------|  
|マスター データのサブスクリプション ビューを作成する。|[マスターデータサービス &#40;データをエクスポートするサブスクリプションビューを作成&#41;](../master-data-services/create-a-subscription-view-to-export-data-master-data-services.md)|  
|既存のサブスクリプション ビューを削除する。|[サブスクリプションビュー &#40;マスターデータサービスの削除&#41;](../master-data-services/delete-a-subscription-view-master-data-services.md)|  
  
## <a name="related-content"></a>関連コンテンツ  
  
-   [サブスクリプションビュー形式 &#40;マスターデータサービス&#41;](../master-data-services/subscription-view-formats-master-data-services.md)  
  
-   [表示モード](../relational-databases/views/views.md)  
  
  
