---
title: 付録 D:データの種類 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- C data types [ODBC], defined
- SQL data types [ODBC], defined
- data types [ODBC]
- data types [ODBC], about data types
ms.assetid: 981d49c3-3531-4543-aa75-5bd9e4f67000
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 75ff7e83aa87bca9f33a3a8f44447af2eb60c581
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2018
ms.locfileid: "52504021"
---
# <a name="appendix-d-data-types"></a>付録 D:データ型
ODBC では、2 つのデータ型のセットを定義します。SQL データ型と C データ型。 SQL データ型は、データ ソースに格納されているデータのデータ型を示します。 C データ型は、アプリケーションのバッファーに格納されたデータのデータ型を示します。  
  
 SQL データ型は、sql-92 標準に従って各 DBMS によって定義されます。 定義は、型の識別子、sql-92 標準で指定された各 SQL データ型では、ODBC、 **#define** ODBC 関数の引数として渡したり、結果セットのメタデータに返される値。 唯一の SQL 92 ODBC でサポートされていないデータ型は (ODBC SQL_BIT 型は、異なる特性を持つ) ビット、BIT_VARYING、TIME_WITH_TIMEZONE、TIMESTAMP_WITH_TIMEZONE、および NATIONAL_CHARACTER します。 ドライバーは ODBC SQL データ型識別子と個々 のドライバーの SQL データ型識別子へのデータ ソースに固有の SQL データ型のマッピングを担当します。 SQL データ型は、実装記述子の SQL_DESC_CONCISE_TYPE フィールドで指定されます。  
  
 ODBC C データ型とその対応する ODBC 型識別子を定義します。 アプリケーションの適切な C 型の識別子を渡すことによって結果セットのデータを受信するバッファーの C データ型を指定します、 *TargetType*への呼び出しで引数**SQLBindCol**または**SQLGetData**します。 適切な C 型の識別子を渡すことによって、ステートメントのパラメーターを格納するバッファーの C 型を指定します、 *ValueType*への呼び出しで引数**SQLBindParameter**します。 C データ型は、アプリケーション記述子を SQL_DESC_CONCISE_TYPE フィールドで指定されます。  
  
> [!NOTE]  
>  ドライバー固有の C データ型はありません。  
  
 各 SQL データ型は、ODBC C データ型に対応します。 データ ソースからデータを返す前に、ドライバーは、これを指定の C データ型に変換します。 データ ソースにデータを送信する前に、ドライバーは、これを指定の C データ型から変換します。  
  
 この付録には、次のトピックが含まれています。  
  
-   [データ型識別子の使用](../../../odbc/reference/appendixes/using-data-type-identifiers.md)  
  
-   [SQL データ型](../../../odbc/reference/appendixes/sql-data-types.md)  
  
-   [C データ型](../../../odbc/reference/appendixes/c-data-types.md)  
  
-   [データ型識別子と記述子](../../../odbc/reference/appendixes/data-type-identifiers-and-descriptors.md)  
  
-   [疑似型識別子](../../../odbc/reference/appendixes/pseudo-type-identifiers.md)  
  
-   [バイナリ形式でのデータ転送](../../../odbc/reference/appendixes/transferring-data-in-its-binary-form.md)  
  
-   [間隔と数値データ型のガイドライン](../../../odbc/reference/appendixes/guidelines-for-interval-and-numeric-data-types.md)  
  
-   [グレゴリオ暦カレンダーの制限](../../../odbc/reference/appendixes/constraints-of-the-gregorian-calendar.md)  
  
-   [列サイズ、小数点以下の桁数、転送オクテット長、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)  
  
-   [SQL から C データ型へのデータ変換](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)  
  
-   [C から SQL データ型へのデータ変換](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)  
  
 ODBC データ型の詳細については、[ODBC のデータ型](../../../odbc/reference/develop-app/data-types-in-odbc.md)を参照してください。 ドライバー固有の SQL データ型については、ドライバーのドキュメントを参照してください。
