---
title: データ ソース (ODBC) の削除 |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 08/01/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data sources [ODBC]
ms.assetid: 910e3e16-7b91-49d8-80bb-b4243926afaa
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: fbd14b4f784f93f78c317268799571220da3a3c9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67939574"
---
# <a name="configuring-the-sql-server-odbc-driver---delete-a-data-source"></a>SQL Server ODBC ドライバーの構成 - データ ソースの削除
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降で ODBC アプリケーションを使用する前に、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でカタログ ストアド プロシージャのバージョンをアップグレードする方法や、データ ソースを追加、削除、およびテストする方法を理解しておく必要があります。  
  
  プログラムで ODBC アドミニストレーターを使用してデータ ソースを削除することができます (を使用して[SQLConfigDataSource](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md))、または (する場合、ファイル データ ソース名) にファイルを削除しています。  
  
### <a name="to-delete-a-data-source-by-using-odbc-administrator"></a>ODBC アドミニストレーターを使用してデータ ソースを削除するには  
  
1.  **コントロール パネルの** オープン**管理ツール**、いずれかをダブルクリックして**ODBC データ ソース (64 ビット)** または**ODBC データ ソース (32 ビット)** . コマンド プロンプトから odbcad32.exe を実行することもできます。  
  
2.  をクリックして、**ユーザー DSN**、**システム DSN**、または**ファイル DSN**タブ。  
  
3.  削除するデータ ソースを選択します。  
  
4.  クリックして**削除**、削除を確定します。  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

## <a name="example"></a>例  
 データ ソースをプログラムで削除するには、呼び出す[SQLConfigDataSource](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md) 2 番目のパラメーターとして ODBC_REMOVE_DSN または ODBC_REMOVE_SYS_DSN を使用します。  
  
 次のサンプルでは、データ ソースをプログラムで削除する方法を示しています。  
  
```  
// remove_odbc_data_source.cpp  
// compile with: ODBCCP32.lib user32.lib  
#include <iostream>  
#include \<windows.h>  
#include \<odbcinst.h>  
  
int main() {   
   LPCSTR provider = "SQL Server";   // Windows SQL Server Driver  
   LPCSTR provider = "SQL Server";   // Windows SQL Server driver  
   LPCSTR provider2 = "SQL Server Native Client 11.0";   // SQL Server 2012 Native Client driver  
   LPCSTR dsnname = "DSN=data2";  
   BOOL retval = SQLConfigDataSource(NULL, ODBC_REMOVE_DSN, provider, dsnname);  
   std::cout << retval;   // 1 if successful  
}  
```  
  
## <a name="see-also"></a>関連項目  
 [データ ソースの追加&#40;ODBC&#41;](../../relational-databases/native-client-odbc-how-to/configuring-the-sql-server-odbc-driver-add-a-data-source.md)  
  
  
