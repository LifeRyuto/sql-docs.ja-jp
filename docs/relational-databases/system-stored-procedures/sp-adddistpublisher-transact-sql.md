---
title: sp_adddistpublisher (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/15/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_adddistpublisher
- sp_adddistpublisher_TSQL
helpviewer_keywords:
- sp_adddistpublisher
ms.assetid: 04e15011-a902-4074-b38c-3ec2fc73b838
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b7f55d89054ff7d950921e0c6762770c6e714500
ms.sourcegitcommit: aeb2273d779930e76b3e907ec03397eab0866494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67716748"
---
# <a name="spadddistpublisher-transact-sql"></a>sp_adddistpublisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  指定されたディストリビューション データベースを使用するように、パブリッシャーを構成します。 このストアド プロシージャは、ディストリビューターのすべてのデータベースで実行されます。 なお、ストアド プロシージャ[sp_adddistributor &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-adddistributor-transact-sql.md)と[sp_adddistributiondb &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-adddistributiondb-transact-sql.md)このストアド プロシージャを使用する前に実行されている必要がありますプロシージャです。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_adddistpublisher [ @publisher= ] 'publisher'   
        , [ @distribution_db= ] 'distribution_db'   
    [ , [ @security_mode= ] security_mode ]   
    [ , [ @login= ] 'login' ]   
    [ , [ @password= ] 'password' ]   
    [ , [ @working_directory= ] 'working_directory' ]   
    [ , [ @storage_connection_string= ] 'storage_connection_string']
    [ , [ @trusted= ] 'trusted' ]   
    [ , [ @encrypted_password= ] encrypted_password ]   
    [ , [ @thirdparty_flag = ] thirdparty_flag ]  
    [ , [ @publisher_type = ] 'publisher_type' ]  
```  
  
## <a name="arguments"></a>引数  
`[ @publisher = ] 'publisher'` パブリッシャーの名前です。 *パブリッシャー* は **sysname** 、既定値はありません。  
  
`[ @distribution_db = ] 'distribution_db'` ディストリビューション データベースの名前です。 *distributor_db*は**sysname**、既定値はありません。 このパラメーターは、パブリッシャーに接続するレプリケーション エージェントが使用されます。  
  
`[ @security_mode = ] security_mode` 実装されているセキュリティ モードです。 このパラメーターは、キュー更新サブスクリプションまたは以外のパブリッシャーに接続するレプリケーション エージェントのみ使用が[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。 *security_mode*は**int**、これらの値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**0**|ディストリビューターの使用時のレプリケーション エージェント[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーへの接続を認証します。|  
|**1** (既定値)|ディストリビューター側のレプリケーション エージェントは Windows 認証を使用してパブリッシャーに接続します。|  
  
`[ @login = ] 'login'` ログインです。 このパラメーターは必要な場合*security_mode*は**0**します。 *login* のデータ型は **sysname** で、既定値は NULL です。 このパラメーターは、パブリッシャーに接続するレプリケーション エージェントが使用されます。  
  
`[ @password = ] 'password']` パスワードです。 *パスワード*は**sysname**、既定値は NULL です。 このパラメーターは、パブリッシャーに接続するレプリケーション エージェントが使用されます。  
  
> [!IMPORTANT]  
>  空白のパスワードは使用しないでください。 強力なパスワードを使用してください。  
  
`[ @working_directory = ] 'working_directory'` パブリケーションのデータとスキーマ ファイルを格納するために使用する作業ディレクトリの名前です。 *working_directory*は**nvarchar (255)** 、および既定値は ReplData フォルダーのこのインスタンスの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、たとえば`C:\Program Files\Microsoft SQL Server\MSSQL\MSSQ.1\ReplData`します。 名前は UNC 形式で指定する必要があります。  

 Azure SQL Database では、使用`\\<storage_account>.file.core.windows.net\<share>`します。

`[ @storage_connection_string = ] 'storage_connection_string'` SQL データベースに必要です。 Azure Portal からストレージ アクセス キーを使用 > 設定します。

 > [!INCLUDE[Azure SQL Database link](../../includes/azure-sql-db-repl-for-more-information.md)]

`[ @trusted = ] 'trusted'` このパラメーターは非推奨とされましたが、旧バージョンとの互換性を保つのために提供されます。 *信頼された*は**nvarchar (5)** 、以外に設定して**false**エラーが発生します。  
  
`[ @encrypted_password = ] encrypted_password` 設定*encrypted_password*現在サポートされていません。 これを設定しようとしています。**ビット**パラメーターを**1** 、エラーが発生します。  
  
`[ @thirdparty_flag = ] thirdparty_flag` パブリッシャーの場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 *thirdparty_flag*は**ビット**値は次のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**0** (既定値)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース。|  
|**1**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外のデータベース|  
  
`[ @publisher_type = ] 'publisher_type'` パブリッシャーでないときに、パブリッシャーの種類を指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 *publisher_type*が sysname で、次の値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**MSSQLSERVER**<br /><br /> (既定値)。|指定します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。|  
|**ORACLE**|標準の Oracle パブリッシャーを指定します。|  
|**ORACLE GATEWAY**|Oracle ゲートウェイ パブリッシャーを指定します。|  
  
 Oracle パブリッシャーと Oracle ゲートウェイ パブリッシャーとの違いの詳細については、次を参照してください。 [Oracle パブリッシャーの構成](../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_adddistpublisher**スナップショット レプリケーション、トランザクション レプリケーション、およびマージ レプリケーションで使用されます。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#AddDistPub](../../relational-databases/replication/codesnippet/tsql/sp-adddistpublisher-tran_1.sql)]  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールが実行できる**sp_adddistpublisher**します。  
  
## <a name="see-also"></a>参照  
 [パブリッシングとディストリビューションの構成](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [sp_changedistpublisher (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql.md)   
 [sp_dropdistpublisher &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql.md)   
 [sp_helpdistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdistpublisher-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [[ディストリビューションの構成]](../../relational-databases/replication/configure-distribution.md)  
  
  
