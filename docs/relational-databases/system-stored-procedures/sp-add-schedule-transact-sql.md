---
title: sp_add_schedule (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_schedule_TSQL
- sp_add_schedule
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_schedule
ms.assetid: 9060aae3-3ddd-40a5-83bb-3ea7ab1ffbd7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 438fe71bcc32c63f97aea95c7105399c2ff8a479
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68088503"
---
# <a name="spaddschedule-transact-sql"></a>sp_add_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  任意の数のジョブで使用できるスケジュールを作成します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_add_schedule [ @schedule_name = ] 'schedule_name'   
    [ , [ @enabled = ] enabled ]  
    [ , [ @freq_type = ] freq_type ]  
    [ , [ @freq_interval = ] freq_interval ]   
    [ , [ @freq_subday_type = ] freq_subday_type ]   
    [ , [ @freq_subday_interval = ] freq_subday_interval ]   
    [ , [ @freq_relative_interval = ] freq_relative_interval ]   
    [ , [ @freq_recurrence_factor = ] freq_recurrence_factor ]   
    [ , [ @active_start_date = ] active_start_date ]   
    [ , [ @active_end_date = ] active_end_date ]   
    [ , [ @active_start_time = ] active_start_time ]   
    [ , [ @active_end_time = ] active_end_time ]   
    [ , [ @owner_login_name = ] 'owner_login_name' ]  
    [ , [ @schedule_uid = ] schedule_uid OUTPUT ]  
    [ , [ @schedule_id = ] schedule_id OUTPUT ]  
    [ , [ @originating_server = ] server_name ] /* internal */  
```  
  
## <a name="arguments"></a>引数  
`[ @schedule_name = ] 'schedule_name'` スケジュールの名前。 *schedule_name*は**sysname**、既定値はありません。  
  
`[ @enabled = ] enabled` スケジュールの現在の状態を示します。 *有効になっている*は**tinyint**、既定値は**1** (有効)。 場合**0**スケジュールが有効になっていません。 スケジュールが有効でない場合、このスケジュールでジョブは実行されません。  
  
`[ @freq_type = ] freq_type` ジョブの場合は、実行することを示す値。 *freq_type*は**int**、既定値は**0**、これらの値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**1**|1 回。|  
|**4**|毎日。|  
|**8**|毎週。|  
|**16**|毎月。|  
|**32**|毎月、に対して相対的な*freq_interval*|  
|**64**|SQLServerAgent サービスの起動時に実行します。|  
|**128**|コンピューターがアイドル状態のときに実行します。|  
  
`[ @freq_interval = ] freq_interval` ジョブを実行する日です。 *freq_interval*は**int**、既定値は**1**の値に依存して*freq_type*します。  
  
|値*freq_type*|影響を与える*freq_interval*|  
|---------------------------|--------------------------------|  
|**1** (1 回)|*freq_interval*は使用されません。|  
|**4** (毎日)|すべて*freq_interval*日。|  
|**8** (毎週)|*freq_interval* (OR 論理演算子で結合)、次の 1 つ以上には。<br /><br /> **1**日曜日を =<br /><br /> **2** = 月曜日<br /><br /> **4** = 火曜日<br /><br /> **8** = 水曜日<br /><br /> **16** = 木曜日<br /><br /> **32** = 金曜日<br /><br /> **64** = 土曜日|  
|**16** (毎月)|*Freq_interval*します月の日。|  
|**32** (月単位)|*freq_interval*は、次の 1 つです。<br /><br /> **1**日曜日を =<br /><br /> **2** = 月曜日<br /><br /> **3** = 火曜日<br /><br /> **4** = 水曜日<br /><br /> **5** = 木曜日<br /><br /> **6** = 金曜日<br /><br /> **7** = 土曜日<br /><br /> **8** = 日<br /><br /> **9** = 平日<br /><br /> **10** = 土日|  
|**64** (SQLServerAgent サービスの開始時)|*freq_interval*は使用されません。|  
|**128**|*freq_interval*は使用されません。|  
  
`[ @freq_subday_type = ] freq_subday_type` 単位を指定します*freq_subday_interval*します。 *freq_subday_type*は**int**、既定値は**0**、これらの値のいずれかを指定できます。  
  
|値|説明 (単位)|  
|-----------|--------------------------|  
|**0x1**|指定された時刻|  
|**0x2**|Seconds|  
|**0x4**|Minutes|  
|**0x8**|Hours|  
  
`[ @freq_subday_interval = ] freq_subday_interval` 数*freq_subday_type*にジョブの各実行間に発生する期間。 *freq_subday_interval*は**int**、既定値は**0**します。 注:間隔は、10 秒より長くする必要があります。 *freq_subday_interval*そのような場合は無視されます、 *freq_subday_type*と等しい**1**します。  
  
`[ @freq_relative_interval = ] freq_relative_interval` ジョブの発生*freq_interval* 、各月場合*freq_interval* 32 (月単位)。 *freq_relative_interval*は**int**、既定値は**0**、これらの値のいずれかを指定できます。 *freq_relative_interval*そのような場合は無視されます、 *freq_type*が 32 と等しくありません。  
  
|値|説明 (単位)|  
|-----------|--------------------------|  
|**1**|First|  
|**2**|第 2 週|  
|**4**|サードパーティ|  
|**8**|4 番目|  
|**16**|Last|  
  
`[ @freq_recurrence_factor = ] freq_recurrence_factor` 週間隔または月間隔は、ジョブのスケジュールされた実行の数。 *freq_recurrence_factor*場合にのみ使用が*freq_type*は**8**、 **16**、または**32**します。 *freq_recurrence_factor*は**int**、既定値は**0**します。  
  
`[ @active_start_date = ] active_start_date` ジョブの実行が開始できる日付。 *active_start_date*は**int**の既定値は NULL には、今日の日付を示します。 日付は yyyymmdd です。 場合*active_start_date*が NULL でない日付は 19900101 以上する必要があります。  
  
 スケジュールを作成した後は、開始日を確認し、正しい日付であることを確認します。 詳細については、「開始日のスケジュール設定」セクションを参照してください[の作成とジョブ スケジュールをアタッチ](../../ssms/agent/create-and-attach-schedules-to-jobs.md)します。  
  
 毎週または月単位のスケジュールでは、エージェントは、active_start_date が過去、し、代わりに、現在の日付を使用する場合は無視されます。 SQL エージェントのスケジュールが sp_add_schedule を使用して作成されたときにジョブの実行を開始する日付が active_start_date パラメーターを指定するオプションがあります。 スケジュールの種類が毎週または毎月、active_start_date パラメーターは、過去の日付に設定されて、active_start_date パラメーターは無視され、現在の日付が active_start_date に使用します。  
  
`[ @active_end_date = ] active_end_date` ジョブの実行が停止できる日付。 *active_end_date*は**int**、既定値は**99991231**、示す年 12 月 31 日 9999 です。 Yyyymmdd 形式で指定として書式設定します。  
  
`[ @active_start_time = ] active_start_time` 間の日で時間*active_start_date*と*active_end_date*ジョブの実行を開始します。 *active_start_time*は**int**、既定値は**000000**12時 00分: 00 AM を示します を 24 時間形式で表したものです。HHMMSS 形式で入力する必要があります。  
  
`[ @active_end_time = ] active_end_time` 間の日で時間*active_start_date*と*active_end_date*ジョブの実行を終了します。 *active_end_time*は**int**、既定値は**235959**、午後 11時 59分: 59 を示します を 24 時間形式で表したものです。HHMMSS 形式で入力する必要があります。  
  
`[ @owner_login_name = ] 'owner_login_name'` スケジュールを所有するサーバー プリンシパルの名前。 *owner_login_name*は**sysname**で、既定値は NULL には、スケジュールが作成者によって所有されていることを示します。  
  
`[ @schedule_uid = ] _schedule_uidOUTPUT` スケジュールの一意の識別子。 *schedule_uid*型の変数は、 **uniqueidentifier**します。  
  
`[ @schedule_id = ] _schedule_idOUTPUT` スケジュールの識別子。 *schedule_id*型の変数は、 **int**します。  
  
`[ @originating_server = ] server_name` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>コメント  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] は、ジョブを簡単に管理できるグラフィカルなツールです。ジョブのインフラストラクチャを作成し、管理するには、このツールを使用することをお勧めします。  
  
## <a name="permissions"></a>アクセス許可  
 既定では、このストアド プロシージャを実行できるのは、 **sysadmin** 固定サーバー ロールのメンバーです。 他のユーザーには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **データベースの次のいずれかの** エージェント固定データベース ロールが許可されている必要があります。  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 これらのロールの権限の詳細については、「 [SQL Server エージェントの固定データベース ロール](../../ssms/agent/sql-server-agent-fixed-database-roles.md)」を参照してください。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-creating-a-schedule"></a>A. スケジュールを作成します。  
 次の例は、名前付きのスケジュールを作成`RunOnce`です。 スケジュールは 1 回のみ、スケジュールが作成された日の `23:30` に実行されます。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_schedule  
    @schedule_name = N'RunOnce',  
    @freq_type = 1,  
    @active_start_time = 233000 ;  
  
GO  
```  
  
### <a name="b-creating-a-schedule-attaching-the-schedule-to-multiple-jobs"></a>B. 複数のジョブにスケジュールをアタッチし、スケジュールを作成します。  
 次の例は、名前付きのスケジュールを作成`NightlyJobs`です。 このスケジュールを使用するジョブは、毎日、サーバーの時間が `01:00` になると実行されます。 例では、ジョブにスケジュールをアタッチする`BackupDatabase`とジョブ`RunReports`します。  
  
> [!NOTE]  
>  この例では、ジョブ`BackupDatabase`とジョブ`RunReports`既に存在します。  
  
```  
USE msdb ;  
GO  
  
EXEC sp_add_schedule  
    @schedule_name = N'NightlyJobs' ,  
    @freq_type = 4,  
    @freq_interval = 1,  
    @active_start_time = 010000 ;  
GO  
  
EXEC sp_attach_schedule  
   @job_name = N'BackupDatabase',  
   @schedule_name = N'NightlyJobs' ;  
GO  
  
EXEC sp_attach_schedule  
   @job_name = N'RunReports',  
   @schedule_name = N'NightlyJobs' ;  
GO  
```  
  
## <a name="see-also"></a>関連項目  
 [作成し、スケジュールをジョブにアタッチ](../../ssms/agent/create-and-attach-schedules-to-jobs.md)   
 [ジョブのスケジュール](../../ssms/agent/schedule-a-job.md)   
 [スケジュールを作成します。](../../ssms/agent/create-a-schedule.md)   
 [SQL Server エージェント ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [sp_add_jobschedule &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-jobschedule-transact-sql.md)   
 [sp_update_schedule &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-schedule-transact-sql.md)   
 [sp_delete_schedule &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-schedule-transact-sql.md)   
 [sp_help_schedule &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-schedule-transact-sql.md)   
 [sp_attach_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql.md)  
  
  
