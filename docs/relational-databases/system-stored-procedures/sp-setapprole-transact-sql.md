---
title: sp_setapprole (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 10/12/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_setapprole
- sp_setapprole_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_setapprole
ms.assetid: cf0901c0-5f90-42d4-9d5b-8772c904062d
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: c18aa6fefb23bb3d388069773aa1633c29859e90
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58533534"
---
# <a name="spsetapprole-transact-sql"></a>sp_setapprole (TRANSACT-SQL)

[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  現在のデータベース内のアプリケーション ロールに関連付けられているアクセス許可をアクティブにします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  

```sql
sp_setapprole [ @rolename = ] 'role',  
    [ @password = ] { encrypt N'password' }
      |  
        'password' [ , [ @encrypt = ] { 'none' | 'odbc' } ]  
        [ , [ @fCreateCookie = ] true | false ]  
    [ , [ @cookie = ] @cookie OUTPUT ]  
```

## <a name="arguments"></a>引数

`[ @rolename = ] 'role'` 現在のデータベースで定義されているアプリケーション ロールの名前です。 *ロール*は**sysname**、既定値はありません。 *ロール*現在のデータベースに存在する必要があります。  
  
`[ @password = ] { encrypt N'password' }` アプリケーション ロールをアクティブ化するために必要なパスワードです。 *パスワード*は**sysname**、既定値はありません。 *パスワード*、ODBC を使用して暗号化できます**暗号化**関数。 使用すると、**暗号化**関数の場合、パスワードは、配置することで Unicode 文字列に変換する必要があります**N**最初の引用符の前にします。  
  
 使用している接続の暗号化オプションはサポートされていません**SqlClient**します。  
  
> [!IMPORTANT]  
> ODBC**暗号化**関数では、暗号化は提供されません。 ネットワーク経由で転送されるパスワードを保護するには、この関数にはしないでください。 この情報は、ネットワークを介して転送は場合、は、SSL または IPSec を使用します。
  
 **@encrypt = 'none'**  
 暗号化を使用しないことを示します。 パスワードはプレーンテキストとして [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に渡されます。 既定値です。  
  
 **@encrypt= 'odbc'**  
 ODBC が ODBC を使用して、パスワードを難読化ことを指定します。**暗号化**関数にパスワードを送信する前に、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]します。 これは、SQL Server 用 ODBC クライアントまたは OLE DB プロバイダーのいずれかを使用する場合にのみ指定できます。  
  
`[ @fCreateCookie = ] true | false` Cookie が作成されるかどうかを指定します。 **true**は 1 に暗黙的に変換します。 **false**は 0 に暗黙的に変換します。  
  
`[ @cookie = ] @cookie OUTPUT` クッキーを含める出力パラメーターを指定します。 場合にのみ、クッキーが生成される値の**@fCreateCookie**は**true**します。 **varbinary(8000)**  
  
> [!NOTE]  
> **sp_setapprole** のクッキーの **OUTPUT** パラメーターは現在、適切な最大長である **varbinary(8000)** としてドキュメントに記載されています。 ただし、現在の実装では **varbinary(50)** を返します。 アプリケーションが引き続き予約**varbinary (8000)** サイズの増加、将来のリリースでクッキーの戻り値が正しく動作するアプリケーションが引き続き行われるようにします。
  
## <a name="return-code-values"></a>リターン コードの値

 0 (成功) と 1 (失敗)  
  
## <a name="remarks"></a>コメント

 使用して、アプリケーション後ロールをアクティブ化**sp_setapprole**、ユーザーがサーバーから切断またはを実行するまで、ロールがアクティブなまま**sp_unsetapprole**します。 **sp_setapprole**直接でのみ実行できます[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメント。 **sp_setapprole**またはユーザー定義のトランザクション内で別のストアド プロシージャ内で実行することはできません。  
  
 アプリケーション ロールの概要については、次を参照してください。[アプリケーション ロール](../../relational-databases/security/authentication-access/application-roles.md)します。  
  
> [!IMPORTANT]  
> ネットワーク経由で送信されるアプリケーション ロールのパスワード保護のため、アプリケーション ロールを有効にする場合に、暗号化された接続を常に使用する必要があります。
> [!INCLUDE[msCoName](../../includes/msconame-md.md)] ODBC**暗号化**では、オプションはサポートされていない**SqlClient**します。 資格情報を格納する必要がある場合は、Crypto API 関数を使用して暗号化します。 パラメーター*パスワード*一方向のハッシュとして格納されます。 旧バージョンとの互換性を維持する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、パスワードの複雑性ポリシーは適用されません**sp_addapprole**します。 パスワードの複雑性ポリシーを適用するには使用[CREATE APPLICATION ROLE](../../t-sql/statements/create-application-role-transact-sql.md)します。  
  
## <a name="permissions"></a>アクセス許可

メンバーシップが必要**パブリック**とロールのパスワードの知識。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-activating-an-application-role-without-the-encrypt-option"></a>A. 暗号化オプションを指定せず、アプリケーション ロールをアクティブ化します。

 次の例では、アプリケーション ロール `SalesAppRole` をアクティブにします。このロールには、プレーンテキストのパスワード `AsDeF00MbXX` が設定されており、現在のユーザーが使用するアプリケーション用に特別に設計された権限が与えられています。

```sql
EXEC sys.sp_setapprole 'SalesApprole', 'AsDeF00MbXX';  
GO
```

### <a name="b-activating-an-application-role-with-a-cookie-and-then-reverting-to-the-original-context"></a>B. クッキーを使用するアプリケーション ロールをアクティブ化して、元のコンテキストに戻す

 次の例では、パスワード `Sales11` が設定されているアプリケーション ロール `fdsd896#gfdbfdkjgh700mM` をアクティブ化し、クッキーを作成します。 この例では、現在のユーザーの名前が返されます。その後、`sp_unsetapprole` を実行して元のコンテキストに戻します。  

```sql
DECLARE @cookie varbinary(8000);  
EXEC sys.sp_setapprole 'Sales11', 'fdsd896#gfdbfdkjgh700mM'  
    , @fCreateCookie = true, @cookie = @cookie OUTPUT;  
-- The application role is now active.  
SELECT USER_NAME();  
-- This will return the name of the application role, Sales11.  
EXEC sys.sp_unsetapprole @cookie;  
-- The application role is no longer active.  
-- The original context has now been restored.  
GO  
SELECT USER_NAME();  
-- This will return the name of the original user.
GO
```

## <a name="see-also"></a>参照

 [システム ストアド プロシージャ&#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md) [セキュリティ ストアド プロシージャ&#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md) [CREATE APPLICATION ROLE &#40;TRANSACT-SQL&#41; ](../../t-sql/statements/create-application-role-transact-sql.md)[DROP APPLICATION ROLE &#40;TRANSACT-SQL&#41; ](../../t-sql/statements/drop-application-role-transact-sql.md) [sp_unsetapprole &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-unsetapprole-transact-sql.md)
