---
title: dbo.sysproxylogin (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.sysproxylogin_TSQL
- sysproxylogin_TSQL
- dbo.sysproxylogin
- sysproxylogin
dev_langs:
- TSQL
helpviewer_keywords:
- sysproxylogin system table
ms.assetid: 433d33cb-bdf2-47bb-af78-2a40b7c8dfce
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 00a3b3b53bcede7f43aad556465358b957331f45
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62470694"
---
# <a name="dbosysproxylogin-transact-sql"></a>dbo.sysproxylogin (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  各 SQL Server エージェント プロキシ アカウントに関連付けられている、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のログインを記録します。 このテーブルに格納されます、 **msdb**データベース。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**proxy_id**|**int**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント プロキシ アカウントの ID。 この値に対応、 **proxy_id**内の列、 **sysproxies**テーブル。|  
|**sid**|**varbinary(85)**|Microsoft Windows *security_identifier*の SQL Server ログインします。|  
|**principal_id**|**int**|ユーザーまたは指定したサブシステム ステップのプロキシ アカウントを使用する権限を持つグループの ID。|  
|**flags**|**int**|ログインの種類:<br /><br /> **0** = Windows ユーザーまたはグループ、および[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインします。<br /><br /> **1**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]固定システム ロール<br /><br /> **2** = **msdb**データベース ロール|  
  
## <a name="remarks"></a>コメント  
 メンバーのみ、 **sysadmin**固定サーバー ロールがこのテーブルにアクセスできます。  
  
## <a name="see-also"></a>参照  
 [dbo.sysproxies &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/dbo-sysproxies-transact-sql.md)  
  
  
