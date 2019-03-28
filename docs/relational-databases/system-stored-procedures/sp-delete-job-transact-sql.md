---
title: sp_delete_job (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_delete_job
- sp_delete_job_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_job
ms.assetid: b85db6e4-623c-41f1-9643-07e5ea38db09
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7b5ccd47f2b702c998a9e9268db523da1bfceaec
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58536684"
---
# <a name="spdeletejob-transact-sql"></a>sp_delete_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ジョブを削除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_delete_job { [ @job_id = ] job_id | [ @job_name = ] 'job_name' } ,  
     [ , [ @originating_server = ] 'server' ]   
     [ , [ @delete_history = ] delete_history ]  
     [ , [ @delete_unused_schedule = ] delete_unused_schedule ]  
```  
  
## <a name="arguments"></a>引数  
`[ @job_id = ] job_id` 削除するジョブの id 番号です。 *job_id*は**uniqueidentifier**、既定値は NULL です。  
  
`[ @job_name = ] 'job_name'` 削除するジョブの名前です。 *job_name*は**sysname**、既定値は NULL です。  
  
> [!NOTE]  
>  いずれか*job_id*または*job_name*指定する必要があります。 両方を指定することはできません。  
  
`[ @originating_server = ] 'server'` 内部で使用します。  
  
`[ @delete_history = ] delete_history` ジョブの履歴を削除するかどうかを指定します。 *delete_history*は**ビット**、既定値は**1**します。 ときに*delete_history*は**1**ジョブのジョブ履歴は削除します。 ときに*delete_history*は**0**、ジョブ履歴は削除されません。  
  
 ジョブの削除し、履歴は削除されませんが、ジョブの履歴情報が表示されないように注意してください、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェント グラフィカル ユーザー インターフェイスのジョブ履歴が、この情報は存在、 **sysjobhistory**テーブルに、 **msdb**データベース。  
  
`[ @delete_unused_schedule = ] delete_unused_schedule` かどうか、スケジュールを削除するジョブにアタッチされたこの、他のジョブにアタッチされていない場合を指定します。 *@delete_unused_schedule*は**ビット**、既定値は**1**します。 ときに *@delete_unused_schedule*は**1**、他のジョブにスケジュールが参照されていない場合、このジョブにアタッチされたスケジュールは削除されます。 ときに *@delete_unused_schedule*は**0**スケジュールは削除されません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>コメント  
 **@originating_server**引数は内部使用のため予約されています。  
  
 **@delete_unused_schedule**引数が自動的にすべてのジョブにアタッチされていないスケジュールを削除して以前のバージョンの SQL Server との下位互換性を提供します。 このパラメーターでは、既定で互換動作が設定されることに注意してください。 ジョブにアタッチされていないスケジュールを保持するには、値を指定する必要があります**0**として、 **@delete_unused_schedule**引数。  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] は、ジョブを簡単に管理できるグラフィカルなツールです。ジョブのインフラストラクチャを作成し、管理するには、このツールを使用することをお勧めします。  
  
 このストアド プロシージャでは、メンテナンス プランやメンテナンス プランの一部であるジョブを削除できません。 代わりに [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、メンテナンス プランを削除します。  
  
## <a name="permissions"></a>アクセス許可  
 既定では、このストアド プロシージャを実行できるのは、 **sysadmin** 固定サーバー ロールのメンバーです。 他のユーザーには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **データベースの次のいずれかの** エージェント固定データベース ロールが許可されている必要があります。  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 これらのロールの権限の詳細については、「 [SQL Server エージェントの固定データベース ロール](../../ssms/agent/sql-server-agent-fixed-database-roles.md)」を参照してください。  
  
 **sp_delete_job** を実行して任意のジョブを削除できるのは、 **sysadmin** 固定サーバー ロールのメンバーです。 **sysadmin** 固定サーバー ロールのメンバーでないユーザーは、自分が所有するジョブのみを削除できます。  
  
## <a name="examples"></a>使用例  
 次の例では、ジョブ `NightlyBackups` を削除します。  
  
```  
USE msdb ;  
GO  
  
EXEC sp_delete_job  
    @job_name = N'NightlyBackups' ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sp_add_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-job-transact-sql.md)   
 [sp_help_job &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-job-transact-sql.md)   
 [sp_update_job &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-job-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
