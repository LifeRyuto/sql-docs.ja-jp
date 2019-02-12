---
title: sys.pdw_nodes_partitions (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: b4216752-4813-4b2c-b259-7d8ffc6cc190
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: e70d11a9161461a01189bbfe69e1959eed124543
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56012553"
---
# <a name="syspdwnodespartitions-transact-sql"></a>sys.pdw_nodes_partitions (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  すべてのテーブルとインデックスでのほとんどの種類の各パーティションの行を格納、 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] データベース。 すべてのテーブルとインデックスには明示的にパーティション分割されているかどうかを示す、少なくとも 1 つのパーティションが含まれます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|partition_id|`bigint`|パーティションの id です。 データベース内で一意です。|  
|object_id|`int`|このパーティションが所属するオブジェクトの id。 すべてのテーブルまたはビューは 1 つ以上のパーティションで構成されます。|  
|index_id|`int`|このパーティションが所属するオブジェクト内のインデックスの id です。|  
|partition_number|`int`|所有しているインデックスまたはヒープ内の 1 から始まるパーティション番号。  [!INCLUDE[ssSDW](../../includes/sssdw-md.md)], 、この列の値は 1 です。|  
|hobt_id|`bigint`|このパーティションの行を保持するデータ ヒープまたは B ツリーの ID です。|  
|rows|`bigint`|このパーティション内の行の概数です。 |  
|data_compression|`int`|各パーティションの圧縮の状態を示します。<br /><br /> 0 = NONE<br /><br /> 1 = ROW<br /><br /> 2 = PAGE<br /><br /> 3 = COLUMNSTORE|  
|data_compression_desc|`nvarchar(60)`|各パーティションの圧縮状態を示します。 有効値は、NONE、ROW、および PAGE です。|  
|pdw_node_id|`int`|一意の識別子、 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] ノードです。|  
  
## <a name="permissions"></a>アクセス許可  
 CONTROL SERVER 権限が必要です。  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] および [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  

### <a name="example-a-display-rows-in-each-partition-within-each-distribution"></a>例 A:各配布内で各パーティション内の行を表示します。 

適用対象: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]
 
各配布内で各パーティションで行の数を表示する使用[DBCC PDW_SHOWPARTITIONSTATS (SQL Server PDW)](../../t-sql/database-console-commands/dbcc-pdw-showpartitionstats-transact-sql.md)します。

### <a name="example-b-uses-system-views-to-view-rows-in-each-partition-of-each-distribution-of-a-table"></a>例 B:システム ビューを使用して、各パーティション内の各ディストリビューション テーブルの行を表示するには

適用対象: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]
 
このクエリは、各パーティション内の各ディストリビューション テーブルの行の数を返します`myTable`します。  
 
```  
SELECT o.name, pnp.index_id, pnp.partition_id, pnp.rows,   
    pnp.data_compression_desc, pnp.pdw_node_id  
FROM sys.pdw_nodes_partitions AS pnp  
JOIN sys.pdw_nodes_tables AS NTables  
    ON pnp.object_id = NTables.object_id  
AND pnp.pdw_node_id = NTables.pdw_node_id  
JOIN sys.pdw_table_mappings AS TMap  
    ON NTables.name = TMap.physical_name 
    AND substring(TMap.physical_name,40, 10) = pnp.distribution_id 
JOIN sys.objects AS o  
    ON TMap.object_id = o.object_id  
WHERE o.name = 'myTable'  
ORDER BY o.name, pnp.index_id, pnp.partition_id;  
```    
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse と Parallel Data Warehouse カタログ ビュー](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  

