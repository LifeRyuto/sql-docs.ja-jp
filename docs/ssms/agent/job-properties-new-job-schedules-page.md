---
title: ジョブのプロパティ - [新しいジョブ] ([スケジュール] ページ) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.job.schedules.f1
ms.assetid: 0b03585b-a510-484d-8a63-9b32459def9c
author: markingmyname
ms.author: maghan
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: b0444310b6c0d226fefe093c281cf9e96c2ca0c4
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/06/2019
ms.locfileid: "65095815"
---
# <a name="job-properties---new-job-schedules-page"></a>ジョブのプロパティ - [新しいジョブ] ([スケジュール] ページ)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) では現在、すべてではありませんがほとんどの SQL Server エージェントの機能がサポートされています。 詳細については、「[Azure SQL Database Managed Instance と SQL Server の T-SQL の相違点](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)」を参照してください。

このページを使用すると、 [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエージェント ジョブのスケジュールを表示したり、調整したりできます。  
  
## <a name="options"></a>オプション  
**[スケジュールの一覧]**  
このジョブのスケジュールの一覧を表示します。  
  
**[新規作成]**  
新しいスケジュールを作成します。 スケジュールを作成すると、そのスケジュールはジョブに追加されます。  
  
**[選択]**  
既存のスケジュールを選択します。 ジョブとスケジュールの所有者は同じである必要があるため、このオプションを使用しても自分が所有するスケジュールしか選択できません。  
  
**[編集]**  
選択したスケジュールを編集し、ジョブのスケジュールのプロパティを変更します。  
  
**[削除]**  
選択されているスケジュールをジョブから削除します。 このスケジュールを使用するジョブが他にない場合、スケジュールはデータベースから削除されます。  
  
## <a name="see-also"></a>参照  
[ジョブの実装](../../ssms/agent/implement-jobs.md)  
  
