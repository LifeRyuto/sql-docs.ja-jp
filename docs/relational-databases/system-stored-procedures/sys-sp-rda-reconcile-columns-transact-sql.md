---
title: sys.sp_rda_reconcile_columns (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_reconcile_columns
- sys.sp_rda_reconcile_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_reconcile_columns stored procedure
ms.assetid: 60d9cc4e-1828-450b-9d88-5b8485800d73
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 83ac2322d39fba05ce75f50fcd9cf9e5005b72b4
ms.sourcegitcommit: 5ed48c7dc6bed153079bc2b23a1e0506841310d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/21/2019
ms.locfileid: "65982987"
---
# <a name="syssprdareconcilecolumns-transact-sql"></a>sys.sp_rda_reconcile_columns (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Stretch 対応 SQL Server テーブル内の列には、リモート Azure テーブルの列を調整します。  
    
  **sp_rda_reconcile_columns**リモート テーブルではなく Stretch 対応 SQL Server テーブルに存在するリモート テーブルに列を追加します。 これらの列には、列をリモート テーブルから誤って削除した可能性があります。 ただし、 **sp_rda_reconcile_columns** SQL Server テーブルではなく、リモート テーブルに存在するリモート テーブルから列を削除しません。
  
  > [!IMPORTANT]
  > **sp_rda_reconcile_columns** がリモート テーブルから誤って削除した列を再作成する場合、削除された列に属していたデータは復元されません。
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
   
## <a name="syntax"></a>構文  
  
```  
  
sp_rda_reconcile_columns @objname = '@objname'  
  
```  
  
## <a name="arguments"></a>引数  
 \@objname = '*\@objname*'  
 Stretch 対応 SQL Server テーブルの名前。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または > 0 (失敗)  
  
## <a name="permissions"></a>アクセス許可  
 Db_owner アクセス許可が必要です。  
   
## <a name="remarks"></a>コメント  
 Stretch 対応の SQL Server テーブルに存在しなくなったリモートの Azure テーブルに列が存在している場合、これらの余分な列が Stretch Database の正常な動作を妨げることはありません。 必要に応じて余分の列を手動で削除できます。  
  
## <a name="example"></a>例  
 リモートの Azure テーブルの列を調整するには、次のステートメントを実行します。  
  
```sql  
EXEC sp_rda_reconcile_columns @objname = N'StretchEnabledTableName';  
```  
  
  
