---
title: sp_dbmmonitoraddmonitoring (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_dbmmonitoraddmonitoring
- sp_dbmmonitoraddmonitoring_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- database mirroring [SQL Server], monitoring
- sp_dbmmonitoraddmonitoring
ms.assetid: 9489dc30-af29-4363-a172-4645947fc95e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4ed53c6a72b201129cf9f75214261bbdd47d6fb9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68108153"
---
# <a name="sp_dbmmonitoraddmonitoring-transact-sql"></a>sp_dbmmonitoraddmonitoring (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  サーバーインスタンス上のミラー化されたデータベースごとにミラーリングの状態を定期的に更新する、データベースミラーリングモニターのジョブを作成します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_dbmmonitoraddmonitoring [ update_period ]  
```  
  
## <a name="arguments"></a>引数  
 *update_period*  
 更新間隔を分単位で指定します。 この値は、1 ~ 120 分の間で指定できます。 既定値は1分です。  
  
> [!NOTE]  
>  更新期間が短すぎると、クライアントの応答時間が長くなる可能性があります。  
  
## <a name="return-code-values"></a>リターン コードの値  
 なし  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>解説  
 このプロシージャを実行するには、サーバー インスタンス上で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを実行できることが必要です。また、データベース ミラーリング監視ジョブを実行するにはエージェントが実行中であることが必要です。  
  
 データベースミラーリングがから[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]開始された場合、 **sp_dbmmonitoraddmonitoring**プロシージャは自動的に実行されます。 ALTER DATABASE ステートメントを使用して手動でミラーリングを開始する場合、サーバーインスタンス上のミラー化されたデータベースを監視するには、 **sp_dbmmonitoraddmonitoring**を手動で実行する必要があります。  
  
> [!NOTE]  
>  データベースミラーリングをセットアップする前に**sp_dbmmonitoraddmonitoring**を実行すると、監視ジョブは実行されますが、データベースミラーリングモニターの履歴が保存されている状態テーブルは更新されません。  
  
## <a name="permissions"></a>アクセス許可  
 
  **sysadmin** 固定サーバー ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>例  
 次の例では、更新間隔`3` (分) で監視を開始します。  
  
```  
EXEC sp_dbmmonitoraddmonitoring 3;  
```  
  
## <a name="see-also"></a>参照  
 [データベースミラーリングの監視 &#40;SQL Server&#41;](../../database-engine/database-mirroring/monitoring-database-mirroring-sql-server.md)   
 [sp_dbmmonitorchangemonitoring &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorchangemonitoring-transact-sql.md)   
 [sp_dbmmonitordropmonitoring &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitordropmonitoring-transact-sql.md)   
 [sp_dbmmonitorhelpmonitoring &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorhelpmonitoring-transact-sql.md)   
 [sp_dbmmonitorresults &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorresults-transact-sql.md)  
  
  
