---
title: DROP EXTERNAL LIBRARY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/27/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP EXTERNAL LIBRARY
- DROP_EXTERNAL_LIBRARY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DROP EXTERNAL LIBRARY
author: dphansen
ms.author: davidph
manager: cgronlund
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 86609c0cb3e66397c4c8c8f3a09fba64b14089e4
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58492824"
---
# <a name="drop-external-library-transact-sql"></a>DROP EXTERNAL LIBRARY (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

既存のパッケージ ライブラリを削除します。 パッケージ ライブラリは、R、Python、Java などのサポートされる外部ランタイムで使用されます。

> [!NOTE]
> SQL Server 2017 では、R 言語と Windows プラットフォームがサポートされています。 Windows および Linux プラットフォームの R、Python、Java は SQL Server 2019 CTP 2.4 でサポートされています。 

## <a name="syntax"></a>構文

```sql
DROP EXTERNAL LIBRARY library_name
[ AUTHORIZATION owner_name ];
```

### <a name="arguments"></a>引数

**library_name**

既存のパッケージ ライブラリの名前を指定します。

ライブラリは、ユーザーに範囲指定されます。 ライブラリ名は、特定のユーザーまたは所有者のコンテキスト内で一意と見なされる必要があります。

**owner_name**

外部ライブラリを所有しているユーザーまたはロールの名前を指定します。

データベース所有者は、他のユーザーによって作成されたライブラリを削除できます。

## <a name="permissions"></a>アクセス許可

ライブラリを削除するには、ALTER ANY EXTERNAL LIBRARY の特権が必要です。 既定では、すべてのデータベース所有者、またはオブジェクトの所有者も外部ライブラリを削除することができます。

### <a name="return-values"></a>戻り値

ステートメントが成功した場合は、情報メッセージが返されます。

## <a name="remarks"></a>Remarks

SQL Server の他の `DROP` とは異なり、このステートメントは、省略可能な承認句の指定をサポートします。 これにより、**dbo** または **db_owner** ロールのユーザーが、データベース内の正規のユーザーによってアップロードされたパッケージ ライブラリを削除することができます。

## <a name="examples"></a>使用例

カスタムの R パッケージ `customPackage` をデータベースに追加します。

```sql
CREATE EXTERNAL LIBRARY customPackage 
FROM (CONTENT = 'C:\temp\customPackage_v1.1.zip')
WITH (LANGUAGE = 'R');
GO
```

`customPackage` ライブラリを削除します。

```sql
DROP EXTERNAL LIBRARY customPackage;
```

## <a name="see-also"></a>参照

[CREATE EXTERNAL LIBRARY (Transact-SQL)](create-external-library-transact-sql.md)  
[ALTER EXTERNAL LIBRARY (Transact-SQL)](alter-external-library-transact-sql.md)  
[sys.external_library_files](../../relational-databases/system-catalog-views/sys-external-library-files-transact-sql.md)  
[sys.external_libraries](../../relational-databases/system-catalog-views/sys-external-libraries-transact-sql.md)  

