---
title: restorefile (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- restorefile
- restorefile_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- restorefile system table
- restoring files [SQL Server], restorefile system table
- file restores [SQL Server], restorefile system table
ms.assetid: 8e40145a-8559-4abe-8e2a-39b818928009
author: stevestein
ms.author: sstein
ms.openlocfilehash: 788d0296087ee8980be0b0ecf56c43f09fb3780c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67910189"
---
# <a name="restorefile-transact-sql"></a>restorefile (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  復元されたファイルごとに 1 行のデータを格納します。復元されたファイルには、ファイル グループ名から間接的に復元されたものも含まれます。 このテーブルは、 **msdb**データベースに格納されます。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**restore_history_id**|**int**|対応する復元操作を特定するための一意な識別番号。 **Restorehistory (restore_history_id)** を参照します。|  
|**file_number**|**numeric (10, 0)**|復元されたファイルのファイル識別番号。 この値は、各データベース内で一意である必要があります。 NULL にすることができます。<br /><br /> データベースをデータベーススナップショットに戻すと、完全復元の場合と同じ方法でこの値が設定されます。|  
|**destination_phys_drive**|**nvarchar (260)**|ファイルが復元されたドライブまたはパーティション。 NULL にすることができます。<br /><br /> データベースをデータベーススナップショットに戻すと、完全復元の場合と同じ方法でこの値が設定されます。|  
|**destination_phys_name**|**nvarchar (260)**|ファイルの復元先のファイル名。ドライブやパーティション情報は含みません。 NULL にすることができます。<br /><br /> データベースをデータベーススナップショットに戻すと、完全復元の場合と同じ方法でこの値が設定されます。|  
  
## <a name="remarks"></a>解説  
 このテーブルおよびその他のバックアップテーブルと履歴テーブルの行の数を減らすには、 [sp_delete_backuphistory](../../relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql.md)ストアドプロシージャを実行します。  
  
## <a name="see-also"></a>参照  
 [Transact-sql&#41;&#40;のテーブルのバックアップと復元](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)   
 [restorefilegroup &#40;Transact-sql&#41;](../../relational-databases/system-tables/restorefilegroup-transact-sql.md)   
 [restorehistory &#40;Transact-sql&#41;](../../relational-databases/system-tables/restorehistory-transact-sql.md)   
 [システムテーブル &#40;Transact-sql&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
