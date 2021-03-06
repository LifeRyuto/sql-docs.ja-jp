---
title: sysmail_update_principalprofile_sp (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_update_principalprofile_sp
- sysmail_update_principalprofile_sp_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_update_principalprofile_sp
ms.assetid: 9fe96e9a-4758-4e4a-baee-3e1217c4426c
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: dd9644253302c6a577c6cc3923bb3a9e3a0d8c0e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68037380"
---
# <a name="sysmail_update_principalprofile_sp-transact-sql"></a>sysmail_update_principalprofile_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  プリンシパルとプロファイルの関連付けに関する情報を更新します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sysmail_update_principalprofile_sp { @principal_id = principal_id | @principal_name = 'principal_name' } ,  
    { [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' } ,  
    [ @is_default = ] 'is_default'  
```  
  
## <a name="arguments"></a>引数  
`[ @principal_id = ] principal_id`関連付けを変更する**msdb**データベースのデータベースユーザーまたはロールの ID。 *principal_id*は**int**,、既定値は NULL です。 *Principal_id*または*principal_name*のいずれかを指定する必要があります。  
  
`[ @principal_name = ] 'principal_name'`関連付けを更新する**msdb**データベースのデータベースユーザーまたはロールの名前。 *principal_name*は**sysname**,、既定値は NULL です。 *Principal_id*または*principal_name*のいずれかを指定できます。  
  
`[ @profile_id = ] profile_id`関連付けを変更するプロファイルの id。 *profile_id*は**int**,、既定値は NULL です。 *Profile_id*または*profile_name*のいずれかを指定する必要があります。  
  
`[ @profile_name = ] 'profile_name'`関連付けを変更するプロファイルの名前。 *profile_name*は**sysname**,、既定値は NULL です。 *Profile_id*または*profile_name*のいずれかを指定する必要があります。  
  
`[ @is_default = ] 'is_default'`このプロファイルが、データベースユーザーの既定のプロファイルかどうかを指定します。 データベースユーザーは、既定のプロファイルを1つだけ持つことができます。 *is_default*は**ビット**,、既定値はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>解説  
 このストアド プロシージャでは、指定したプロファイルを、データベース ユーザーの既定のプロファイルにするかどうかを変更します。 データベース ユーザーが持つことのできる既定のプライベート プロファイルは 1 つだけです。  
  
 アソシエーションのプリンシパル名が**public**の場合、またはアソシエーションのプリンシパル id が**0**の場合、このストアドプロシージャはパブリックプロファイルを変更します。 既定のパブリック プロファイルは 1 つしか存在できません。  
  
 ** \@Is_default**が '**1**' で、プリンシパルが複数のプロファイルに関連付けられている場合、指定されたプロファイルはプリンシパルの既定のプロファイルになります。 以前既定のプロファイルであったプロファイルは引き続きプリンシパルに関連付けられていますが、既定のプロファイルではなくなりました。  
  
 ストアドプロシージャ**sysmail_update_principalprofile_sp**は**msdb**データベースにあり、 **dbo**スキーマが所有しています。 現在のデータベースが**msdb**でない場合は、3つの部分で構成される名前を使用してプロシージャを実行する必要があります。  
  
## <a name="permissions"></a>アクセス許可  
 このプロシージャの実行権限は、既定では**sysadmin**固定サーバーロールのメンバーに与えています。  
  
## <a name="examples"></a>例  
 **A. プロファイルをデータベースの既定のパブリック プロファイルに設定する**  
  
 次の例では、 `General Use Profile`プロファイルを、 **msdb**データベースのユーザーの既定のパブリックプロファイルに設定します。  
  
```  
EXECUTE msdb.dbo.sysmail_update_principalprofile_sp  
    @principal_name = 'public',  
    @profile_name = 'General Use Profile',  
    @is_default = '1';  
```  
  
 **B. プロファイルをユーザーの既定のプライベート プロファイルに設定する**  
  
 次の例では、 `AdventureWorks Administrator`プロファイルを、 **msdb**データベース内のプリンシパル`ApplicationUser`の既定のプロファイルに設定します。 このプロファイルはプリンシパルに既に関連付けられている必要があります。 以前既定のプロファイルであったプロファイルは引き続きプリンシパルに関連付けられていますが、既定のプロファイルではなくなりました。  
  
```  
EXECUTE msdb.dbo.sysmail_update_principalprofile_sp  
    @principal_name = 'ApplicationUser',  
    @profile_name = 'AdventureWorks Administrator',  
    @is_default = '1' ;  
```  
  
## <a name="see-also"></a>参照  
 [データベース メール](../../relational-databases/database-mail/database-mail.md)   
 [データベースメール構成オブジェクト](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [Transact-sql&#41;&#40;のストアドプロシージャのデータベースメール](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
