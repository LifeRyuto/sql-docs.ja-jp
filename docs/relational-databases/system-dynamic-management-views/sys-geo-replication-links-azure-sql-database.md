---
title: sys.geo_replication_links (Azure SQL データベース) |Microsoft Docs
ms.custom: ''
ms.date: 01/28/2019
ms.service: sql-database
ms.reviewer: ''
ms.topic: conceptual
f1_keywords:
- dm_geo_replication_links_TSQL
- dm_geo_replication_links
- sys.dm_geo_replication_links
- sys.dm_geo_replication_links_TSQL
helpviewer_keywords:
- sys.dm_geo_replication_links dynamic management view
- dm_geo_replication_links dynamic management view
ms.assetid: 58911798-1d60-4f28-87ab-2def2bfc3de7
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 94ed170ea4aa99d861bea2e087310260982af4d3
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56031772"
---
# <a name="sysgeoreplicationlinks-azure-sql-database"></a>sys.geo_replication_links (Azure SQL Database)

[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  地理的レプリケーション パートナーでのプライマリおよびセカンダリ データベース間でのレプリケーション リンクごとに 1 行が含まれています。 このビューは、論理マスター データベースに存在します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|database_id|**int**|Sys.databases ビューでは、現在のデータベースの ID です。|  
|start_date|**datetimeoffset**|データベースのレプリケーションが開始されたときに地域別の SQL データベース datacenter の UTC 時刻|  
|modify_date|**datetimeoffset**|SQL データベースにデータ センター データベースの地理的レプリケーションが完了したときに地域別に UTC 時刻。 新しいデータベースは、この時点で、プライマリ データベースと同期されます。 .|  
|link_guid|**uniqueidentifier**|地理的レプリケーション リンクの一意の ID。|  
|partner_server|**sysname**|Geo レプリケートされたデータベースを含む SQL データベース サーバーの名前です。|  
|partner_database|**sysname**|リンクされた SQL データベース サーバーを geo レプリケートされたデータベースの名前。|  
|replication_state|**tinyint**|このデータベースには、いずれかの地理的レプリケーションの状態: です。<br /><br /> 0 = 保留中です。 アクティブなセカンダリ データベースの作成がスケジュールされているが、必要な準備手順がまだ完了していません。<br /><br /> 1 = シード処理中です。 地理的レプリケーションの対象がシード中は、2 つのデータベースがまだ同期されていません。 シードが完了するまでは、セカンダリ データベースに接続することはできません。 プライマリからセカンダリ データベースを削除すると、シード操作がキャンセルされます。<br /><br /> 2 = キャッチアップです。 セカンダリ データベースはトランザクション全体で一貫性のある状態でありが常に、プライマリ データベースと同期されています。|  
|replication_state_desc|**nvarchar (256)**|PENDING<br /><br /> SEEDING<br /><br /> CATCH_UP|  
|ロール (role)|**tinyint**|いずれかの地理的レプリケーション ロール:<br /><br /> 0 = プライマリです。 Database_id は、地理的レプリケーション パートナーシップのプライマリ データベースを参照します。<br /><br /> 1 = セカンダリです。  Database_id は、地理的レプリケーション パートナーシップのプライマリ データベースを参照します。|  
|role_desc|**nvarchar (256)**|PRIMARY<br /><br /> SECONDARY|  
|secondary_allow_connections|**tinyint**|いずれかのセカンダリ型。<br /><br /> 0 = いいえ。 フェールオーバーまで、セカンダリ データベースにアクセスできません。<br /><br /> 1 = 読み取り専用です。 セカンダリ データベースは ApplicationIntent でクライアント接続のみがアクセスできる = 読み取り専用です。<br /><br /> 2 = すべて。 セカンダリ データベースにはクライアントの接続にアクセスします。|  
|secondary_allow_connections _desc|**nvarchar (256)**|いいえ<br /><br /> All<br /><br /> 読み取り専用|  
  
## <a name="permissions"></a>アクセス許可

このビューはのみ利用可能、**マスター**データベース、サーバー レベル プリンシパル ログインをします。  
  
## <a name="example"></a>例

すべてのデータベースとその地理的レプリケーションのリンクを表示します。  

```sql
SELECT
     database_id  
   , start_date  
   , partner_server  
   , partner_database  
   , replication_state  
   , role_desc  
   , secondary_allow_connections_desc
FROM sys.geo_replication_links;  
```

## <a name="see-also"></a>参照

 [ALTER DATABASE (Azure SQL Database)](../../t-sql/statements/alter-database-azure-sql-database.md)   
 [sys.dm_geo_replication_link_status &#40;Azure SQL Database&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-geo-replication-link-status-azure-sql-database.md)   
 [sys.dm_operation_status &#40;Azure SQL Database&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-operation-status-azure-sql-database.md)  
