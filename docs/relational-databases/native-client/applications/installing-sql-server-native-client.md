---
title: SQL Server Native Client をインストールする |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 07/15/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
author: MightyPen
ms.author: genemi
manager: craigg
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client, uninstalling
- SQLNCLI, installing
- SQLNCLI, uninstalling
- Setup [SQL Server Native Client]
- uninstalling SQL Server Native Client
- data access [SQL Server Native Client], uninstalling SQL Server Native Client
- installing SQL Server Native Client
- SQL Server Native Client, installing
- data access [SQL Server Native Client], installing SQL Server Native Client
- removing SQL Server Native Client
ms.assetid: c6abeab2-0052-49c9-be79-cfbc50bff5c1
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b2c6695fd8e005311667b1edaad1b9e315019487
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2018
ms.locfileid: "51670981"
---
# <a name="installing-sql-server-native-client"></a>SQL Server Native Client のインストール
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 がインストールするときにインストールされている[!INCLUDE[ssSQL15](../../../includes/sssql15-md.md)]します。 
 
 SQL Server 2016 Native Client はありません。 詳細については、[SQL Server Native Client](../../../relational-databases/native-client/sql-server-native-client.md)を参照してください。 
 
SQL Server 2012 Feature Pack の web ページから sqlncli.msi を取得することもできます。 SQL Server Native Client の最新バージョンをダウンロードするには[Microsoft® SQL Server® 2012 Feature Pack](https://www.microsoft.com/download/confirmation.aspx?id=29065)します。 以前のバージョンの場合[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]ネイティブ クライアント コンピューターで、SQL Server 2012 がインストールされてもよりも早く[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client 11.0 は以前のバージョンと並列でインストールされます。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client のファイル (sqlncli11.dll、sqlnclir11.rll、および s11ch_sqlncli.chm) は、次の場所にインストールされます。  
  
 `%SYSTEMROOT%\system32\`  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーと [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーのすべてのレジストリ設定は、インストール処理の一環として適切に行われます。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ヘッダー ファイルとライブラリ ファイル (sqlncli.h と sqlncli11.lib) は、次の場所にインストールされます。  
  
 `%PROGRAMFILES%\Microsoft SQL Server\110\SDK`  
  
 インストールするだけでなく[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]ネイティブ クライアントの一環として、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]インストールもには、sqlncli.msi をという名前の再頒布可能パッケージのインストール プログラムがある、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]次の場所にインストール ディスク`%CD%\Setup\`。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client は、sqlncli.msi を使用して配布できます。 アプリケーションを配置する場合は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client をインストールする必要があります。 チェイナーとブートストラップのテクノロジを使用すると、ユーザーが 1 回のインストール手順に従うだけで複数のパッケージをまとめてインストールできるようになります。 詳細については、「[Visual Studio 2005 用のカスタム ブートストラップ パッケージの作成](https://go.microsoft.com/fwlink/?LinkId=115667)」および「[カスタムの必須コンポーネントの追加](https://go.microsoft.com/fwlink/?LinkId=115668)」をご覧ください。  
  
 x64 バージョンと Itanium バージョンの sqlncli.msi では、32 ビット バージョンの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client もインストールされます。 アプリケーションが、開発時に使用したものとは異なるプラットフォームを対象としている場合、Microsoft ダウンロード センターから x64、Itanium、および x86 用のバージョンの sqlncli.msi をダウンロードできます。  
  
 sqlncli.msi を呼び出すと、既定ではクライアント コンポーネントだけがインストールされます。 クライアント コンポーネント ファイルを使用して開発されたアプリケーションの実行をサポートするは[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client。 SDK コンポーネントもインストールするには、コマンド ラインで `ADDLOCAL=All` を指定します。 以下に例を示します。  
  
 `msiexec /i sqlncli.msi ADDLOCAL=ALL APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  
  
## <a name="silent-install"></a>サイレント インストール  
 msiexec で /passive、/qn、/qb、または /qr オプションを指定する場合、IACCEPTSQLNCLILICENSETERMS=YES も指定して、使用許諾契約の条件に同意することを明示的に指定する必要があります。 このオプションは、すべて大文字で指定する必要があります。  
  
## <a name="uninstalling-sql-server-native-client"></a>SQL Server Native Client のアンインストール  
 などのアプリケーション[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]サーバーおよび[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]ツールによって異なります[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client は、アンインストールする重要なは[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]すべてに依存するアプリケーションがアンインストールされるまで、ネイティブ クライアントです。 警告メッセージに依存するアプリケーションがプロバイダーのユーザーに[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client は、の APPGUID インストール オプションから、MSI での次のように使用します。  
  
 `msiexec /i sqlncli.msi APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  
  
 APPGUID に渡す値は、特定の製品コードです。 Microsoft インストーラーを使用してアプリケーションのセットアップ プログラムをバンドルするときは、製品コードを作成する必要があります。  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client によるアプリケーションの構築](../../../relational-databases/native-client/applications/installing-sql-server-native-client.md)   
 [インストール方法に関するトピック](https://msdn.microsoft.com/library/59de41e7-557f-462a-8914-53ec35496baa)  
  
  
