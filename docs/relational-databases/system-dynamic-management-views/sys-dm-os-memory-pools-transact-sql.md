---
title: dm_os_memory_pools (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_os_memory_pools_TSQL
- dm_os_memory_pools
- dm_os_memory_pools_TSQL
- sys.dm_os_memory_pools
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_memory_pools dynamic management view
ms.assetid: 1ef053f3-c6f3-456e-82b6-26e4bd630d46
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: dbd5ce36c9d83eb6347bcba71c26c3fd71c4513d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68265738"
---
# <a name="sysdm_os_memory_pools-transact-sql"></a>dm_os_memory_pools (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンス内のオブジェクトストアごとに1行の値を返します。 このビューを使用すると、キャッシュメモリの使用状況を監視し、無効なキャッシュ動作を識別できます。  
  
> [!NOTE]  
>  またはから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]これを[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]呼び出すには、 **dm_pdw_nodes_os_memory_pools**という名前を使用します。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**memory_pool_address**|**varbinary (8)**|メモリ プールを表すエントリのメモリ アドレス。 NULL 値は許可されません。|  
|**pool_id**|**int**|プールのセット内にある特定プールの ID。 NULL 値は許可されません。|  
|**type**|**nvarchar (60)**|オブジェクトプールの種類。 NULL 値は許可されません。 詳細については、「 [sys. dm_os_memory_clerks &#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql.md)」を参照してください。|  
|**name**|**nvarchar(256)**|システムによって割り当てられた、メモリ オブジェクトの名前。 NULL 値は許可されません。|  
|**max_free_entries_count**|**bigint**|プールに含めることができる空きエントリの最大数。 NULL 値は許可されません。|  
|**free_entries_count**|**bigint**|現在プール内にある空きエントリ数。 NULL 値は許可されません。|  
|**removed_in_all_rounds_count**|**bigint**|
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの起動後、プールから削除されたエントリ数。 NULL 値は許可されません。|  
|**pdw_node_id**|**int**|**適用対象**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> このディストリビューションが配置されているノードの識別子。|  
  
## <a name="permissions"></a>アクセス許可

で[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]は、 `VIEW SERVER STATE`権限が必要です。   
Premium [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]レベルでは、データベース`VIEW DATABASE STATE`の権限が必要です。 Standard [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]レベルおよび Basic レベルでは、**サーバー管理**者または**Azure Active Directory 管理者**アカウントが必要です。   

## <a name="remarks"></a>解説  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コンポーネントは、共通のプールフレームワークを使用して、同種のステートレスなデータをキャッシュすることがあります。 プール フレームワークは、キャッシュ フレームワークよりも単純です。 プール内のすべてのエントリが等しいと見なされます。 内部的には、プールはメモリ クラークであり、メモリ クラークが使用される場所で使用できます。  
  
## <a name="see-also"></a>参照  
 
  [SQL Server オペレーティングシステム関連の動的管理ビュー &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


