---
title: SQL Server on Linux への接続の暗号化 |Microsoft Docs
description: この記事には、Linux 上の SQL Server への接続の暗号化がについて説明します。
author: vin-yu
ms.date: 01/30/2018
ms.author: vinsonyu
manager: craigg
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: ''
helpviewer_keywords:
- Linux, encrypted connections
ms.openlocfilehash: 97714d09839c873c96684579e70e3269f96b0e31
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66705670"
---
# <a name="encrypting-connections-to-sql-server-on-linux"></a>SQL Server on Linux への接続の暗号化

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on Linux を使用してトランスポート層セキュリティ (TLS) 暗号化をクライアント アプリケーションとのインスタンス間のネットワーク経由で送信されるデータ[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]します。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Windows と Linux の両方で同じ TLS プロトコルをサポートしています。TLS 1.2、1.1、および 1.0。 ただし、TLS を構成する手順は、オペレーティング システムに固有[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]が実行されています。  

## <a name="requirements-for-certificates"></a>証明書の要件 
始める前に、証明書がこれらの要件に従うことを確認する必要があります。
- 現在のシステム時刻は、証明書のプロパティをプロパティと有効期間の前に、証明書の発効後にする必要があります。
- 証明書がサーバー認証に使用されていること。 つまり、証明書の [拡張キー使用法] プロパティで [ サーバー認証 ] (1.3.6.1.5.5.7.3.1) が指定されている必要があります。
- AT_KEYEXCHANGE の KeySpec オプションを使用して証明書を作成する必要があります。 通常、証明書のキー使用法プロパティ (KEY_USAGE) では、キーの暗号化 (CERT_KEY_ENCIPHERMENT_KEY_USAGE) も含まれています。
- 証明書の Subject プロパティは、共通名 (CN) が同じホスト名またはサーバー コンピューターの完全修飾ドメイン名 (FQDN) を示す必要があります。 注:ワイルドカード証明書がサポートされています。

## <a name="configuring-the-openssl-libraries-for-use-optional"></a>(省略可能) を使用するため、OpenSSL ライブラリを構成します。
シンボリック リンクを作成することができます、`/opt/mssql/lib/`ディレクトリを参照する`libcrypto.so`と`libssl.so`ライブラリは、暗号化に使用する必要があります。 これは、システムによって提供される既定以外の特定のバージョンの OpenSSL を使用する SQL Server を強制する場合に便利です。 これらのシンボリック リンクが存在しない場合、SQL Server は、システムの既定の構成の OpenSSL ライブラリを読み込みます。

これらのシンボリック リンクに名前を付ける`libcrypto.so`と`libssl.so`に置かれていると、`/opt/mssql/lib/`ディレクトリ。

## <a name="overview"></a>概要
TLS は、クライアント アプリケーションからの接続の暗号化に使用[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]します。 正しく構成されている、ときに、TLS は、プライバシーと、クライアントとサーバー間の通信用のデータの整合性の両方を提供します。  TLS 接続が開始したクライアントまたはサーバーが開始した指定できます。 

## <a name="client-initiated-encryption"></a>クライアントが暗号化を開始 
- **証明書の生成**(/CN は、SQL Server ホストの完全修飾ドメイン名を一致する必要があります)

> [!NOTE]
> この例では、自己署名証明書を使用して、この使わないで運用環境のシナリオ。 CA の証明書を使用する必要があります。 

        openssl req -x509 -nodes -newkey rsa:2048 -subj '/CN=mssql.contoso.com' -keyout mssql.key -out mssql.pem -days 365 
        sudo chown mssql:mssql mssql.pem mssql.key 
        sudo chmod 600 mssql.pem mssql.key   
        sudo mv mssql.pem /etc/ssl/certs/ 
        sudo mv mssql.key /etc/ssl/private/ 

- **SQL Server を構成します。**

        systemctl stop mssql-server 
        cat /var/opt/mssql/mssql.conf 
        sudo /opt/mssql/bin/mssql-conf set network.tlscert /etc/ssl/certs/mssql.pem 
        sudo /opt/mssql/bin/mssql-conf set network.tlskey /etc/ssl/private/mssql.key 
        sudo /opt/mssql/bin/mssql-conf set network.tlsprotocols 1.2 
        sudo /opt/mssql/bin/mssql-conf set network.forceencryption 0 

- **(Windows、Linux、または macOS)、クライアント コンピューターの証明書を登録します。**

    -   CA の署名証明書を使用している場合は、ユーザー証明書ではなく証明書機関 (CA) 証明書をクライアント コンピューターにコピーする必要があります。 
    -   自己署名証明書を使用している場合だけ、.pem ファイルを配布にはそれぞれ次のフォルダーにコピーし、コマンドを実行できるようにします 
        - **Ubuntu**:コピーの証明書と```/usr/share/ca-certificates/```を .crt に名前の変更拡張機能では、dpkg reconfigure の ca 証明書を使用して、システム CA の証明書として有効にします。 
        - **RHEL**:コピーの証明書と```/etc/pki/ca-trust/source/anchors/```使用```update-ca-trust```システム CA の証明書として有効にします。
        - **SUSE**:コピーの証明書と```/usr/share/pki/trust/anchors/```使用```update-ca-certificates```システム CA の証明書として有効にします。
        - **Windows**:ルート証明機関証明書]-> [信頼された .pem ファイルを現在のユーザー証明書として]-> [インポート
        - **macOS**: 
           - 証明書をコピーします。 ```/usr/local/etc/openssl/certs```
           - ハッシュ値を取得する次のコマンドを実行します。 ```/usr/local/Cellar/openssql/1.0.2l/openssql x509 -hash -in mssql.pem -noout```
           - 値に、証明書の名前を変更します。 たとえば、「 ```mv mssql.pem dc2dd900.0```」のように入力します。 Dc2dd900.0 がで確認します。 ```/usr/local/etc/openssl/certs```
    
-   **接続文字列の例** 

    - **[!INCLUDE[ssmanstudiofull-md](../includes/ssmanstudiofull-md.md)]**   
  ![SSMS 接続ダイアログ](media/sql-server-linux-encrypted-connections/ssms-encrypt-connection.png "SSMS 接続ダイアログ")  
  
    - **SQLCMD** 

            sqlcmd  -S <sqlhostname> -N -U sa -P '<YourPassword>' 
    - **ADO.NET** 

            "Encrypt=True; TrustServerCertificate=False;" 
    - **ODBC** 

            "Encrypt=Yes; TrustServerCertificate=no;" 
    - **JDBC** 
    
            "encrypt=true; trustServerCertificate=false;" 

## <a name="server-initiated-encryption"></a>サーバー暗号化の開始 

- **証明書の生成**(/CN は、SQL Server ホストの完全修飾ドメイン名を一致する必要があります)
        
        openssl req -x509 -nodes -newkey rsa:2048 -subj '/CN=mssql.contoso.com' -keyout mssql.key -out mssql.pem -days 365 
        sudo chown mssql:mssql mssql.pem mssql.key 
        sudo chmod 600 mssql.pem mssql.key   
        sudo mv mssql.pem /etc/ssl/certs/ 
        sudo mv mssql.key /etc/ssl/private/ 

- **SQL Server を構成します。**

        systemctl stop mssql-server 
        cat /var/opt/mssql/mssql.conf 
        sudo /opt/mssql/bin/mssql-conf set network.tlscert /etc/ssl/certs/mssql.pem 
        sudo /opt/mssql/bin/mssql-conf set network.tlskey /etc/ssl/private/mssql.key 
        sudo /opt/mssql/bin/mssql-conf set network.tlsprotocols 1.2 
        sudo /opt/mssql/bin/mssql-conf set network.forceencryption 1 
        
-   **接続文字列の例** 

    - **SQLCMD**

            sqlcmd  -S <sqlhostname> -U sa -P '<YourPassword>' 
    - **ADO.NET** 

            "Encrypt=False; TrustServerCertificate=False;" 
    - **ODBC** 

            "Encrypt=no; TrustServerCertificate=no;"  
    - **JDBC** 
    
            "encrypt=false; trustServerCertificate=false;" 
            
> [!NOTE]
> 設定**TrustServerCertificate**クライアントは、証明書の信頼性を検証する CA に接続できない場合は True に設定

## <a name="common-connection-errors"></a>一般的な接続エラー  

|エラー メッセージ |Fix |
|--- |--- |
|証明書チェーンが信頼されていない証明機関によって発行されました。  |このエラーは、クライアントは TLS ハンドシェイク中に SQL サーバーによって提示される証明書の署名を確認することがときに発生します。 クライアントが信頼するかを確認、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]証明書を直接、または SQL Server 証明書に署名する CA です。 |
|対象のプリンシパル名が正しくありません。  |SQL Server の証明書の共通名 フィールドに、クライアントの接続文字列で指定されたサーバー名と一致することを確認します。 |  
|既存の接続はリモート ホストに強制的に切断されました。 |SQL Server に必要な TLS プロトコル バージョンをサポートしていないクライアント、このエラーが発生します。 たとえば場合、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]を TLS 1.2 を必要として、クライアントも TLS 1.2 プロトコルをサポートしているかどうかを確認するように構成します。 |
| | |   
