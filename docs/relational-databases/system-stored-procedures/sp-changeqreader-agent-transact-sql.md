---
title: sp_changeqreader_agent (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changeqreader_agent_TSQL
- sp_changeqreader_agent
helpviewer_keywords:
- sp_changeqreader_agent
ms.assetid: d3fe79c5-31ef-4565-bf38-b476b5fb16f7
author: stevestein
ms.author: sstein
ms.openlocfilehash: b636eb929d74aec7b0f3555ce511372f6592c5b0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68099137"
---
# <a name="sp_changeqreader_agent-transact-sql"></a>sp_changeqreader_agent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  キュー リーダー エージェントのセキュリティのプロパティを変更します。 このストアドプロシージャは、ディストリビューター側のディストリビューションデータベース、またはパブリッシャー側のパブリケーションデータベースに対して実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_changeqreader_agent [ [ @job_login = ] 'job_login' ]  
    [ , [ @job_password = ] 'job_password' ]  
    [ , [ @frompublisher = ] frompublisher   
```  
  
## <a name="arguments"></a>引数  
`[ @job_login = ] 'job_login'`エージェントを実行する[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アカウントのログインを指定します。 *job_login*は**nvarchar (257)**,、既定値は NULL です。  
  
`[ @job_password = ] 'job_password'`エージェントを実行する Windows アカウントのパスワードを指定します。 *job_password*は**sysname**,、既定値は NULL です。  
  
`[ @frompublisher = ] frompublisher`プロシージャがパブリッシャーで実行されているかどうかを示します。 *frompublisher*の部分は bit で、既定値は**0**です。 値**1**は、パブリケーションデータベースのパブリッシャーからプロシージャが実行されていることを意味します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_changeqreader_agent**は、トランザクションレプリケーションで使用します。  
  
 **sp_changeqreader_agent**は、キューリーダーエージェントを実行する Windows アカウントを変更するために使用されます。 既存の Windows ログインのパスワードを変更することも、新しい Windows ログインとパスワードを指定することもできます。  
  
 エージェントのログインまたはパスワードを変更した後、変更を有効にするには、エージェントを停止して再起動する必要があります。  
  
## <a name="permissions"></a>アクセス許可  
 **Sp_changeqreader_agent**を実行できるのは、 **sysadmin**固定サーバーロールのメンバーだけです。  
  
## <a name="see-also"></a>参照  
 [レプリケーションのセキュリティ設定を表示および変更する](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)   
 [sp_addqreader_agent &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addqreader-agent-transact-sql.md)  
  
  
