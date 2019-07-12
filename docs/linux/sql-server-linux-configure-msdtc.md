---
title: Linux で MSDTC を構成する方法
description: この記事では、Linux 上の MSDTC を構成するためのチュートリアルについてを提供します。
author: VanMSFT
ms.author: vanto
manager: jroth
ms.date: 03/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: f4fe81c5e306b059414fe0f2245aca9c9787ee1b
ms.sourcegitcommit: 93d1566b9fe0c092c9f0f8c84435b0eede07019f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67834025"
---
# <a name="how-to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-on-linux"></a>Linux 上の Microsoft 分散トランザクション コーディネーター (MSDTC) を構成する方法

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

この記事では、Linux で Microsoft 分散トランザクション コーディネーター (MSTDC) を構成する方法について説明します。 Linux 上の MSDTC のサポートは、SQL Server 2019 プレビューで導入されました。

## <a name="overview"></a>概要

分散トランザクションは SQL Server on Linux に SQL Server 内で MSDTC と RPC エンドポイント マッパー機能を導入することで有効になっています。 既定では、RPC エンドポイント マッピング プロセスは、受信 RPC 要求のポート 135 をリッスンし、リモート要求に登録されているコンポーネントの情報を提供します。 リモート要求は、エンドポイント マッパーによって返される情報を使用して、MSDTC サービスなど、登録済みの RPC コンポーネントと通信します。 プロセスには、Linux 上の既知のポート (1024 未満のポート番号) にバインドするスーパー ユーザー権限が必要です。 RPC エンドポイント マッパーのプロセスのルート特権を持つ SQL Server の起動を防ぐためには、システム管理者は、SQL Server の RPC エンドポイント マッピングのプロセスにポート 135 でトラフィックをルーティングするのにネットワーク アドレス変換を作成するのに iptables を使用する必要があります。

SQL Server 2019 には、mssql conf ユーティリティの 2 つの構成パラメーターが導入されています。

| mssql-conf setting | 説明 |
|---|---|
| **network.rpcport** | RPC エンドポイント マッパーのプロセスがバインドされる TCP ポート。 |
| **distributedtransaction.servertcpport** | MSDTC サーバーがリッスンするポート。 できない場合は、設定すると、MSDTC サービスを使用してランダムな一時的なポートでサービスが再起動し、ファイアウォールの例外が MSDTC サービスが通信を継続できるようにすることを確認するように再構成する必要があります。 |

これらの設定とその他の関連の MSDTC 設定の詳細については、次を参照してください。 [mssql-conf ツールを使った Linux 上の SQL Server の構成](sql-server-linux-configure-mssql-conf.md#msdtc)します。

## <a name="supported-msdtc-configurations"></a>サポートされている MSDTC の構成

次のような MSDTC 構成がサポートされています。

- OLE TX 分散トランザクションに対して SQL Server on Linux の ODBC プロバイダー。
- JDBC および ODBC プロバイダーを使用して Linux 上の SQL Server に対して XA 分散トランザクション。 XA トランザクションの ODBC プロバイダーを使用して実行する場合は、バージョン 17.3 以降の SQL Server 用 Microsoft ODBC Driver を使用する必要があります。
- リンク サーバー上の分散トランザクション。

制限事項とプレビューの MSDTC の既知の問題は、次を参照してください。 [Linux 上の SQL Server 2019 プレビューのリリース ノート](sql-server-linux-release-notes-2019.md#msdtc)します。

## <a name="msdtc-configuration-steps"></a>MSDTC の構成手順

MSDTC 通信と機能を構成する 3 つの手順があります。 必要な構成手順が行われていない場合、SQL Server は MSDTC 機能を有効にできません。

- 構成**network.rpcport**と**distributedtransaction.servertcpport** mssql 会議を使用します。
- 通信を許可するファイアウォールを構成する**distributedtransaction.servertcpport**ポート 135 とします。
- Linux サーバーのルーティングには、SQL Server のポート 135 で RPC 通信がリダイレクトされるように構成**network.rpcport**します。

次のセクションでは、各手順の詳細な手順を説明します。

## <a name="configure-rpc-and-msdtc-ports"></a>RPC、MSDTC のポートを構成します。

最初に、構成**network.rpcport**と**distributedtransaction.servertcpport** mssql 会議を使用します。 SQL Server に固有でサポートされているすべてのディストリビューション間で一般的な場合は、この手順

1. Mssql conf を使用して設定する、 **network.rpcport**値。 次の例は、13500 に設定します。

   ```bash
   sudo /opt/mssql/bin/mssql-conf set network.rpcport 13500
   ```

2. 設定、 **distributedtransaction.servertcpport**値。 次の例は、51999 に設定します。

   ```bash
   sudo /opt/mssql/bin/mssql-conf set distributedtransaction.servertcpport 51999
   ```

3. SQL Server を再起動してください。

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a name="configure-the-firewall"></a>ファイアウォールの構成

2 番目の手順が通信を許可するファイアウォールを構成するには**servertcpport**ポート 135 とします。  これにより、RPC エンドポイント マッピングのプロセスとその他のトランザクション マネージャーとコーディネーター外部通信するために MSDTC プロセス。 この実際の手順については、ファイアウォール、Linux ディストリビューションによって異なります。 

次の例でこれらの規則を作成する方法を示しています。 **Ubuntu**します。

```bash
sudo ufw allow from any to any port 51999 proto tcp
sudo ufw allow from any to any port 135 proto tcp
```

次の例で実行できる方法を示しています**Red Hat Enterprise Linux (RHEL)** :。

```bash
sudo firewall-cmd --zone=public --add-port=51999/tcp --permanent
sudo firewall-cmd --zone=public --add-port=135/tcp --permanent
sudo firewall-cmd --reload
```

ポートは、次のセクションでルーティングを構成する前に、ファイアウォールを構成するのには重要です。 ファイアウォールを更新すると、場合によっては、ポート ルーティング規則をクリアできます。

## <a name="configure-port-routing"></a>ポートのルーティングを構成します。

Linux サーバーのルーティング テーブルを構成するのには、SQL Server のポート 135 で RPC 通信がリダイレクトされるように**network.rpcport**します。 異なるディストリビューション上のポート転送の構成メカニズムが異なる場合があります。 次のセクションでは、Ubuntu、SUS Enterprise Linux (SLES) および Red Hat Enterprise Linux (RHEL) のガイダンスを提供します。

### <a name="port-routing-in-ubuntu-and-sles"></a>Ubuntu または SLES でのルーティングをポートします。

Ubuntu または SLES は使用しないでください、 **firewalld**ためサービス**iptable**ルールは、ポート ルーティングを実現するために、効率的なメカニズムです。 **Iptable**次のコマンドは、再起動後に、ルールを復元するための手順を指定するため、再起動中にルールが保持されない可能性があります。

1. ポート 135 のルーティング規則を作成します。 次の例では、ポート 135 は、前のセクションで定義されている RPC ポート 13500 に送られます。 置換`<ipaddress>`サーバーの IP アドレスを使用します。

   ```bash
   sudo iptables -t nat -A PREROUTING -d <ip> -p tcp --dport 135 -m addrtype --dst-type LOCAL  \
      -j DNAT --to-destination <ip>:13500 -m comment --comment RpcEndPointMapper
   sudo iptables -t nat -A OUTPUT -d <ip> -p tcp --dport 135 -m addrtype --dst-type LOCAL \
      -j DNAT --to-destination <ip>:13500 -m comment --comment RpcEndPointMapper
   ```

   `--comment RpcEndPointMapper`後のコマンドでこれらの規則を管理するを支援し、前のコマンド パラメーター。

2. 次のコマンドで作成したルーティング規則を表示するには。

   ```bash
   sudo iptables -S -t nat | grep "RpcEndPointMapper"
   ```

3. ルーティング規則をコンピューター上のファイルに保存します。

   ```bash
   sudo iptables-save > /etc/iptables.conf
   ```

4. 規則を再読み込み、再起動後に、次のコマンドを追加`/etc/rc.local`(Ubuntu) 用または`/etc/init.d/after.local`(SLES) 用。

   ```bash
   iptables-restore < /etc/iptables.conf
   ```

   > [!NOTE]
   > 編集するスーパー ユーザー (sudo) 特権が必要、 **rc.local**または**after.local**ファイル。

**Iptables 保存**と**iptables 復元**コマンド、と共にと`rc.local` / `after.local`スタートアップ構成を保存し、iptables を復元する基本的なメカニズムを提供エントリ。 使用可能なオプションの自動化によっては、Linux ディストリビューションにある可能性があるより高度なこともできます。 たとえば、Ubuntu の代替は、 **iptables 永続的な**永続的なエントリを作成するパッケージ。

> [!IMPORTANT]
> 前の手順では、固定の IP アドレスと仮定します。 (手動による介入や DHCP) のため、SQL Server インスタンスの IP アドレスが変更された場合は、削除、iptables を使用して作成された場合は、ルーティング規則を再作成する必要があります。 再作成または既存のルーティング規則を削除する必要がある場合、次のコマンドを使用して古いを削除することができます`RpcEndPointMapper`規則。
> 
> ```bash
> sudo iptables -S -t nat | grep "RpcEndPointMapper" | sed 's/^-A //' | while read rule; do iptables -t nat -D $rule; done
> ```

### <a name="port-routing-in-rhel"></a>RHEL でのルーティング ポート

使用するディストリビューションで**firewalld**両方のサーバーと内部ポート転送ポートを開くために、Red Hat Enterprise Linux、同じサービスなどのサービスを使用できます。 たとえば、Red Hat Enterprise linux、する必要がありますを使用する**firewalld**サービス (を使用して**ファイアウォール cmd**構成ユーティリティを`-add-forward-port`または同様のオプション) の作成し、永続的なポートを管理するにはiptables を使用する代わりにルールを転送します。

```bash
sudo firewall-cmd --permanent --add-forward-port=port=135:proto=tcp:toport=13500
sudo firewall-cmd --reload
```

## <a name="verify"></a>Verify (英語の可能性あり)

この時点では、SQL Server は、分散トランザクションに参加できる必要があります。 SQL Server がリッスンしていることを確認するには、実行、 **netstat**コマンド (RHEL を使用している場合は、最初にインストールする必要があります、 **net ツール**パッケージ)。

```bash
sudo netstat -tulpn | grep sqlservr
```

次のような出力が表示されます。

```bash
tcp 0 0 0.0.0.0:1433 0.0.0.0:* LISTEN 13911/sqlservr
tcp 0 0 127.0.0.1:1434 0.0.0.0:* LISTEN 13911/sqlservr
tcp 0 0 0.0.0.0:13500 0.0.0.0:* LISTEN 13911/sqlservr
tcp 0 0 0.0.0.0:51999 0.0.0.0:* LISTEN 13911/sqlservr
tcp6 0 0 :::1433 :::* LISTEN 13911/sqlservr
tcp6 0 0 ::1:1434 :::* LISTEN 13911/sqlservr
tcp6 0 0 :::13500 :::* LISTEN 13911/sqlservr
tcp6 0 0 :::51999 :::* LISTEN 13911/sqlservr
```

ただし、再起動後、SQL Server が起動しないでリッスンしている、 **servertcpport**最初にディストリビュートされたトランザクションまでです。 ここでは、最初の分散トランザクションまで、この例ではポート 51999 でリッスンしている SQL Server が表示されないとします。

## <a name="configure-authentication-on-rpc-communication-for-msdtc"></a>MSDTC の RPC 通信で認証を構成します。

SQL Server on Linux の MSDTC を使用しない認証 RPC 通信既定。 ただし、ホスト コンピューターが Active Directory (AD) ドメインに参加しているときに行うことが認証された RPC 通信を使用するよう MSDTC を構成する次を使用して**mssql conf**設定。

| 設定 | 説明 |
|---|---|
| **distributedtransaction.allowonlysecurerpccalls**          | 分散トランザクションの唯一の RPC 呼び出しをセキュリティで保護を構成します。 |
| **distributedtransaction.fallbacktounsecurerpcifnecessary** | のみの RPC コールは分散トランザクションのセキュリティを構成します。 |
| **distributedtransaction.turnoffrpcsecurity**               | 有効または分散トランザクションの RPC セキュリティを無効にします。 |

## <a name="next-steps"></a>次の手順

Linux 上の SQL Server に関する詳細については、次を参照してください。 [SQL Server on Linux](sql-server-linux-overview.md)します。
