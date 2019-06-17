---
title: sp_add_jobstep (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_jobstep_TSQL
- sp_add_jobstep
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_jobstep
ms.assetid: 97900032-523d-49d6-9865-2734fba1c755
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 112afe8f7a8eaea87c860264c820c874788cbc7f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66500357"
---
# <a name="spaddjobstep-transact-sql"></a>sp_add_jobstep (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss-xxxx-xxxx-xxx-md.md)]

  ジョブにステップ (操作) を追加します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```
sp_add_jobstep [ @job_id = ] job_id | [ @job_name = ] 'job_name'   
     [ , [ @step_id = ] step_id ]   
     { , [ @step_name = ] 'step_name' }   
     [ , [ @subsystem = ] 'subsystem' ]   
     [ , [ @command = ] 'command' ]   
     [ , [ @additional_parameters = ] 'parameters' ]   
          [ , [ @cmdexec_success_code = ] code ]   
     [ , [ @on_success_action = ] success_action ]   
          [ , [ @on_success_step_id = ] success_step_id ]   
          [ , [ @on_fail_action = ] fail_action ]   
          [ , [ @on_fail_step_id = ] fail_step_id ]   
     [ , [ @server = ] 'server' ]   
     [ , [ @database_name = ] 'database' ]   
     [ , [ @database_user_name = ] 'user' ]   
     [ , [ @retry_attempts = ] retry_attempts ]   
     [ , [ @retry_interval = ] retry_interval ]   
     [ , [ @os_run_priority = ] run_priority ]   
     [ , [ @output_file_name = ] 'file_name' ]   
     [ , [ @flags = ] flags ]   
     [ , { [ @proxy_id = ] proxy_id   
         | [ @proxy_name = ] 'proxy_name' } ]  
```  
  
## <a name="arguments"></a>引数  
`[ @job_id = ] job_id` ステップを追加するジョブの識別番号。 *job_id*は**uniqueidentifier**、既定値は NULL です。  
  
`[ @job_name = ] 'job_name'` ステップを追加するジョブの名前。 *job_name*は**sysname**、既定値は NULL です。  
  
> [!NOTE]  
>  いずれか*job_id*または*job_name*指定する必要がありますが、両方を指定することはできません。  
  
`[ @step_id = ] step_id` ジョブ ステップのシーケンス id 番号。 ステップの識別番号の始まり**1**と隙間なく増分します。 既存のシーケンスにステップを挿入すると、シーケンス番号が自動的に調整されます。 値を指定する場合は*step_id*が指定されていません。 *step_id*は**int**、既定値は NULL です。  
  
`[ @step_name = ] 'step_name'` ステップの名前。 *step_name*は**sysname**、既定値はありません。  
  
`[ @subsystem = ] 'subsystem'` によって使用されるサブシステム、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェント サービスを実行する*コマンド*します。 *サブシステム*は**nvarchar (40)** 、これらの値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|'**ACTIVESCRIPTING**'|アクティブ スクリプト<br /><br /> **\*\* 重要 \*\*** [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]|  
|'**CMDEXEC**'|オペレーティング システム コマンドまたは実行可能なプログラム|  
|'**配布**'|レプリケーション ディストリビューション エージェント ジョブ|  
|'**スナップショット**'|レプリケーション スナップショット エージェント ジョブ|  
|'**ログリーダー**'|レプリケーション ログ リーダー エージェント ジョブ|  
|'**マージ**'|レプリケーション マージ エージェント ジョブ|  
|'**QueueReader**'|レプリケーション キュー リーダー エージェント ジョブ|  
|'**ANALYSISQUERY**'|Analysis Services クエリ (MDX、DMX)。|  
|'**ANALYSISCOMMAND**'|Analysis Services コマンド (XMLA)|  
|'**Dts**'|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージ実行|  
|'**PowerShell**'|PowerShell スクリプト|  
|'**TSQL**' (既定値)|[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメント|  
  
`[ @command = ] 'command'` によって実行されるコマンド**SQLServerAgent**サービス*サブシステム*します。 *コマンド*は**nvarchar (max)** 、既定値は NULL です。 SQL Server エージェントでは、ソフトウェア プログラムを記述するときの変数と同じような柔軟性を持つトークン置換を使用できます。  
  
> [!IMPORTANT]  
>  エスケープ マクロがジョブ ステップで使用されるすべてのトークンを含める必要があります。 そう、ジョブ ステップは失敗します。 さらに、ようになりましたトークン名をかっこで囲みしてドル記号 (`$`)、トークン構文の先頭にします。 例 :  
>   
>  `$(ESCAPE_` *マクロ名* `(DATE))`  
  
 これらのトークンと、新しいトークン構文を使用するジョブ ステップの更新の詳細については、次を参照してください。[ジョブ ステップでトークンを使用して](../../ssms/agent/use-tokens-in-job-steps.md)します。  
  
> [!IMPORTANT]  
>  Windows イベント ログに対して書き込みのアクセス許可を持っている Windows ユーザーであればだれでも、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの警告または WMI 警告によってアクティブ化されるジョブ ステップにアクセスできます。 このセキュリティ上のリスクを避けるために、警告によってアクティブになるジョブで使用できる [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント トークンは、既定で無効になっています。 このようなトークンには、**A-DBN**、**A-SVR**、**A-ERR**、**A-SEV**、**A-MSG**、**WMI(** _property_ **)** があります。 このリリースでは、トークンの使用はすべての警告に拡張されていることに注意してください。  
>   
>  これらのトークンを使用する必要がある場合は、まず、Administrators グループなどの信頼されている Windows セキュリティ グループのメンバーのみが、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が存在するコンピューターのイベント ログに対して書き込みのアクセス許可を持っていることを確認してください。 確認したら、[オブジェクト エクスプローラー] で **[SQL Server エージェント]** を右クリックし、 **[プロパティ]** をクリックします。次に、 **[警告システム]** ページで、 **[警告に応答するすべてのジョブのトークンを置き換える]** チェック ボックスをオンにして、これらのトークンを有効にします。  
  
`[ @additional_parameters = ] 'parameters'` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)] *パラメーター*は**ntext**、既定値は NULL です。  
  
`[ @cmdexec_success_code = ] code` によって返される値、 **CmdExec**を示すサブシステム コマンド*コマンド*が正常に実行します。 *コード*は**int**、既定値は**0**します。  
  
`[ @on_success_action = ] success_action` ステップが成功した場合に実行するアクション。 *success_action*は**tinyint**、これらの値のいずれかを指定できます。  
  
|値|説明 (動作)|  
|-----------|----------------------------|  
|**1** (既定値)|正常終了します。|  
|**2**|失敗した状態で終了します。|  
|**3**|次のステップに進みます。|  
|**4**|手順に進みます*on_success_step_id*|  
  
`[ @on_success_step_id = ] success_step_id` ステップが成功した場合に実行するこのジョブ ステップの ID と*success_action*は**4**します。 *success_step_id*は**int**、既定値は**0**します。  
  
`[ @on_fail_action = ] fail_action` ステップが失敗した場合に実行するアクション。 *fail_action*は**tinyint**、これらの値のいずれかを指定できます。  
  
|値|説明 (動作)|  
|-----------|----------------------------|  
|**1**|正常終了します。|  
|**2** (既定値)|失敗した状態で終了します。|  
|**3**|次のステップに進みます。|  
|**4**|手順に進みます*on_fail_step_id*|  
  
`[ @on_fail_step_id = ] fail_step_id` ステップが失敗した場合に実行するこのジョブ ステップの ID と*fail_action*は**4**します。 *fail_step_id*は**int**、既定値は**0**します。  
  
`[ @server = ] 'server'` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)] *server*は**nvarchar (30)** 、既定値は NULL です。  
  
`[ @database_name = ] 'database'` 実行するためのデータベースの名前、[!INCLUDE[tsql](../../includes/tsql-md.md)]手順。 *データベース*は**sysname**、既定値は null の場合、この場合、**マスター**データベースが使用されます。 角かっこ () で囲まれた名前を指定することはできません。 ActiveX ジョブ ステップでは、*データベース*ステップを使用するスクリプト言語の名前を指定します。  
  
`[ @database_user_name = ] 'user'` 実行時に使用するユーザー アカウントの名前、[!INCLUDE[tsql](../../includes/tsql-md.md)]手順。 *ユーザー*は**sysname**、既定値は NULL です。 ときに*ユーザー*が null の場合、手順は、ジョブの所有者のユーザー コンテキストで実行すると、*データベース*します。  SQL Server エージェント ジョブの所有者が SQL Server sysadmin である場合にのみこのパラメーターが含まれます。 そのため、指定された TRANSACT-SQL ステップ実行する場合は、特定の SQL Server ユーザー名のコンテキストでします。 ジョブ所有者が、SQL Server sysadmin でないかどうかは、TRANSACT-SQL ステップは、このジョブを所有するログインのコンテキストで常に実行して、@database_user_nameパラメーターは無視されます。  
  
`[ @retry_attempts = ] retry_attempts` 再試行の回数は、このステップが失敗した場合は、使用しようとします。 *retry_attempts*は**int**、既定値は**0**でないことを示します再試行しようとします。  
  
`[ @retry_interval = ] retry_interval` 再試行間隔を分単位の時間数。 *retry_interval*は**int**、既定値は**0**を示す、 **0**-分までの間隔。  
  
`[ @os_run_priority = ] run_priority` 予約されています。  
  
`[ @output_file_name = ] 'file_name'` このステップの出力を保存するファイルの名前。 *file_name*は**nvarchar (200)** 、既定値は NULL です。 *file_name*で説明したトークンの 1 つ以上含めることができます*コマンド*します。 実行されているコマンドでのみこのパラメーターは有効、 [!INCLUDE[tsql](../../includes/tsql-md.md)]、 **CmdExec**、 **PowerShell**、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]、または[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]サブシステム。  
  
`[ @flags = ] flags` 動作を制御するオプションです。 *フラグ*は**int**、これらの値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**0** (既定値)|出力ファイルを上書き|  
|**2**|出力ファイルに追加します。|  
|**4**|書き込み[!INCLUDE[tsql](../../includes/tsql-md.md)]ジョブ ステップ履歴にステップの出力|  
|**8**|テーブルにログを書き込む (既存の履歴を上書きする)|  
|**16**|テーブルにログを書き込む (既存の履歴に追加します)|  
|**32**|すべての出力をジョブ履歴に書き込みます。|  
|**64**|中止する Cmd ジョブ ステップのシグナルとして使用する Windows イベントを作成します。|  
  
`[ @proxy_id = ] proxy_id` ジョブ ステップを実行するプロキシの id 番号。 *proxy_id*型は、 **int**、既定値は NULL です。 いない場合*proxy_id*が指定されていない*proxy_name*が指定されているおよび no *user_name*を指定すると、ジョブ ステップをサービス アカウントとして実行[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェント。  
  
`[ @proxy_name = ] 'proxy_name'` ジョブ ステップを実行するプロキシの名前。 *proxy_name*型は、 **sysname**、既定値は NULL です。 いない場合*proxy_id*が指定されていない*proxy_name*が指定されているおよび no *user_name*を指定すると、ジョブ ステップをサービス アカウントとして実行[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェント。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>コメント  
 **sp_add_jobstep**から実行する必要があります、 **msdb**データベース。  
  
 SQL Server Management Studio は、簡単かつ直観的な方法でジョブを管理するためのツールで、ジョブ体系の作成および管理に最適です。  
  
 ジョブ ステップの作成者がのメンバーでない限り、ジョブ ステップでプロキシを指定する必要があります、 **sysadmin**固定セキュリティ ロール。  
  
 プロキシで識別できます*proxy_name*または*proxy_id*します。  
  
## <a name="permissions"></a>アクセス許可  
 既定では、このストアド プロシージャを実行できるのは、 **sysadmin** 固定サーバー ロールのメンバーです。 他のユーザーには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **データベースの次のいずれかの** エージェント固定データベース ロールが許可されている必要があります。  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 これらのロールの権限の詳細については、「 [SQL Server エージェントの固定データベース ロール](../../ssms/agent/sql-server-agent-fixed-database-roles.md)」を参照してください。  
  
 ジョブ ステップの作成者は、ジョブ ステップのプロキシへのアクセスが必要です。 メンバー、 **sysadmin**固定サーバー ロールは、すべてのプロキシへのアクセス権を持ちます。 他のユーザー必要があります明示的に付与するアクセスをプロキシします。  
  
## <a name="examples"></a>使用例  
 次の例では、データベースへのアクセスを Sales データベースの読み取り専用に変更するジョブ ステップを作成します。 さらに、この例では、各再試行は 5 分待機後に発生する 5 つの再試行回数を指定します。  
  
> [!NOTE]  
>  この例では、`Weekly Sales Data Backup`ジョブが既に存在します。  
  
```sql
USE msdb;  
GO  
EXEC sp_add_jobstep  
    @job_name = N'Weekly Sales Data Backup',  
    @step_name = N'Set database to read only',  
    @subsystem = N'TSQL',  
    @command = N'ALTER DATABASE SALES SET READ_ONLY',
    @retry_attempts = 5,  
    @retry_interval = 5 ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [表示またはジョブの変更](../../ssms/agent/view-or-modify-jobs.md)   
 [sp_add_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-job-transact-sql.md)   
 [sp_add_schedule &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)   
 [sp_delete_jobstep &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql.md)   
 [sp_help_job &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-job-transact-sql.md)   
 [sp_help_jobstep &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-jobstep-transact-sql.md)   
 [sp_update_jobstep &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
