---
title: JDBC ドライバーの展開 | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 3ad3508d-d9b1-47fb-a63b-21cdc3ed44e0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7e8b4655695d37db10d18fbaa6215587036017bf
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 08/14/2019
ms.locfileid: "69028107"
---
# <a name="deploying-the-jdbc-driver"></a>JDBC ドライバーの展開
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] に依存するアプリケーションを展開する場合、使用するアプリケーションと共に JDBC ドライバーを再配布する必要があります。 Windows オペレーティング システムのコンポーネントである Windows Data Access Component (Windows DAC) とは異なり、JDBC ドライバーは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のコンポーネントであると見なされます。  
  
 アプリケーションと共に JDBC ドライバーを展開する方法には 2 種類あります。 1 つは、JDBC ドライバーのファイルを、独自のカスタム インストール パッケージの一部として含める方法です。 2 つ目の方法では、Microsoft によって提供される JDBC インストール パッケージを使用します。これは、[デベロッパー センター内の Microsoft JDBC Driver for SQL Server](https://go.microsoft.com/fwlink/?LinkId=70166) に関するページからダウンロードできます。  
  
 以下のセクションでは、Windows および UNIX オペレーティング システム上で JDBC インストール パッケージを使用する方法について説明します。  
  
> [!NOTE]  
>  一般的な Java アプリケーションの展開については、Java の Web サイトを参照してください。  
  
## <a name="deploying-the-jdbc-driver-on-windows-systems"></a>Windows システム上での JDBC ドライバーの展開  
 Windows オペレーティング システム上で JDBC ドライバーを展開する場合、実行可能な ZIP ファイル形式のインストール パッケージを使用する必要があります。これは通常、`sqljdbc_<version>_<language>.exe` という名前です。  
  
 実行可能な ZIP ファイルをサイレント実行するには、次のようにコマンド ライン上またはバッチ ファイル内で `/auto` コマンド ライン オプションを使用する必要があります。  
  
 `sqljdbc_<version>_<language>.exe /auto`  
  
> [!NOTE]  
>  `/auto` オプションを使用しても、ユーザーの画面上に WinZip ダイアログ ボックスは表示されるため、それは完全なサイレント インストールではありません。 ただし、このダイアログ ボックスで操作を行う必要はなく、解凍処理が完了するとダイアログ ボックスは閉じます。  
  
## <a name="deploying-the-driver-on-unix-systems"></a>UNIX システム上での JDBC ドライバーの展開 
 UNIX オペレーティング システム上で JDBC ドライバーを展開する場合、GZIP ファイル形式のインストール パッケージを使用する必要があります。これは通常、`sqljdbc_<version>_<language>.tar.gz` という名前です。  
  
 JDBC ドライバーをインストールする前に、gzip ユーティリティおよび tar ユーティリティの両方がユーザーのシステム上にインストールされ、これらのユーティリティの実行可能ファイルを含むフォルダーが PATH 環境変数に追加されていることを確認します。  
  
 zip 形式の tar ファイルをアンパックするには、ドライバーをアンパックするディレクトリに移動し、次のコマンドを入力します。  
  
 `gzip -d sqljdbc_<version>_<language>.tar.gz`  
  
 tar ファイルをアンパックするには、ドライバーをインストールするディレクトリに tar ファイルを移動し、次のコマンドを入力します。  
  
 `tar -xf sqljdbc_<version>_<language>.tar`  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーの概要](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
