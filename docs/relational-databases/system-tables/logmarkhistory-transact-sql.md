---
title: logmarkhistory (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- logmarkhistory
- logmarkhistory_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- logmarkhistory system table
ms.assetid: 5c1becc5-f34e-4869-bf69-dfafab684540
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0674bf993087b349d4e8b6f9947c65167e94df8e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68001804"
---
# <a name="logmarkhistory-transact-sql"></a>logmarkhistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  予約されているマークされたトランザクションごとに1行のレコードを格納します。 このテーブルは、 **msdb**データベースに格納されます。  
  

|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**database_name**|**nvarchar(128**|マークされたトランザクションが発生したローカルデータベース。|  
|**mark_name**|**nvarchar(128**|マークされたトランザクションのユーザー指定の名前。|  
|**記述**|**nvarchar(255)**|マーク付きのトランザクションに指定されたユーザー定義の説明。 NULL にすることができます。|  
|**user_name**|**nvarchar(128**|マーク付きのトランザクションを実行したデータベース ユーザー名。 NULL にすることができます。|  
|**lsn**|**数値 (25, 0)**|マークが発生したトランザクションレコードのログシーケンス番号。|  
|**mark_time**|**DATETIME**|マークされたトランザクションのコミット時間 (ローカル時刻)。|  
  
## <a name="see-also"></a>参照  
 [マークされたトランザクション &#40;SQL Server Management Studio にデータベースを復元する&#41;](../../relational-databases/backup-restore/restore-a-database-to-a-marked-transaction-sql-server-management-studio.md)   
 [マークされたトランザクションを使用して、関連するデータベースを完全復旧モデル &#40;一貫して復旧&#41;](../../relational-databases/backup-restore/use-marked-transactions-to-recover-related-databases-consistently.md)   
 [システムテーブル &#40;Transact-sql&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
