---
title: sys.pdw_table_distribution_properties (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 639a7475-7c92-41e0-a8ab-ad630eb5aea3
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 33d6ad4a8a22186fdf6174a0605eadfe62108dee
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56035623"
---
# <a name="syspdwtabledistributionproperties-transact-sql"></a>sys.pdw_table_distribution_properties (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  テーブルの情報の配布を保持します。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|  
|**object_id**|**int**|プロパティが指定されている前提とするテーブルの ID。||  
|**distribution_policy**|**tinyint**|0 = 定義されていません。<br /><br /> 1 = なし<br /><br /> 2 = ハッシュ<br /><br /> 3 = REPLICATE<br /><br /> 4 = ROUND_ROBIN|REPLICATE にのみ適用されます[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]します。|  
|**distribution_policy_desc**|**nvarchar(60)**|定義されていないなしでは、ハッシュ、複製、SEGMENTED_HEAP|[!INCLUDE[ssSDW](../../includes/sssdw-md.md)] ハッシュまたは複製を返します。|  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse と Parallel Data Warehouse カタログ ビュー](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
