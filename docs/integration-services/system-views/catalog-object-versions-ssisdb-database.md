---
title: catalog.object_versions (SSISDB データベース) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 2fd8c020-1c77-4702-8e6b-efa6a348daab
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 44f3d605e9110271fc104842a58df992ede0eeb0
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/20/2019
ms.locfileid: "58276021"
---
# <a name="catalogobjectversions-ssisdb-database"></a>catalog.object_versions (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] カタログのオブジェクトのバージョンを示します。 このリリースでは、プロジェクトのバージョンのみがこのビューでサポートされます。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|object_version_lsn|**bigint**|オブジェクト バージョンの一意識別子 (ID)。 この番号は、シーケンシャルを保証するものではありません。|  
|object_id|**bigint**|オブジェクトの一意の ID。|  
|object_type|**smallint**|オブジェクトの種類。 プロジェクトには、値 `20` が表示されます。|  
|object_name|**sysname(nvarchar(128))**|オブジェクトの名前。|  
|description|**nvarchar(1024)**|プロジェクトの説明。|  
|created_by|**nvarchar(128)**|オブジェクトをカタログに追加したユーザーの名前。|  
|created_time|**datetimeoffset**|オブジェクトがカタログに追加された日時。|  
|restored_by|**nvarchar(128)**|オブジェクトを復元したユーザーの名前。|  
|last_restored_time|**datetimeoffset**|オブジェクトが前回復元された日時。|  
  
## <a name="remarks"></a>Remarks  
 このビューは、カタログの各オブジェクトの行を表示します。  
  
## <a name="permissions"></a>アクセス許可  
 このビュー内の行を表示するには、次のアクセス権限のいずれかが必要です。  
  
-   オブジェクトの READ 権限  
  
-   **ssis_admin** データベース ロールのメンバーシップ  
  
-   **sysadmin** サーバー ロールのメンバーシップ  
  
> [!NOTE]  
>  行レベルのセキュリティが適用されるため、表示する権限がある行のみが表示されます。  
  
  
