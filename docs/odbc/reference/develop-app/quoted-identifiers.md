---
title: 引用符で囲まれた識別子 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], quoted identifiers
- quoted identifiers [ODBC]
ms.assetid: 729ba55f-743b-4a04-8c39-ac0a9914211d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3bc4d8378c243edf9f01cca58ff8be11d675711a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68079000"
---
# <a name="quoted-identifiers"></a>引用符で囲まれた識別子
SQL ステートメントでは、特殊文字または一致するキーワードを含む識別子は、*識別子引用符*で囲む必要があります。このような文字で囲まれた識別子は、*引用符で囲ま*れた識別子 (SQL-92 では区切られた*識別子*とも呼ばれます) と呼ばれます。 たとえば、次の**SELECT**ステートメントでは、アカウントの買掛金識別子は引用符で囲まれています。  
  
```  
SELECT * FROM "Accounts Payable"  
```  
  
 識別子を引用符で囲む理由は、ステートメントを解析することです。 たとえば、前のステートメントで勘定科目が引用符で囲まれていない場合、パーサーは2つのテーブル (Accounts および買掛金) があると想定し、コンマで区切られていないという構文エラーを返します。 識別子の引用符文字はドライバー固有であり、 **SQLGetInfo**の SQL_IDENTIFIER_QUOTE_CHAR オプションを使用して取得されます。 の特殊文字とキーワードの一覧は、 **SQLGetInfo**の SQL_SPECIAL_CHARACTERS オプションと SQL_KEYWORDS オプションを使用して取得されます。  
  
 相互運用可能なアプリケーションでは、多くの場合、Oracle の ROWID 列など、擬似列以外のすべての識別子を引用符で囲む必要があります。 **Sqlの列**には、擬似列の一覧が返されます。 また、オブジェクト名に特殊文字を含めることができるアプリケーション固有の制限がある場合は、それらの位置で特殊文字を使用しない、相互運用可能なアプリケーションに適しています。
