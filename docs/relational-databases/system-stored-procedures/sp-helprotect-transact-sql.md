---
title: sp_helprotect (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helprotect
- sp_helprotect_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helprotect
ms.assetid: faaa3e40-1c95-43c2-9fdc-c61a1d3cc0c3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7db43df5d500e56e58e3e8465ac03158fe7e4d21
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67997473"
---
# <a name="sp_helprotect-transact-sql"></a>sp_helprotect (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在のデータベース内のオブジェクトまたはステートメント権限に対するユーザー権限に関する情報を含むレポートを返します。  
  
> [!IMPORTANT]  
>  **sp_helprotect**は、で導入された securables に関する[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]情報を返しません。 代わりに、 [database_permissions](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md)を使用し、 [fn_builtin_permissions](../../relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql.md)してください。  
  
 固定サーバー ロールまたは固定データベース ロールに常に割り当てられる権限は表示されません。 には、ロールのメンバーシップに基づいて権限を受け取るログインやユーザーは含まれません。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helprotect [ [ @name = ] 'object_statement' ]   
     [ , [ @username = ] 'security_account' ]   
     [ , [ @grantorname = ] 'grantor' ]   
     [ , [ @permissionarea = ] 'type' ]  
```  
  
## <a name="arguments"></a>引数  
`[ @name = ] 'object_statement'`現在のデータベース内のオブジェクトの名前、またはレポートする権限を持つステートメントを指定します。 *object_statement*は**nvarchar (776)**,、既定値は NULL の場合、すべてのオブジェクトとステートメントの権限が返されます。 値がオブジェクト (テーブル、ビュー、ストアドプロシージャ、または拡張ストアドプロシージャ) の場合は、現在のデータベース内の有効なオブジェクトである必要があります。 オブジェクト名には、所有者の修飾子をフォームの_所有者_として含めることができ**ます。**_オブジェクト_。  
  
 *Object_statement*がステートメントである場合は、CREATE ステートメントを指定できます。  
  
`[ @username = ] 'security_account'`権限が返されるプリンシパルの名前を指定します。 *security_account*のデータ型は**sysname**で、既定値は NULL です。 NULL の場合は、現在のデータベース内のすべてのプリンシパルが返されます。 *security_account*は、現在のデータベースに存在している必要があります。  
  
`[ @grantorname = ] 'grantor'`権限を許可したプリンシパルの名前を指定します。 権限の許可者のデータ型は**sysname**で、既定値は NULL です。 NULL の場合は、データベース内のプリンシパルによって付与された権限のすべての情報が*返されます*。  
  
`[ @permissionarea = ] 'type'`オブジェクト権限 (文字列**o**)、ステートメント権限 (文字列**s**)、またはその両方 (**os**) を表示するかどうかを示す文字列を指定します。 *種類*は**varchar (10)**,、既定値は**os**です。 *type*は、 **o**と**s**の任意の組み合わせにすることができます。また、または、 **o**と**s**の間にコンマまたはスペースを入れません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**[所有者]**|**sysname**|オブジェクト所有者の名前。|  
|**Object**|**sysname**|オブジェクトの名前。|  
|**権限**|**sysname**|権限が許可されたプリンシパルの名前。|  
|**Grantor**|**sysname**|指定された権限付与対象ユーザーに権限を許可したプリンシパルの名前。|  
|**ProtectType**|**nvarchar (10)**|保護の種類の名前:<br /><br /> 取り消しの許可|  
|**アクション**|**nvarchar (60)**|アクセス許可の名前。 有効な権限ステートメントは、オブジェクトの種類によって異なります。|  
|**列**|**sysname**|アクセス許可の種類:<br /><br /> All = オブジェクトの現在の列すべてに対する権限<br /><br /> 新規 = アクセス許可は、後でオブジェクトに対して変更される可能性のある新しい列 (ALTER ステートメントを使用) を対象とします。<br /><br /> All+New = All と New を組み合わせた権限<br /><br /> 権限の種類が列に適用されない場合は、ピリオドを返します。|  
  
## <a name="remarks"></a>解説  
 次のプロシージャでは、すべてのパラメーターが省略可能です。 パラメーターを使用せずに`sp_helprotect`実行すると、現在のデータベースで許可または拒否されたすべての権限が表示されます。  
  
 すべてではなく一部のパラメーターだけを指定する場合は、特定のパラメーターを示す名前付きのパラメーターを使用するか、プレースホルダーとして `NULL` を使用します。 たとえば、データベース所有者 (`dbo`) のすべてのアクセス許可を報告するには、次のように実行します。  
  
```  
EXEC sp_helprotect NULL, NULL, dbo;  
```  
  
 または  
  
```  
EXEC sp_helprotect @grantorname = 'dbo';  
```  
  
 出力レポートは、権限カテゴリ、所有者、オブジェクト、権限付与対象ユーザー、許可者、保護の種類のカテゴリ、保護の種類、アクション、列のシーケンシャル ID によって並べ替えられます。  
  
## <a name="permissions"></a>アクセス許可  
 **Public**ロールのメンバーシップが必要です。  
  
 返される情報には、メタデータへのアクセスに関する制限が適用されます。 プリンシパルに権限がないエンティティは表示されません。 詳細については、「[メタデータ表示の構成](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="examples"></a>例  
  
### <a name="a-listing-the-permissions-for-a-table"></a>A. テーブルの権限の一覧表示  
 次の例では、テーブル `titles` の権限に関するレポートを一覧表示します。  
  
```  
EXEC sp_helprotect 'titles';  
```  
  
### <a name="b-listing-the-permissions-for-a-user"></a>B. ユーザーに対する権限を一覧表示する  
 次の例では、ユーザー `Judy`が現在のデータベースに保持しているすべてのアクセス許可を一覧表示します。  
  
```  
EXEC sp_helprotect NULL, 'Judy';  
```  
  
### <a name="c-listing-the-permissions-granted-by-a-specific-user"></a>C. 特定のユーザーによって付与されたアクセス許可を一覧表示する  
 次の例では、現在のデータベース内でユーザー `Judy` に許可されたすべての権限を一覧表示します。指定しないパラメーターについては、プレースホルダーとして `NULL` を使用します。  
  
```  
EXEC sp_helprotect NULL, NULL, 'Judy';  
```  
  
### <a name="d-listing-the-statement-permissions-only"></a>D. ステートメント権限のみを一覧表示する  
 次の例では、現在のデータベース内のすべてのステートメント権限を表示します。指定しないパラメーターについては、プレースホルダーとして `NULL` を使用します。  
  
```  
EXEC sp_helprotect NULL, NULL, NULL, 's';   
```  
  
### <a name="e-listing-the-permissions-for-a-create-statement"></a>e. CREATE ステートメントの権限だけを一覧表示する  
 次の例では、CREATE TABLE アクセス許可が付与されているすべてのユーザーを一覧表示します。  
  
```  
EXEC sp_helprotect @name = 'CREATE TABLE';  
```  
  
## <a name="see-also"></a>参照  
 [セキュリティストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [Transact-sql&#41;の拒否 &#40;](../../t-sql/statements/deny-transact-sql.md)   
 [GRANT &#40;Transact-sql&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [&#40;Transact-sql&#41;を取り消す](../../t-sql/statements/revoke-transact-sql.md)   
 [システムストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
