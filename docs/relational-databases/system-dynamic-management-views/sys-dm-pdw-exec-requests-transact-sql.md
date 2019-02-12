---
title: sys.dm_pdw_exec_requests (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 390225cc-23e8-4051-a5f6-221e33e4c0b4
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: edbed9f5f0e8672c4f779431f810099b50470a9a
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56016793"
---
# <a name="sysdmpdwexecrequests-transact-sql"></a>sys.dm_pdw_exec_requests (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  現在または最近アクティブになっているすべての要求に関する情報を保持して [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]です。 これには、要求/クエリごとに 1 行が一覧表示します。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|このビューのキーです。 要求に関連付けられている一意の数値 id です。|システム内のすべての要求間で一意です。|  
|session_id|**nvarchar(32)**|このクエリの実行に使用されたセッションに関連付けられた一意の数値 id です。 参照してください[sys.dm_pdw_exec_sessions &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md)します。||  
|status|**nvarchar(32)**|要求の現在の状態。|実行中 ' '、'中断'、'完了'、'キャンセル'、'失敗' です。|  
|submit_time|**datetime**|実行要求が送信された時刻。|有効な**datetime**より小さいか等しい start_time と現在の時刻。|  
|start_time|**datetime**|要求の実行が開始された時刻。|キューに置かれた要求の場合は NULLそれ以外の場合、有効な**datetime**小さいまたは現在の時刻と同じです。|  
|end_compile_time|**datetime**|エンジンが、要求のコンパイルを完了した時刻。|まだコンパイルされていない要求の場合は NULLそれ以外の場合、有効な**datetime** start_time よりも小さいと、現在の時刻。|
|end_time|**datetime**|時間を要求の実行完了、失敗したか、取り消されました。|キューまたはアクティブな要求の場合は nullそれ以外の場合、有効な**datetime**小さいまたは現在の時刻と同じです。|  
|total_elapsed_time|**int**|(ミリ秒単位)、要求を開始してから、実行の経過時間です。|0 ~ start_time と end_time の違い範囲。<br /><br /> Total_elapsed_time では、整数の最大値を超えると、total_elapsed_time 引き続き、最大値になります。 この状態が"、最大値を超過しました"警告を生成します。<br /><br /> 最大値をミリ秒単位は 24.8 日に相当します。|  
|ラベル●らべる○|**nvarchar (255)**|(省略可能) ラベル文字列がいくつかのクエリの SELECT ステートメントに関連付けられています。|任意の文字列を含む ' a ～ z'、' A ～ Z'、' 0-9'、'_' です。|  
|error_id|**nvarchar(36)**|存在する場合は、要求に関連付けられているエラーの一意の id。|参照してください[sys.dm_pdw_errors &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-errors-transact-sql.md); エラーが発生していない場合は NULL に設定します。|  
|database_id|**int**|コンテキストの明示的な (使用 DB_X など) によって使用されるデータベースの識別子です。|内の id を参照してください。 [sys.databases &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)します。|  
|command|**nvarchar (4000)**|ユーザーによって送信されると、要求の完全なテキストを保持します。|有効なクエリまたは要求テキスト。 4,000 バイトより長いクエリは切り捨てられます。|  
|resource_class|**nvarchar(20)**|この要求のリソース クラスです。 関連する参照**concurrency_slots_used**で[sys.dm_pdw_resource_waits &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-resource-waits-transact-sql.md)します。|SmallRC<br /><br /> MediumRC<br /><br /> LargeRC<br /><br /> XLargeRC|  
  
 このビューで保持される最大行数については、「最小値と最大値」を参照してください、[!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)]します。  
  
## <a name="permissions"></a>アクセス許可  
 VIEW SERVER STATE 権限が必要です。  
  
## <a name="security"></a>セキュリティ  
 sys.dm_pdw_exec_requests は、データベース固有のアクセス許可に従ってのクエリの結果をフィルターしていません。 VIEW SERVER STATE 権限を持つログインでも、結果をすべてのデータベースのクエリ結果を得ることができます。  
  
> [!WARNING]  
>  攻撃者は、sys.dm_pdw_exec_requests を使用して、データベース固有のアクセス許可がないと VIEW SERVER STATE 権限を保持するだけでは、特定のデータベース オブジェクトに関する情報を取得します。  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse と Parallel Data Warehouse の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
