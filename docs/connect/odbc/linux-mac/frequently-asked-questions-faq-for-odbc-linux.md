---
title: ODBC Linux と macOS のよく寄せられる質問 (FAQ) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 65bfd6d2-c83d-4528-a5e1-a85b125a4f4a
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: aadbf8d0cc850d71626663883587195a8229ada8
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66785858"
---
# <a name="frequently-asked-questions-faq-for-odbc-linux-and-macos"></a>ODBC Linux と macOS のよく寄せられる質問 (FAQ)
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

次に、ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on Linux および macOS に関する質問に対する回答を示します。
  
## <a name="frequently-asked-questions"></a>よく寄せられる質問

**Linux または macOS 上の既存の ODBC アプリケーションは、どのようにドライバーと連動しますか?**  
他のドライバーを使用して Linux または macOS 上でコンパイルして実行している ODBC アプリケーションは、コンパイルして実行することができます。 
  
**このバージョンのドライバーがサポートしている [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] の機能はどれですか?**

ODBC Driver on Linux および macOS は、LocalDB を除く [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] のすべてのサーバー機能をサポートしています。 詳細については[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]サポートについては、「 [Programming Guidelines](../../../connect/odbc/linux-mac/programming-guidelines.md)します。  
  
**ドライバーは Kerberos 認証をサポートしますか?**  
可能。 既存の Kerberos 環境のセットアップがあればを使用してサーバーに接続できる必要があります、 `Trusted_Connection=Yes` DSN または接続文字列オプションです。 詳細については、「[統合認証を使用する](../../../connect/odbc/linux-mac/using-integrated-authentication.md)」を参照してください。  
  
**アプリケーションではどの Unicode エンコードを使用すればよいですか?**  
SQL_CHAR データには UTF-8、SQL_WCHAR データには UTF-16 を使用してください。  

**ドライバーの試用および評価のために、ダウンロードしてドライバーで実行できる ODBC サンプルはありますか?**

サンプルについては、「 [Use Existing MSDN C++ ODBC Samples for the ODBC Driver on Linux (Linux の ODBC ドライバーに既存の MSDN C++ ODBC サンプルを使用する)](https://blogs.msdn.com/b/sqlblog/archive/2012/01/26/use-existing-msdn-c-odbc-samples-for-microsoft-linux-odbc-driver.aspx) 」を参照してください。 またこれは、macOS の ODBC ドライバーに当てはまります。 

**Linux で ODBC ドライバーは、または macOS のオープン ソースですか。**

Linux と macOS の ODBC ドライバーはオープン ソース製品ではありません。  

## <a name="see-also"></a>参照
[Linux および macOS に Microsoft ODBC Driver for SQL Server をインストールする](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)
