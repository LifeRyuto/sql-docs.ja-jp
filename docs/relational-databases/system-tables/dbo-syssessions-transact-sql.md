---
title: dbo.syssessions (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.syssessions_TSQL
- dbo.syssessions
- syssessions_TSQL
- syssessions
dev_langs:
- TSQL
helpviewer_keywords:
- syssessions system table
ms.assetid: 187819b6-c7f4-4a26-b74c-0a89e96695cf
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2ad2ccc2505c3bb72b8d2efc02afbc5ef5aebaf0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62470561"
---
# <a name="dbosyssessions-transact-sql"></a>dbo.syssessions (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  毎回[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェントの起動、新しいセッションを作成します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスが予期せず再開または停止すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントではジョブの状態を保持するためセッションが使用されます。 行ごと、 **syssessions**テーブルに 1 つのセッションの情報が含まれています。 使用して、 **sysjobactivity**セッションごとの最後に、ジョブの状態を表示するテーブル。  
  
 このテーブルに格納されます、 **msdb**データベース。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**session_id**|**int**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント セッションの ID。|  
|**agent_start_date**|**datetime**|セッションに対して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスが開始された日時。|  
  
## <a name="remarks"></a>コメント  
 メンバーであるユーザーのみの**sysadmin**固定サーバー ロールがこのテーブルにアクセスできます。  
  
## <a name="see-also"></a>参照  
 [dbo.sysjobactivity &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/dbo-sysjobactivity-transact-sql.md)  
  
  
