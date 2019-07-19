---
title: sys.resource_stats (Azure SQL データベース) |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2018
ms.service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- resource_stats
- sys.resource_stats
- sys.resource_stats_TSQL
- resource_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.resource_stats
- resource_stats
ms.assetid: 02379a1b-3622-4578-8c59-a1b8f1a17914
author: julieMSFT
ms.author: jrasnick
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 06e3a3e632473c33a3f4652b2f4169ce3c7ca1e4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68097051"
---
# <a name="sysresourcestats-azure-sql-database"></a>sys.resource_stats (Azure SQL データベース)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Azure SQL データベースの CPU 使用率とストレージのデータを返します。 データは、5 分間隔で収集と集計が実行されます。 各ユーザー データベースの 1 行では、リソースの消費量の変更をすべて 5 分間のレポート ウィンドウのデータがあります。 返されるデータには、CPU 使用率、ストレージ サイズの変更、およびデータベース SKU の変更が含まれています。 アイドル状態のデータベースを変更せずに 5 分間隔の行がありません。 履歴データは約 14 日間保持されます。  
  
 **Sys.resource_stats**ビューでは、データベースが関連付けられている Azure SQL Database サーバーのバージョンによって異なる定義します。 新しいサーバー バージョンにアップグレードする際は、それら定義の違いとアプリケーションに必要な変更を考慮してください。  
  
 次の表は、v12 サーバーで使用できる列について説明しています。  
  
|[列]|データ型|説明|  
|----------------------------|---------------|-----------------|  
|start_time|**datetime**|5 分間のレポート期間の開始を示す UTC 時刻。|  
|end_time|**datetime**|5 分間のレポート期間の終了を示す UTC 時刻。|  
|database_name|**varchar**|ユーザー データベースの名前。|  
|sku|**varchar**|データベースのサービス階層。 使用できる値を次に示します。<br /><br /> Basic<br /><br /> Standard<br /><br /> Premium<br /><br />General Purpose<br /><br />Business Critical|  
|storage_in_megabytes|**float**|データベースのデータ、インデックス、ストアド プロシージャ、およびメタデータを含む、期間のメガバイト単位でストレージの最大サイズ。|  
|avg_cpu_percent|**numeric**|サービス層の上限に対するパーセンテージで示した、平均コンピューティング使用率。|  
|avg_data_io_percent|**numeric**|サービス層の上限に基づくパーセンテージで示した、平均入出力使用率。|  
|avg_log_write_percent|**numeric**|サービス層の上限に対するパーセンテージで示した、平均書き込みリソース使用率。|  
|max_worker_percent|**decimal(5,2)**|データベースのサービス層の限度に対する割合で表した最大同時実行ワーカー (要求)。<br /><br /> 最大値を現在の同時実行ワーカー数の 15 秒サンプルに基づいた、5 分間隔を計算します。|  
|max_session_percent|**decimal(5,2)**|データベースのサービス層の限度に対する割合で表した最大同時セッション数。<br /><br /> 最大値は現在の同時セッション数の 15 秒サンプルに基づいた、5 分間隔の計算されます。|  
|dtu_limit|**int**|現在データベースの最大 DTU このデータベースの設定この間隔中にします。 |  
|allocated_storage_in_megabytes|**float**|量では、ファイルの空き領域 (mb) のデータベースのデータを格納するために使用できる書式設定されます。 書式設定されたファイル領域は、"割り当てられているデータ領域"とも呼ばれます。  詳細については、以下をご覧ください。[SQL DB でのファイル領域の管理](https://docs.microsoft.com/azure/sql-database/sql-database-file-space-management)|
  
> [!TIP]  
>  これらの制限とサービス レベルに関する詳細なコンテキスト、トピックを参照してください。[サービス階層](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/)します。  
    
## <a name="permissions"></a>アクセス許可  
 このビューは、仮想に接続するアクセス許可を持つすべてのユーザー ロールに使用可能な**マスター**データベース。  
  
## <a name="remarks"></a>コメント  
 によって返されるデータ**sys.resource_stats**実行しているサービス階層/パフォーマンス レベルの制限が許容される最大の割合として表されます。  
  
 データベースがエラスティック プールのメンバーである場合は、割合の値として表示されるリソース統計は、エラスティック プールの構成で設定されているデータベースの最大制限の割合として表されます。  
  
 このデータの詳細なビューを使用して**sys.dm_db_resource_stats**ユーザー データベースでの動的管理ビュー。 このビューはデータを 15 秒ごとにキャプチャし、履歴データを 1 時間保持します。  詳細については、次を参照してください。 [sys.dm_db_resource_stats &#40;Azure SQL Database&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-resource-stats-azure-sql-database.md)します。  

## <a name="examples"></a>使用例  
 次の例では、過去 1 週間で平均してコンピューティング使用率が 80% 以上になっているすべてのデータベースが返されます。  
  
```sql  
DECLARE @s datetime;  
DECLARE @e datetime;  
SET @s= DateAdd(d,-7,GetUTCDate());  
SET @e= GETUTCDATE();  
SELECT database_name, AVG(avg_cpu_percent) AS Average_Compute_Utilization   
FROM sys.resource_stats   
WHERE start_time BETWEEN @s AND @e  
GROUP BY database_name  
HAVING AVG(avg_cpu_percent) >= 80  
```  
    
## <a name="see-also"></a>参照  
 [サービス レベル](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/)   
 [サービス層の機能と制限](https://azure.microsoft.com/documentation/articles/sql-database-performance-guidance/)  
  
  
