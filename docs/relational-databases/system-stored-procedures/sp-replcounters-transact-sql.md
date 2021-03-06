---
title: sp_replcounters (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replcounters
- sp_replcounters_TSQL
helpviewer_keywords:
- sp_replcounters
ms.assetid: fe585b1f-edda-421f-81d6-8a03a3a535d2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 12ddbfe11a2b1a29dadaacde845f96e70959bebb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68770999"
---
# <a name="sp_replcounters-transact-sql"></a>sp_replcounters (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  パブッリッシュされたデータベースごとに、待機時間、スループット、トランザクション数に関するレプリケーションの統計を返します。 このストアドプロシージャは、パブリッシャー側で任意のデータベースに対して実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_replcounters  
  
```  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**[データベース]**|**sysname**|データベースの名前。|  
|**replicated transactions**|**int**|ディストリビューションデータベースへの配信を待機しているログ内のトランザクションの数。|  
|**レプリケーションレートトランザクション/秒**|**float**|ディストリビューションデータベースに1秒間に配信された平均トランザクション数。|  
|**レプリケーションの潜在期間**|**float**|トランザクションがログに記録されてから、配布されるまでの平均時間 (秒)。|  
|**replbeginlsn**|**binary (10)**|ログ内の現在の切り捨てポイントのログシーケンス番号 (LSN)。|  
|**Replnextlsn**|**binary (10)**|ディストリビューション データベースへの配信を待機する、次のコミット レコードの LSN。|  
  
## <a name="remarks"></a>解説  
 **sp_replcounters**は、トランザクションレプリケーションで使用します。  
  
## <a name="permissions"></a>アクセス許可  
 **Db_owner**固定データベースロールまたは**sysadmin**固定サーバーロールのメンバーシップが必要です。  
  
## <a name="see-also"></a>参照  
 [sp_replcmds &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md)   
 [sp_repldone &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-repldone-transact-sql.md)   
 [sp_replflush &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-replflush-transact-sql.md)   
 [システムストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
