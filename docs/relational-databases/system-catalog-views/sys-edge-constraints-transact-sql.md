---
title: edge_constraints (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 09/17/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.edge_constraints
- edge_constraints
- SQL Graph
- edge_constraints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.edge_constraints catalog view
ms.assetid: 0f782d2f-7126-46ab-85b7-bcba44862231
author: shkale-msft
ms.author: shkale
monikerRange: '>=sql-server-2017||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5dc2e47c49dc9d639489426fceab0b848c9def3e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68079323"
---
# <a name="sysedge_constraints-transact-sql"></a>edge_constraints (Transact-sql)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx.md](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

エッジ制約であるオブジェクトごとに1行のレコードを格納します。 
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**\<Sys. オブジェクトから継承された列>**||このビューが継承する列の一覧については、「 [sys. objects &#40;transact-sql&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)」を参照してください。|  
|**is_disabled**|**bit**|1 = エッジ制約は disbled です。<br /><br /> 0 = エッジ制約が有効です。|  
|**is_not_trusted**|**bit**|1 = エッジ制約は、システムによって検証されていません。<br /><br /> 0 = エッジ制約は、システムによって検証されています。|  
|**delete_referential_action**|**tinyint**|このエッジ制約で定義された参照アクション。<br /><br />0 = No Action。|  
|**delete_referential_action_desc**|**nvarchar (60)**|このエッジ制約で定義された参照アクションの説明です。<br /><br />NO_ACTION|  
|**is_system_named**|**bit**|1 = エッジ制約名がシステムによって生成されました。<br /><br />0 = エッジ制約名がユーザーによって指定されました。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]詳細については、「[メタデータ表示の構成](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [オブジェクトカタログビュー &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [SQL Server システム カタログに対するクエリに関してよく寄せられる質問](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
