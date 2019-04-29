---
title: sp_browsesnapshotfolder (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_browsesnapshotfolder
- sp_browsesnapshotfolder_TSQL
helpviewer_keywords:
- sp_browsesnapshotfolder
ms.assetid: 0872edf2-4038-4bc1-a68d-05ebfad434d2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a2ace8d02997b7c0647be0b7abe26ff098849905
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62996266"
---
# <a name="spbrowsesnapshotfolder-transact-sql"></a>sp_browsesnapshotfolder (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  パブリケーションに対して生成された最新のスナップショットの完全なパスを返します。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_browsesnapshotfolder [@publication= ] 'publication'  
    { [ , [ @subscriber = ] 'subscriber' ]  
 [ , [ @subscriber_db = ] 'subscriber_db' ] }  
```  
  
## <a name="arguments"></a>引数  
`[ @publication = ] 'publication'` アーティクルを含むパブリケーションの名前です。 *パブリケーション* は **sysname** 、既定値はありません。  
  
`[ @subscriber = ] 'subscriber'` サブスクライバーの名前です。 *サブスクライバー* は **sysname** 、既定値は NULL です。  
  
`[ @subscriber_db = ] 'subscriber_db'` サブスクリプション データベースの名前です。 *@subscriber_db* は **sysname** 、既定値は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**snapshot_folder**|**nvarchar(512)**|スナップショット ディレクトリの完全パスです。|  
  
## <a name="remarks"></a>コメント  
 **sp_browsesnapshotfolder**スナップショット レプリケーションおよびトランザクション レプリケーションで使用されます。  
  
 場合、*サブスクライバー*と *@subscriber_db*フィールドが NULL のまま、ストアド プロシージャは、パブリケーションを検索できる最新のスナップショットのスナップショット フォルダーを返します。 場合、*サブスクライバー*と *@subscriber_db*フィールドを指定すると、ストアド プロシージャは、指定されたサブスクリプションのスナップショット フォルダーを返します。 パブリケーションに対するスナップショットが生成されていない場合は、空の結果セットが返されます。  
  
 パブリッシャーの作業ディレクトリとパブリッシャー スナップショット フォルダーの両方でスナップショット ファイルを生成するパブリケーションを設定する場合、結果セットには、2 つの行が含まれています。 第 1 の行にはパブリケーションのスナップショット フォルダーが含まれ、第 2 の行にはパブリッシャーの作業ディレクトリが含まれます。 **sp_browsesnapshotfolder**はスナップショット ファイルが生成されるディレクトリを決定するために便利です。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_browsesnapshotfolder**します。  
  
## <a name="see-also"></a>参照  
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
