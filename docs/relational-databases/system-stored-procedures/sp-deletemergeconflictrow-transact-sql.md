---
title: sp_deletemergeconflictrow (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_deletemergeconflictrow
- sp_deletemergeconflictrow_TSQL
helpviewer_keywords:
- sp_deletemergeconflictrow
ms.assetid: 64cf1186-28b8-4cd9-88f1-a7808a9c8d60
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5bef3e4902562edde0adb2a4f495c51e6a82b091
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58535284"
---
# <a name="spdeletemergeconflictrow-transact-sql"></a>sp_deletemergeconflictrow (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  競合テーブルから行を削除または[MSmerge_conflicts_info &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-tables/msmerge-conflicts-info-transact-sql.md)テーブル。 このストアド プロシージャは、競合テーブルが格納されているコンピューターの、任意のデータベース上で実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_deletemergeconflictrow [ [ @conflict_table = ] 'conflict_table' ]  
    [ , [ @source_object = ] 'source_object' ]  
    { , [ @rowguid = ] 'rowguid'  
        , [ @origin_datasource = ] 'origin_datasource' ] }  
    [ , [ @drop_table_if_empty = ] 'drop_table_if_empty' ]  
```  
  
## <a name="arguments"></a>引数  
`[ @conflict_table = ] 'conflict_table'` 競合テーブルの名前です。 *conflict_table*は**sysname**、既定値は **%** します。 場合、 *conflict_table*は NULL として指定または**%**、競合が削除競合と一致する行があると見なされます*rowguid*と*origin_datasource*と*source_object*から削除されて、 [MSmerge_conflicts_info &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-tables/msmerge-conflicts-info-transact-sql.md)テーブル。  
  
`[ @source_object = ] 'source_object'` ソース テーブルの名前です。 *source_object*は**nvarchar (386)**、既定値は NULL です。  
  
`[ @rowguid = ] 'rowguid'` 削除競合の行の識別子です。 *rowguid*は**uniqueidentifier**、既定値はありません。  
  
`[ @origin_datasource = ] 'origin_datasource'` 競合の元です。 *origin_datasource*は**varchar (255)**、既定値はありません。  
  
`[ @drop_table_if_empty = ] 'drop_table_if_empty'` あることを示すフラグです、 *conflict_table*削除場合は空です。 *drop_table_if_empty*は**varchar (10)**、既定値は FALSE。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_deletemergeconflictrow**はマージ レプリケーションで使用します。  
  
 [MSmerge_conflicts_info &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-tables/msmerge-conflicts-info-transact-sql.md)テーブルはシステム テーブルであり、空である場合でも、データベースからは削除されません。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_deletemergeconflictrow**します。  
  
## <a name="see-also"></a>参照  
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
