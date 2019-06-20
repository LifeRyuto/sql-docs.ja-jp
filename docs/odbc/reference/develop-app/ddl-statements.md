---
title: DDL ステートメント |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], DDL statements
- DDL statements [ODBC]
ms.assetid: 96ac9859-5976-4b06-ae1f-2fec3231e266
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9100405c91387faa66b714a94b8259167ae31899
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63267658"
---
# <a name="ddl-statements"></a>DDL ステートメント
データ定義言語 (DDL) ステートメントは、Dbms によって大幅に異なります。 ODBC SQL ステートメントの最も一般的なデータ定義操作を定義します作成すると、テーブル、インデックス、およびビューを削除する。テーブルの変更許可と権限の取り消し。 その他のすべての DDL ステートメントは、データ ソースに固有です。 そのため、相互運用可能なアプリケーションでは、一部のデータ定義操作を実行できません。 一般に、これは問題ではありません、このような操作が高 DBMS 固有にする傾向があり、最適なため、ほとんどの Dbms に専用のデータベース管理ソフトウェアに左が付属またはセットアップ プログラムは、ドライバーに付属します。  
  
 データの定義で別の問題は、そのデータ型の名前は Dbms の間で大幅に異なります。 標準的なデータ型の名前を定義して、DBMS 固有の名前に変換するドライバーを強制ではなく**SQLGetTypeInfo**アプリケーション DBMS 固有のデータ型名を検出するための手段を提供します。 相互運用可能なアプリケーションは作成し、変更テーブルに SQL ステートメントでこれらの名前を使用する必要があります。示した名前[付録 c:SQL 文法](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md)、および[付録 d:データ型](../../../odbc/reference/appendixes/appendix-d-data-types.md)、例のみを示します。
