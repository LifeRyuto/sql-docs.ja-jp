---
title: sp_dropmergepartition (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_dropmergepartition_TSQL
- sp_dropmergepartition
helpviewer_keywords:
- sp_dropmergepartition
ms.assetid: 1be511c1-79ff-4947-9379-78d83b7b8945
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 74837390afe358d4f9a12d4f98ea9d2e4166e146
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58536094"
---
# <a name="spdropmergepartition-transact-sql"></a>sp_dropmergepartition (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  パブリケーションから、パラメーター化された行フィルターのパーティションを削除します。 このストアド プロシージャは、パブリッシャー、パブリケーション データベースに対して実行されます。 また、パーティションに対応するスナップショット ジョブとスナップショット ファイルも削除されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_dropmergepartition [ @publication = ] 'publication'  
        , [ @suser_sname = ] 'suser_sname'  
        , [ @host_name = ] 'host_name'  
```  
  
## <a name="arguments"></a>引数  
`[ @publication] = 'publication'` パブリケーションの名前です。 *パブリケーション* は **sysname** 、既定値はありません。  
  
`[ @suser_sname = ] 'suser_sname'` 値である、 [SUSER_SNAME](../../t-sql/functions/suser-sname-transact-sql.md)サブスクライバーでの関数は、パーティションの定義に使用します。 *suser_sname*は**sysname**、既定値はありません。  
  
`[ @host_name = ] 'host_name'` 値である、 [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md)サブスクライバーでの関数は、パーティションの定義に使用します。 *host_name*は**sysname**、既定値はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_dropmergepartition**はマージ レプリケーションで使用します。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_dropmergepartition**します。  
  
## <a name="see-also"></a>参照  
 [パラメーター化されたフィルターによるマージ パブリケーションのパーティションの管理](../../relational-databases/replication/publish/manage-partitions-for-a-merge-publication-with-parameterized-filters.md)  
  
  
