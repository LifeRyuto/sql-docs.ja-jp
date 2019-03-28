---
title: sp_helpmergearticlecolumn (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpmergearticlecolumn
- sp_helpmergearticlecolumn_TSQL
helpviewer_keywords:
- sp_helpmergearticlecolumn
ms.assetid: 651c017b-9e9a-48f2-a0bd-6fc896eab334
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2221762934011c2268a40d0162bde7e62dbcf256
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58528224"
---
# <a name="sphelpmergearticlecolumn-transact-sql"></a>sp_helpmergearticlecolumn (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  マージ パブリケーションの指定のテーブルまたはビュー アーティクル内の列の一覧を返します。 ストアド プロシージャには列がないので、アーティクルとしてストアド プロシージャを指定してこのストアド プロシージャを実行するとエラーが返されます。 このストアド プロシージャは、パブリッシャー、パブリケーション データベースに対して実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helpmergearticlecolumn [ @publication = ] 'publication' ]  
        , [ @article= ] 'article' ]  
```  
  
## <a name="arguments"></a>引数  
`[ @publication = ] 'publication'` パブリケーションの名前です。*パブリケーション*は**sysname**、既定値はありません。  
  
`[ @article = ] 'article'` テーブルまたは情報を取得するアーティクルであるビューの名前です。*記事*は**sysname**、既定値はありません。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**column_id**|**sysname**|列を識別します。|  
|**column_name**|**sysname**|テーブルまたはビューの列の名前です。|  
|**公開**|**bit**|列名がパブリッシュされているかどうかを指定します。<br /><br /> **1**列がパブリッシュされていることを指定します。<br /><br /> **0**公開しないことを指定します。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_helpmergearticlecolumn**はマージ レプリケーションで使用します。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **replmonitor**ディストリビューション データベースまたはパブリケーションのパブリケーション アクセス リストの固定データベース ロールが実行できる**sp_helpmergearticlecolumn**します。  
  
## <a name="see-also"></a>参照  
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
