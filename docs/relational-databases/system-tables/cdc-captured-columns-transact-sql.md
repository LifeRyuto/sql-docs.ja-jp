---
title: cdc. captured_columns (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- cdc.captured_columns
- cdc.captured_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- cdc.captured_columns
ms.assetid: 7bb4d408-d764-4ef6-802c-f271c8d39c2a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 96927e2c0a773674cbc4b8dabee804870d6559e1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68119258"
---
# <a name="cdccaptured_columns-transact-sql"></a>cdc.captured_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  キャプチャインスタンスで追跡されている列ごとに1行の値を返します。 既定では、ソーステーブルのすべての列がキャプチャされます。 ただし、列リストを指定することで、ソース テーブルでの変更データ キャプチャが有効になっているときに列を含めたり除外したりできます。 詳細については、「 [sys. sp_cdc_enable_table &#40;transact-sql&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-table-transact-sql.md)」を参照してください。  
  
 **システムテーブルに対して直接クエリを実行しない**ことをお勧めします。 代わりに、 [sp_cdc_get_source_columns](../../relational-databases/system-stored-procedures/sys-sp-cdc-get-captured-columns-transact-sql.md)ストアドプロシージャを実行します。  
   
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|キャプチャされた列が属するソーステーブルの ID。|  
|**column_name**|**sysname**|キャプチャされた列の名前です。|  
|**column_id**|**int**|ソーステーブル内のキャプチャされた列の ID。|  
|**column_type**|**sysname**|キャプチャされた列の種類。|  
|**column_ordinal**|**int**|変更テーブル内の列の序数 (1 から始まる)。 変更テーブル内のメタデータ列は除外されます。 最初にキャプチャされた列には、序数1が割り当てられます。|  
|**is_computed**|**bit**|キャプチャされた列がソーステーブル内の計算列であることを示します。|  
  
## <a name="see-also"></a>参照  
 [cdc. change_tables &#40;Transact-sql&#41;](../../relational-databases/system-tables/cdc-change-tables-transact-sql.md)  
  
  
