---
title: sp_update_jobschedule (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_update_jobschedule_TSQL
- sp_update_jobschedule
dev_langs:
- TSQL
helpviewer_keywords:
- sp_update_jobschedule
ms.assetid: 4df02594-4cd1-49a9-8d97-37c44e4d5423
author: stevestein
ms.author: sstein
ms.openlocfilehash: ebdaa23db8602b608498b4012ffd71367bb99a0b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68084900"
---
# <a name="sp_update_jobschedule-transact-sql"></a>sp_update_jobschedule (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定したジョブのスケジュール設定を変更します。  
  
 **sp_update_jobschedule**は、旧バージョンとの互換性のためだけに用意されています。  
  
> [!IMPORTANT]
>  以前のバージョンの Microsoft SQL Server で使用されている構文の詳細については、Microsoft SQL Server 2000 の『 Transact-sql Referencefor を参照してください *。*  
  
## <a name="remarks"></a>解説  
 ジョブスケジュールをジョブとは別に管理できるようになりました。 スケジュールを更新するには、 **sp_update_schedule**を使用します。  
  
## <a name="permissions"></a>アクセス許可  
 既定では、 **sysadmin**固定サーバーロールのメンバーは、このストアドプロシージャを実行できます。 他のユーザーには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **データベースの次のいずれかの** エージェント固定データベース ロールが許可されている必要があります。  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 これらのロールの権限の詳細については、「 [SQL Server エージェントの固定データベース ロール](../../ssms/agent/sql-server-agent-fixed-database-roles.md)」を参照してください。  
  
 このストアドプロシージャを使用して、他のユーザーが所有するジョブスケジュールを更新できるのは、 **sysadmin**のメンバーだけです。  
  
## <a name="see-also"></a>参照  
 [Transact-sql&#41;&#40;のストアドプロシージャの SQL Server エージェント](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [sp_update_schedule &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-update-schedule-transact-sql.md)  
  
  
