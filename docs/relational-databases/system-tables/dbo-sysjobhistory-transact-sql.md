---
title: dbo. sysjobhistory (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/24/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.sysjobhistory_TSQL
- dbo.sysjobhistory
- sysjobhistory
- sysjobhistory_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysjobhistory system table
ms.assetid: 1b1fcdbb-2af2-45e6-bf3f-e8279432ce13
author: stevestein
ms.author: sstein
ms.openlocfilehash: cc488958513f4a84ac776ff26f1fe2c867f8fa74
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "76761836"
---
# <a name="dbosysjobhistory-transact-sql"></a>dbo. sysjobhistory (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]


  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントで実行予定のジョブに関する情報を格納します。
  
> [!NOTE]
> ほとんどの場合、データは、ジョブステップが完了した後にのみ更新されます。テーブルには、通常、現在進行中のジョブステップのレコードが含まれていませんが、場合によっては、基に*なるプロセスが*進行中のジョブステップに関する情報を提供します。

このテーブルは、 **msdb**データベースに格納されます。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**instance_id**|**int**|行の一意識別子。|  
|**job_id**|**UNIQUEIDENTIFIER**|ジョブ ID。|  
|**step_id**|**int**|ジョブ ステップの ID。|  
|**step_name**|**sysname**|ステップの名前。|  
|**sql_message_id**|**int**|ジョブが失敗[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]した場合に返されるエラーメッセージの ID。|  
|**sql_severity**|**int**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エラーの重大度。|  
|**メッセージ**|**nvarchar(4000)**|
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラーのテキスト (存在する場合)。|  
|**run_status**|**int**|ジョブ実行のステータス。<br /><br /> **0** = 失敗<br /><br /> **1** = 成功<br /><br /> **2** = 再試行<br /><br /> **3** = キャンセル<br /><br />**4** = 実行中|  
|**run_date**|**int**|ジョブまたはステップの実行を開始した日付。 進行中の履歴については、履歴が書き込まれた日付/時刻です。|  
|**run_time**|**int**|ジョブまたはステップが**HHMMSS**形式で開始された時刻。|  
|**run_duration**|**int**|ジョブまたはステップの実行の経過時間 ( **HHMMSS**形式)。|  
|**operator_id_emailed**|**int**|ジョブの完了時に通知されたオペレーターの ID。|  
|**operator_id_netsent**|**int**|ジョブの完了時にメッセージによって通知されたオペレーターの ID。|  
|**operator_id_paged**|**int**|ジョブの終了時にポケットベルの通知を受けるオペレーターの ID。|  
|**retries_attempted**|**int**|ジョブまたはステップの再試行回数。|  
|**server**|**sysname**|ジョブが実行されたサーバーの名前。|  
  
  ## <a name="example"></a>例
 次[!INCLUDE[tsql](../../includes/tsql-md.md)]のクエリでは、 **run_time**と**run_duration**列をユーザーフレンドリな形式に変換します。  で[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]スクリプトを実行します。
 
 ```sql
 SET NOCOUNT ON;
 
 SELECT sj.name,
        sh.run_date,
        sh.step_name,
        STUFF(STUFF(RIGHT(REPLICATE('0', 6) +  CAST(sh.run_time as varchar(6)), 6), 3, 0, ':'), 6, 0, ':') 'run_time',
        STUFF(STUFF(STUFF(RIGHT(REPLICATE('0', 8) + CAST(sh.run_duration as varchar(8)), 8), 3, 0, ':'), 6, 0, ':'), 9, 0, ':') 'run_duration (DD:HH:MM:SS)  '
FROM msdb.dbo.sysjobs sj
JOIN msdb.dbo.sysjobhistory sh
ON sj.job_id = sh.job_id
```
