---
title: dm_db_xtp_transactions (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 08/29/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_db_xtp_transactions
- sys.dm_db_xtp_transactions_TSQL
- dm_db_xtp_transactions
- dm_db_xtp_transactions_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_xtp_transactions dynamic management view
ms.assetid: 5c1a0a7a-e851-4b6f-8dfd-c9655fbf5a51
author: stevestein
ms.author: sstein
monikerRange: =azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: cc5f12e50c1e7a7d639acdbf9a244406ce9366c6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68097933"
---
# <a name="sysdm_db_xtp_transactions-transact-sql"></a>sys.dm_db_xtp_transactions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  インメモリ OLTP データベース エンジンのアクティブなトランザクションを報告します。  
  
 詳細については、「[インメモリ OLTP &#40;インメモリ最適化&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)」を参照してください。  
    
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|xtp_transaction_id|**bigint**|XTP トランザクションマネージャーでのこのトランザクションの内部 ID。|  
|transaction_id|**bigint**|トランザクション ID。 他のトランザクション関連の DMV (sys.dm_tran_active_transactions など) にあるトランザクション ID と結合されます。<br /><br /> ネイティブ コンパイル ストアド プロシージャによって開始されたトランザクションなど、XTP のみのトランザクションの場合は 0 です。|  
|session_id|**smallint**|このトランザクションを実行しているセッションのセッション識別子。 sys.dm_exec_sessions と結合されます。|  
|begin_tsn|**bigint**|トランザクションの開始トランザクションのシリアル番号。|  
|end_tsn|**bigint**|トランザクションの終了トランザクションのシリアル番号。|  
|state|**int**|トランザクションの状態。<br /><br /> 0=ACTIVE<br /><br /> 1=COMMITTED<br /><br /> 2=ABORTED<br /><br /> 3=VALIDATING|  
|state_desc|**nvarchar**|トランザクションの状態の説明。|  
|result|**int**|このトランザクションの結果。 有効な値を次に示します。<br /><br /> 0 - IN PROGRESS<br /><br /> 1-成功<br /><br /> 2-エラー<br /><br /> 3 - COMMIT DEPENDENCY<br /><br /> 4 - VALIDATION FAILED (RR)<br /><br /> 5-検証に失敗しました (SR)<br /><br /> 6-ロールバック|  
|result_desc|**nvarchar**|このトランザクションの結果。 有効な値を次に示します。<br /><br /> IN PROGRESS<br /><br /> SUCCESS<br /><br /> ERROR<br /><br /> コミットの依存関係<br /><br /> 検証に失敗しました (RR)<br /><br /> VALIDATION FAILED (SR)<br /><br /> ROLLBACK|  
|last_error|**int**|内部でのみ使用されます|  
|is_speculative|**bit**|内部でのみ使用されます|  
|is_prepared|**bit**|内部でのみ使用されます|  
|is_delayed_durability|**bit**|内部でのみ使用されます|  
|memory_address|**varbinary**|内部でのみ使用されます|  
|database_address|**varbinary**|内部でのみ使用されます|  
|thread_id|**int**|内部でのみ使用されます|  
|read_set_row_count|**int**|内部でのみ使用されます|  
|write_set_row_count|**int**|内部でのみ使用されます|  
|scan_set_count|**int**|内部でのみ使用されます|  
|savepoint_garbage_count|**int**|内部でのみ使用されます|  
|log_bytes_required|**bigint**|内部でのみ使用されます|  
|count_of_allocations|**int**|内部でのみ使用されます|  
|allocated_bytes|**int**|内部でのみ使用されます|  
|reserved_bytes|**int**|内部でのみ使用されます|  
|commit_dependency_count|**int**|内部でのみ使用されます|  
|commit_dependency_total_attempt_count|**int**|内部でのみ使用されます|  
|scan_area|**int**|内部でのみ使用されます|  
|scan_area_desc|**nvarchar**|内部でのみ使用されます|  
|scan_location|**int**|内部使用のみです。|  
|dependent_1_address|**varbinary (8)**|内部でのみ使用されます|  
|dependent_2_address|**varbinary (8)**|内部でのみ使用されます|  
|dependent_3_address|**varbinary (8)**|内部でのみ使用されます|  
|dependent_4_address|**varbinary (8)**|内部でのみ使用されます|  
|dependent_5_address|**varbinary (8)**|内部でのみ使用されます|  
|dependent_6_address|**varbinary (8)**|内部でのみ使用されます|  
|dependent_7_address|**varbinary (8)**|内部でのみ使用されます|  
|dependent_8_address|**varbinary (8)**|内部でのみ使用されます|  
  
## <a name="permissions"></a>アクセス許可  
 サーバーに対する VIEW DATABASE STATE 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [メモリ最適化テーブルの動的管理ビュー &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)  
  
  
