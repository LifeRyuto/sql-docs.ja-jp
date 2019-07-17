---
title: sp_browsereplcmds (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_browsereplcmds_TSQL
- sp_browsereplcmds
helpviewer_keywords:
- sp_browsereplcmds
ms.assetid: 30abcb41-1d18-4f43-a692-4c80914c0450
author: stevestein
ms.author: sstein
ms.openlocfilehash: b29ee604f1b584fcbdcd0ef91e32c84d89cc5f96
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68045992"
---
# <a name="spbrowsereplcmds-transact-sql"></a>sp_browsereplcmds (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ディストリビューション データベースに格納されているレプリケートされたコマンドの結果セットを判読可能な形で返します。診断ツールとして使用できます。 このストアド プロシージャは、ディストリビューター側でディストリビューション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_browsereplcmds [ [ @xact_seqno_start = ] 'xact_seqno_start' ]  
    [ , [ @xact_seqno_end = ] 'xact_seqno_end' ]   
    [ , [ @originator_id = ] 'originator_id' ]  
    [ , [ @publisher_database_id = ] 'publisher_database_id' ]  
    [ , [ @article_id = ] 'article_id' ]  
    [ , [ @command_id= ] command_id ]  
    [ , [ @agent_id = ] agent_id ]  
    [ , [ @compatibility_level = ] compatibility_level ]  
```  
  
## <a name="arguments"></a>引数  
`[ @xact_seqno_start = ] 'xact_seqno_start'` 返す最小の値を持つの正確なシーケンス番号を指定します。 *xact_seqno_start*は**nchar (22)** 、既定値は 0x00000000000000000000 です。  
  
`[ @xact_seqno_end = ] 'xact_seqno_end'` 返される最大の正確なシーケンス番号を指定します。 *xact_seqno_end*は**nchar (22)** 、既定値は 0 xffffffffffffffffffff です。  
  
`[ @originator_id = ] 'originator_id'` 場合を指定します。 指定したコマンド*originator_id*が返されます。 *originator_id*は**int**、既定値は NULL です。  
  
`[ @publisher_database_id = ] 'publisher_database_id'` 場合を指定します。 指定したコマンド*化コ*が返されます。 *化コ*は**int**、既定値は NULL です。  
  
`[ @article_id = ] 'article_id'` 場合を指定します。 指定したコマンド*コ*が返されます。 *コ*は**int**、既定値は NULL です。  
  
`[ @command_id = ] command_id` 内のコマンドの場所は、 [MSrepl_commands &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-tables/msrepl-commands-transact-sql.md)デコードします。 *command_id*は**int**、既定値は NULL です。 その他のすべてのパラメーターをさらに、指定する必要があります指定した場合と*xact_seqno_start*と同じである必要があります*xact_seqno_end*します。  
  
`[ @agent_id = ] agent_id` 特定のレプリケーション エージェントのコマンドのみが返されることを指定します。 *agent_id*は**int**既定値は NULL です。  
  
`[ @compatibility_level = ] compatibility_level` バージョンである[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を*compatibility_level*は**int**既定値は 9000000 です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**xact_seqno**|**varbinary(16)**|コマンドのシーケンス番号。|  
|**originator_srvname**|**sysname**|サーバーはトランザクションが発生します。|  
|**originator_db**|**sysname**|データベースのトランザクションが発生します。|  
|**article_id**|**int**|アーティクルの ID。|  
|**type**|**int**|コマンドの種類。|  
|**partial_command**|**bit**|部分的なコマンドかどうかを示します。|  
|**hashkey**|**int**|内部使用のみです。|  
|**originator_publication_id**|**int**|トランザクションが発生したパブリケーションの ID。|  
|**originator_db_version**|**int**|トランザクションが発生したデータベースのバージョンです。|  
|**originator_lsn**|**varbinary(16)**|発生元パブリケーションで、コマンドのログ シーケンス番号 (LSN) を識別します。 ピア ツー ピア トランザクション レプリケーションで使用されます。|  
|**command**|**nvarchar(1024)**|[!INCLUDE[tsql](../../includes/tsql-md.md)] コマンド。|  
|**command_id**|**int**|内のコマンドの ID [MSrepl_commands](../../relational-databases/system-tables/msrepl-commands-transact-sql.md)します。|  
  
 長いコマンドは、結果セット内でいくつかの行に分割できます。  
  
## <a name="remarks"></a>コメント  
 **sp_browsereplcmds**はトランザクション レプリケーションで使用します。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールのメンバーや、 **db_owner**または**replmonitor** を実行できるは、ディストリビューションデータベースの固定データベースロール**sp_browsereplcmds**します。  
  
## <a name="see-also"></a>関連項目  
 [sp_replcmds &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md)   
 [sp_replshowcmds &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replshowcmds-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
