---
title: sys.dm_pdw_sql_requests (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 44e19609-902c-46cf-acdf-19ea75011365
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 9a99d922dd8b57bb033f2a6ba13560c22c0eff6c
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56030813"
---
# <a name="sysdmpdwsqlrequests-transact-sql"></a>sys.dm_pdw_sql_requests (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  クエリでは、SQL の手順の一部としては、SQL Server クエリのすべてのディストリビューションに関する情報を保持します。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|この SQL クエリの分布が属している、クエリの一意の識別子。<br /><br /> request_id、step_index、および distribution_id は、このビューのキーを形成します。|Request_id 内を参照してください。 [sys.dm_pdw_exec_requests &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md)します。|  
|step_index|**int**|このような配布の一部であるクエリのステップのインデックスです。<br /><br /> request_id、step_index、および distribution_id は、このビューのキーを形成します。|Step_index を参照してください。 [sys.dm_pdw_request_steps &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md)します。|  
|pdw_node_id|**int**|このクエリの配布を実行するノードの一意の識別子。|Node_id を参照してください。 [sys.dm_pdw_nodes &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md)します。|  
|distribution_id|**int**|このクエリの配布を実行する配布の一意の識別子。<br /><br /> request_id、step_index、および distribution_id は、このビューのキーを形成します。|Distribution_id を参照してください。 [sys.pdw_distributions &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-distributions-transact-sql.md)します。 ノード スコープの配布のスコープではないで実行される要求の場合は-1 に設定されます。|  
|status|**nvarchar(32)**|クエリの分布の現在の状態。|保留中、実行して、失敗、取り消し済み、完了、中止、CancelSubmitted|  
|error_id|**nvarchar(36)**|エラーの一意識別子は、存在する場合に、このクエリの配布に関連付けられました。|Error_id を参照してください。 [sys.dm_pdw_errors &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-errors-transact-sql.md)します。 エラーが発生していない場合は、NULL に設定します。|  
|start_time|**datetime**|クエリでは、配布は実行を開始した時刻。|このクエリの分布が属している小さいまたは現在の時刻に等しいと大きいまたは等しい start_time のクエリのステップ|  
|end_time|**datetime**|このクエリの分布の実行完了したが取り消された場合、または失敗したの時間です。|以上の開始時刻、またはクエリの分布が継続的なまたはキューに置かれた場合は NULL に設定します。|  
|total_elapsed_time|**int**|クエリの配布が実行されている、ミリ秒単位で時間を表します。|大きいまたは 0 を設定します。 Start_time のデルタに等しいと end_time 完了済み、失敗、またはクエリの分布が取り消されました。<br /><br /> Total_elapsed_time では、整数の最大値を超えると、total_elapsed_time 引き続き、最大値になります。 この状態が"、最大値を超過しました"警告を生成します。<br /><br /> 最大値をミリ秒単位は 24.8 日に相当します。|  
|row_count|**bigint**|行の数は、変更されたか、このクエリの分布を読み取りません。|CREATE TABLE や DROP TABLE などのデータを取得または変更しない操作の場合は-1。|  
|spid|**int**|クエリの配布を実行している SQL Server インスタンス上のセッション id です。||  
|command|**nvarchar (4000)**|このクエリの配布用のコマンドの完全なテキスト。|有効なクエリまたは要求文字列。|  
  
 このビューで保持される最大行数は、詳細については、システム ビューの最大値」セクションを参照してください、[最小値と最大値 (SQL Server PDW)](https://msdn.microsoft.com/5243f018-2713-45e3-9b61-39b2a57401b9)トピック。  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse と Parallel Data Warehouse の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
