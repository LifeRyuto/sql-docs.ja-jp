---
title: sys.dm_operation_status (Azure SQL データベース) |Microsoft Docs
ms.custom: ''
ms.date: 06/05/2017
ms.service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- dm_operation_status_TSQL
- dm_operation_status
- sys.dm_operation_status
- sys.dm_operation_status_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dm_operation_status dynamic management view
- sys.dm_operation_status dynamic management view
ms.assetid: cc847784-7f61-4c69-8b78-5f971bb24d61
author: stevestein
ms.author: sstein
monikerRange: = azuresqldb-current || = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: d9ce81a0d7aad6b41945b1564076004db80cd5e7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67900276"
---
# <a name="sysdmoperationstatus-azure-sql-database"></a>sys.dm_operation_status (Azure SQL データベース)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

  [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] サーバーのデータベースに対して実行される操作に関する情報を返します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|session_activity_id|**uniqueidentifier**|操作の ID。 NULL 以外です。|  
|resource_type|**int**|操作が実行される対象のリソースの種類を示します。 NULL 以外です。 現在のリリースでは、このビューが追跡するのは [!INCLUDE[ssSDS](../../includes/sssds-md.md)] に対して実行される操作のみであり、これに対応する整数値は 0 です。|  
|resource_type_desc|**nvarchar(2048)**|操作が実行される対象のリソースの種類の説明。 現在のリリースでは、このビューが追跡するのは [!INCLUDE[ssSDS](../../includes/sssds-md.md)] に対して実行される操作のみです。|  
|major_resource_id|**sql_variant**|操作が実行される対象の [!INCLUDE[ssSDS](../../includes/sssds-md.md)] の名前。 Null 以外です。|  
|minor_resource_id|**sql_variant**|内部使用のみです。 NULL 以外です。|  
|operation|**nvarchar(60)**|[!INCLUDE[ssSDS](../../includes/sssds-md.md)] に対して実行される操作。たとえば、CREATE や ALTER などです。|  
|state|**tinyint**|操作の状態。<br /><br /> 0 = 保留<br />1 = 実行中<br />2 = 完了<br />3 = 失敗<br />4 = 取り消し|  
|state_desc|**nvarchar(120)**|PENDING = 操作はリソースまたはクォータが利用可能になるのを待機しています。<br /><br /> IN_PROGRESS = 操作は開始され、実行中です。<br /><br /> COMPLETED = 操作が正常に完了しました。<br /><br /> FAILED = 操作が失敗しました。 参照してください、 **error_desc**詳細列。<br /><br /> CANCELLED = ユーザーの要求によって操作が停止しました。|  
|percent_complete|**int**|操作が完了した割合 (%)。 値は連続していないと、有効な値を以下に示します。 NULL 以外です。<br/><br/>0 = 操作が開始されていません<br/>50 = 実行中の操作<br/>100 = 操作が完了しました|  
|error_code|**int**|失敗した操作中に発生したエラーを示すコード。 値が 0 の場合は、操作が正常に完了したことを示します。|  
|error_desc|**nvarchar(2048)**|失敗した操作中に発生したエラーの説明。|  
|error_severity|**int**|失敗した操作中に発生したエラーの重大度レベル。 エラーの重大度に関する詳細については、次を参照してください。[データベース エンジン エラーの重大度](https://go.microsoft.com/fwlink/?LinkId=251052)します。|  
|error_state|**int**|将来使用するために予約されています。 将来の互換性は保証されません。|  
|start_time|**datetime**|操作が開始した時点のタイムスタンプ。|  
|last_modify_time|**datetime**|実行時間の長い操作のレコードが最後に変更された時点のタイムスタンプ。 操作が正常に完了した場合、このフィールドには操作が完了した時点のタイムスタンプが表示されます。|  
  
## <a name="permissions"></a>アクセス許可  
 このビューはのみ利用可能、**マスター**データベース、サーバー レベル プリンシパル ログインをします。  
  
## <a name="remarks"></a>コメント  
 このビューを使用するに接続する必要があります、**マスター**データベース。 使用して、`sys.dm_operation_status`で表示、**マスター**のデータベース、[!INCLUDE[ssSDS](../../includes/sssds-md.md)]サーバーに対して実行される次の操作の状態を追跡するために、 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]:  
  
-   データベースを作成します。  
  
-   データベースをコピーします。 データベースのコピーによって、ソース サーバーおよび対象サーバーの両方にあるこのビューに、レコードが作成されます。  
  
-   データベースの変更  
  
-   サービス層のパフォーマンス レベルの変更  
  
-   データベースのサービス層を変更します (Basic から Standard への変更など)。  
  
-   地理的レプリケーション リレーションシップの設定  
  
-   地理的レプリケーション リレーションシップの終了  
  
-   ダイアログ ボックスの  
  
-   データベースの削除  
  
## <a name="example"></a>例  
 データベース 'mydb' に関連付けられている最新の geo レプリケーション操作を表示します。  
  
```  
SELECT * FROM sys.dm_ operation_status   
   WHERE major_resource_id = 'myddb'   
   ORDER BY start_time DESC;  
```  
  
## <a name="see-also"></a>参照  
 [地理的レプリケーション動的管理ビューおよび関数&#40;Azure SQL Database&#41;](../../relational-databases/system-dynamic-management-views/geo-replication-dynamic-management-views-and-functions-azure-sql-database.md)   
 [sys.dm_geo_replication_link_status &#40;Azure SQL Database&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-geo-replication-link-status-azure-sql-database.md)   
 [sys.geo_replication_links &#40;Azure SQL Database&#41;](../../relational-databases/system-dynamic-management-views/sys-geo-replication-links-azure-sql-database.md)   
 [ALTER DATABASE &#40;Azure SQL Database&#41;](../../t-sql/statements/alter-database-azure-sql-database.md)  
  
  
