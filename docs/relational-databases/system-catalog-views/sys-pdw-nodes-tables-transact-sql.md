---
title: sys.pdw_nodes_tables (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 473b5d14-171b-4a16-9195-acf36d3f786c
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 99693b4261df24a666144f93dc07b8aaa68bc3d4
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56031283"
---
# <a name="syspdwnodestables-transact-sql"></a>sys.pdw_nodes_tables (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  プリンシパルが所有しているかまたはをプリンシパルが権限を許可されて、テーブル オブジェクトごとに 1 行が含まれています。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|  
|\<列を継承 >||このビューが継承する列の一覧は、次を参照してください。 [sys.objects](https://msdn.microsoft.com/c36fa71e-549a-4533-a6cd-1314d26f533f)します。||  
|lob_data_space_id|**int**||常に 0 です。|  
|filestream_data_space_id|**int**|データ領域の FILESTREAM ファイル グループの ID または [!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|NULL|  
|max_column_id_used|**int**|このテーブルで使用される列の最大の ID です。||  
|lock_on_bulk_load|**bit**|テーブルは、一括読み込みにロックされます。|TBD|  
|uses_ansi_nulls|**bit**|テーブルは、SET ANSI_NULLS データベース オプションが ON の場合に作成されます。|1|  
|is_replicated|**bit**|1 = テーブルは、レプリケーションを使用してパブリッシュします。|0 になります。レプリケーションがサポートされていません。|  
|has_replication_filter|**bit**|1 = テーブルにはレプリケーション フィルターがあります。|0|  
|is_merge_published|**bit**|1 = テーブルは、マージ レプリケーションを使用してパブリッシュされます。|0 になります。サポートされていません。|  
|is_sync_tran_subscribed|**bit**|1 = テーブルは、即時更新サブスクリプションを使用してサブスクライブされます。|0 になります。サポートされていません。|  
|has_unchecked_assembly_data|**bit**|1 = テーブルに、前回の ALTER ASSEMBLY で定義が変更されたアセンブリに依存する、持続データが含まれています。 次の成功した DBCC CHECKDB または DBCC CHECKTABLE の後に 0 にリセットされます。|0 になります。CLR はサポートされません。|  
|text_in_row_limit|**int**|0 = text in row オプションは設定されていません。|常に 0 です。|  
|large_value_types_out_of_row|**bit**|1 = 大きい値の型は行外に格納されます。|常に 0 です。|  
|is_tracked_by_cdc|**bit**|1 = テーブルは、変更データ キャプチャを有効には|常に 0 です。CDC はサポートされません。|  
|lock_escalation|**tinyint**|テーブルの LOCK_ESCALATION オプションの値です。2 = AUTO|常に 2 になります。|  
|lock_escalation_desc|**nvarchar(60)**|Lock_escalation オプションの説明テキストです。|常に ꞌAUTOꞌ です。|  
|pdw_node_id|**int**|一意の識別子、 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] ノードです。|NOT NULL|  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse と Parallel Data Warehouse カタログ ビュー](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
