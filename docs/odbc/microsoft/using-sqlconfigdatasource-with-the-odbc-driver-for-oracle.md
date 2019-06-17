---
title: 使用した SQLConfigDatasource with the ODBC Driver for Oracle |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLConfigDataSource function [ODBC], ODBC driver for Oracle
ms.assetid: e535d1ef-aff9-4ae7-a3ed-ef4ca2584289
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9edd9ae15e66a39abd84a8a6d8e50a83ed4a39ba
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63259335"
---
# <a name="using-sqlconfigdatasource-with-the-odbc-driver-for-oracle"></a>ODBC Driver for Oracle を使用した SQLConfigDatasource の使用
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 次の表にリストが有効な**SQLConfigDatasource** Microsoft ODBC Driver for Oracle、バージョン 1.0 (Msorcl10.dll) と Microsoft ODBC Driver for Oracle、バージョン 2.0 (Msorcl32.dll) に設定します。  
  
> [!NOTE]  
>  Msorcl10.dll ドライバー (バージョン 1.0) を除くすべての設定をサポートしている**Server**します。 Msorcl32.dll ドライバー (バージョン 2.0 以降) では、すべての設定をサポートします。  
  
 一部の設定は、ドライバーでは無視されますで受け入れることが**SQLConfigDatasource**します。 実行時に同意したが、唯一の方法には、ODBC 接続文字列にこれらの設定を含むです。 無視の設定はレジストリに保存されず**SQLConfigDatasource**データ ソースを作成します。  
  
 次の表に*A/N*まで許容される最大長の有効な英数字文字列のことを意味します。 *最大 Len* (最大長) は文字列ターミネータ文字を含む、設定によって受け入れられる許容される文字列の最大長。  
  
|設定|最大の長さ|既定値|有効な値|説明|  
|-------------|-------------|-------------------|------------------|-----------------|  
|BufferSize|7|65535|1000|最小のフェッチ バッファー サイズは最大 65535 バイト|  
|CatalogCap|2|1|0 または 1|1 の場合、nonquoted 識別子は、カタログで大文字に変換関数になります。|  
|ConnectString|128|""|A/N|接続文字列: Msorcl10.dll ドライバーを使用したサーバー名を指定する必要なメソッドです。|  
|説明|256|""|A/N|説明|  
|DSN|33|""|A/N|データ ソースの名前。|  
|GuessTheColDef|4|0|A/N|列は Oracle 定義のスケールを 0 以外の値を返します。|  
|NumberFloat|2|""|0 または 1|0 の場合は、float 型の列が使用できますとして扱われます。 1 の場合、浮動小数点数の列は SQL_DOUBLE として扱われます。|  
|PWD|30|""|A/N|パスワードです。|  
|RDOSupport|2|""|0 または 1|RDO Oracle プロシージャを呼び出すことができます。|  
|コメント|2|0|0 または 1|カタログ関数では、「解説」をが含まれます。|  
|RowLimit|4|""|0 ~ 99 の範囲|SELECT ステートメントによって返される行の最大数。 長さ 0 の文字列では、制限を適用しないことを示します。|  
|[サーバー]|128|""|A/N|Oracle サーバー名。|  
|SynonymColumns|2|1|0 または 1|SQLColumns、シノニムがあります。|  
|SystemTable|2|""|0 または 1|0 の場合、システム テーブルは表示されません。 1 の場合、システム テーブルが表示されます。|  
|TranslationDLL|33|""|A/N|翻訳 .dll の名前。|  
|TranslationName|33|""|A/N|翻訳の名前。|  
|TranslationOption|33|""|A/N|翻訳オプション。|  
|TxnCap|2|""|A/N|トランザクションに対応します。 0 の場合、ドライバーは、トランザクションをサポートしないを報告します。 1 の場合、ドライバーがトランザクションを実行できることを報告します。|  
|UID|30|""|A/N|ユーザー名。|
