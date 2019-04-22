---
title: Windows への PolyBase のインストール | Microsoft Docs
ms.custom: ''
ms.date: 09/24/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: polybase
ms.topic: conceptual
helpviewer_keywords:
- PolyBase, installation
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 6783112203e5c63aae41749f942da6240265eea3
ms.sourcegitcommit: 323d2ea9cb812c688cfb7918ab651cce3246c296
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58872302"
---
# <a name="install-polybase-on-windows"></a>Windows への PolyBase のインストール

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server の試用版は [SQL Server 評価版ソフトウェア](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016) からインストールすることができます。 
   
## <a name="prerequisites"></a>Prerequisites  
   
- 64 ビット SQL Server 評価版。  
   
- Microsoft .NET Framework 4.5。  

- Oracle Java SE Runtime Environment (JRE). バージョン 7 (7.51 以降) および 8 がサポートされます。 [JRE](https://www.oracle.com/technetwork/java/javase/downloads/jre8-downloads-2133155.html) と [Server JRE](https://www.oracle.com/technetwork/java/javase/downloads/server-jre8-downloads-2133154.html) のどちらも機能します。 [Java SE ダウンロード](https://www.oracle.com/technetwork/java/javase/downloads/index.html)に移動します。 JRE が存在しない場合、インストーラーが失敗します。 JRE9 と JRE10 はサポートされていません。

- 最小メモリ:4 GB。 
   
- 最小ハード ディスク容量: 2 GB。
  
- 推奨:16-GB 以上の RAM。
   
- PolyBase が正常に機能するには、TCP/IP を有効にする必要があります。 TCP/IP は、Developer Edition と Express Edition を除く SQL Server のすべてのエディションで、既定で有効です。 Developer Edition および Express Edition で PolyBase が正常に機能するためには、TCP/IP 接続を有効にする必要があります。 「[サーバー ネットワーク プロトコルの有効化または無効化](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)」を参照してください。

- MSVC++ 2012。 

> [!NOTE]
> 
> PolyBase は各マシンで 1 つの SQL Server インスタンスにのみインストールできます。
> 
> [!IMPORTANT]
> 
> Hadoop に対して計算プッシュダウン機能を使用するには、ターゲットの Hadoop クラスターに、ジョブの履歴サーバーが有効になっている HDFS のコア コンポーネントの YARN と MapReduce がある必要があります。 PolyBase から MapReduce 経由でプッシュダウン クエリを送信し、ジョブの履歴サーバーからステータスをプルします。 いずれかのコンポーネントがない場合、クエリは失敗します。
  
## <a name="single-node-or-polybase-scale-out-group"></a>シングル ノードまたは PolyBase スケールアウト グループ

SQL Server インスタンスに PolyBase をインストールする前に、シングル ノード インストールが必要なのか、[PolyBase スケールアウト グループ](../../relational-databases/polybase/polybase-scale-out-groups.md)が必要なのかを決めます。

PolyBase スケールアウト グループの場合、次のことを確認します。

- すべてのマシンが同じドメインにある。
- PolyBase のインストール時、同じサービス アカウントとパスワードを使用する。
- SQL Server インスタンスがネットワーク経由で相互に通信できる。
- SQL Server インスタンスがすべて同じバージョンの SQL Server である。

スタンドアロンまたはスケールアウト グループの PolyBase をインストールすると、後から変更することはできません。 この設定を変更するには、この機能をアンインストールしてから再インストールする必要があります。

## <a name="use-the-installation-wizard"></a>インストール ウィザードの使用
   
1. SQL Server の setup.exe を実行します。   
   
2. **[インストール]** を選択し、**[SQL Server の新規スタンドアロン インストールを実行するか、既存のインストールに機能を追加します]** を選択します。  
   
3. [機能の選択] ページで、**[外部データ用 PolyBase クエリ サービス]** を選択します。  

   ![PolyBase サービス](../../relational-databases/polybase/media/install-wizard.png "PolyBase サービス")  
   
4. [Server の構成] ページで、**SQL Server PolyBase エンジン サービス**と **SQL Server PolyBase Data Movement Service** を同じアカウントで実行するように構成します。  
   
   > [!IMPORTANT] 
   >
   >PolyBase スケールアウト グループで、すべてのノード上の PolyBase エンジンおよび PolyBase Data Movement サービスを、同じドメイン アカウントで実行する必要があります。 「[PolyBase スケールアウト グループ](#enable)」を参照してください。
   
5. [PolyBase の構成] ページで、次の 2 つのオプションのいずれかを選択します。 詳細については、「[PolyBase スケールアウト グループ](../../relational-databases/polybase/polybase-scale-out-groups.md) 」を参照してください。  
   
   - スタンドアロンの PolyBase 対応インスタンスとして、SQL Server インスタンスを使用します。  
   
     SQL Server インスタンスをスタンドアロンのヘッド ノードとして使用するには、このオプションを選択します。  
   
   - PolyBase スケールアウト グループの一部として、SQL Server インスタンスを使用します このオプションにより、ファイアウォールが開かれて、着信接続が許可されます。 SQL Server データベース エンジン、SQL Server PolyBase エンジン、SQL Server PolyBase Data Movement サービス、および SQL ブラウザーへの接続が許可されます。 ファイアウォールでは、PolyBase スケールアウト グループ内の他のノードからの着信接続も許可されます。  
   
     このオプションにより、Microsoft 分散トランザクション コーディネーター (MSDTC) ファイアウォール接続も有効になり、MSDTC レジストリの設定が変更されます。  
   
6. [PolyBase の構成] ページで、少なくとも 6 つのポートを含むポート範囲を指定します。 SQL Server セットアップにより、この範囲の最初の 6 つの利用可能なポートが割り当てられます。  

   > [!IMPORTANT]
   >
   > インストール後に、[PolyBase 機能を有効にする](#enable)必要があります。


##  <a name="installing"></a> コマンド プロンプトの使用

次の表の値を使用して、インストール スクリプトを作成します。 SQL Server PolyBase エンジンと SQL Server PolyBase Data Movement サービスは、同じアカウントで実行する必要があります。 PolyBase スケールアウト グループで、すべてのノード上の PolyBase サービスを、同じドメイン アカウントで実行する必要があります。  
   
<!--SQL Server 2016/2017-->
::: moniker range="= sql-server-2016 || = sql-server-2017"

|SQL Server のコンポーネント (SQL Server component)|パラメーターおよび値|[説明]|  
|--------------------------|--------------------------|-----------------|  
|SQL Server セットアップ コントロール|**必須**<br /><br /> /FEATURES=PolyBase|PolyBase 機能を選択します。|  
|SQL Server PolyBase エンジン|**省略可**<br /><br /> /PBENGSVCACCOUNT|エンジン サービスのアカウントを指定します。 既定値は、 **NT Authority\NETWORK SERVICE**です。|  
|SQL Server PolyBase エンジン|**省略可**<br /><br /> /PBENGSVCPASSWORD|エンジン サービス アカウントのパスワードを指定します。|  
|SQL Server PolyBase エンジン|**省略可**<br /><br /> /PBENGSVCSTARTUPTYPE|PolyBase エンジン サービスのスタートアップ モードを指定します (Automatic (既定)、Disabled、Manual)。|  
|SQL Server PolyBase Data Movement |**省略可**<br /><br /> /PBDMSSVCACCOUNT|データ移動サービスのアカウントを指定します。 既定値は、 **NT Authority\NETWORK SERVICE**です。|  
|SQL Server PolyBase Data Movement |**省略可**<br /><br /> /PBDMSSVCPASSWORD|データ移動アカウントのパスワードを指定します。|  
|SQL Server PolyBase Data Movement |**省略可**<br /><br /> /PBDMSSVCSTARTUPTYPE|データ移動サービスのスタートアップ モードを指定します (Automatic (既定)、Disabled、Manual)。|  
|PolyBase|**省略可**<br /><br /> /PBSCALEOUT|PolyBase スケールアウト計算グループの一部として SQL Server インスタンスを使用するかどうかを指定します。 <br />サポートされる値:True、False。|  
|PolyBase|**省略可**<br /><br /> /PBPORTRANGE|PolyBase サービスのポート範囲 (6 ポート以上) を指定します。 例:<br /><br /> `/PBPORTRANGE=16450-16460`|  

::: moniker-end
<!--SQL Server 2019-->
::: moniker range=">= sql-server-ver15 || =sqlallproducts-allversions"

|SQL Server のコンポーネント (SQL Server component)|パラメーターおよび値|[説明]|  
|--------------------------|--------------------------|-----------------|  
|SQL Server セットアップ コントロール|**必須**<br /><br /> /FEATURES=PolyBaseCore, PolyBaseJava, PolyBase | PolyBaseCore では、Hadoop 接続を除くすべての PolyBase 機能のサポートがインストールされます。 PolyBaseJava では Hadoop 接続が有効化されます。 PolyBase では両方ともインストールされます。 |  
|SQL Server PolyBase エンジン|**省略可**<br /><br /> /PBENGSVCACCOUNT|エンジン サービスのアカウントを指定します。 既定値は、 **NT Authority\NETWORK SERVICE**です。|  
|SQL Server PolyBase エンジン|**省略可**<br /><br /> /PBENGSVCPASSWORD|エンジン サービス アカウントのパスワードを指定します。|  
|SQL Server PolyBase エンジン|**省略可**<br /><br /> /PBENGSVCSTARTUPTYPE|PolyBase エンジン サービスのスタートアップ モードを指定します (Automatic (既定)、Disabled、Manual)。|  
|SQL Server PolyBase Data Movement |**省略可**<br /><br /> /PBDMSSVCACCOUNT|データ移動サービスのアカウントを指定します。 既定値は、 **NT Authority\NETWORK SERVICE**です。|  
|SQL Server PolyBase Data Movement |**省略可**<br /><br /> /PBDMSSVCPASSWORD|データ移動アカウントのパスワードを指定します。|  
|SQL Server PolyBase Data Movement |**省略可**<br /><br /> /PBDMSSVCSTARTUPTYPE|データ移動サービスのスタートアップ モードを指定します (Automatic (既定)、Disabled、Manual)。|  
|PolyBase|**省略可**<br /><br /> /PBSCALEOUT|PolyBase スケールアウト計算グループの一部として SQL Server インスタンスを使用するかどうかを指定します。 <br />サポートされる値:True、False。|  
|PolyBase|**省略可**<br /><br /> /PBPORTRANGE|PolyBase サービスのポート範囲 (6 ポート以上) を指定します。 例:<br /><br /> `/PBPORTRANGE=16450-16460`|  

::: moniker-end

インストール後に、[PolyBase 機能を有効にする](#enable)必要があります。



**例**

この例は、サンプルのセットアップ スクリプトを示しています。  

```cmd
   
Setup.exe /Q /ACTION=INSTALL /IACCEPTSQLSERVERLICENSETERMS /FEATURES=SQLEngine,PolyBase   
/INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="\<fabric-domain>\Administrator"   
/INSTANCEDIR="C:\Program Files\Microsoft SQL Server" /PBSCALEOUT=TRUE   
/PBPORTRANGE=16450-16460 /SECURITYMODE=SQL /SAPWD="<StrongPassword>"   
/PBENGSVCACCOUNT="<DomainName>\<UserName>" /PBENGSVCPASSWORD="<StrongPassword>"   
/PBDMSSVCACCOUNT="<DomainName>\<UserName>" /PBDMSSVCPASSWORD="<StrongPassword>"  
   
```  

## <a id="enable"></a> PolyBase を有効にする

インストールが完了したら、PolyBase を有効にしてその機能にアクセスできるようにする必要があります。 SQL Server 2019 CTP 2.0 に接続するには、インストール後に PolyBase を有効にする必要があります。 次の Transact-SQL コマンドを使用します。


```sql
exec sp_configure @configname = 'polybase enabled', @configvalue = 1;
RECONFIGURE [ WITH OVERRIDE ]  ;
```
その後、インスタンスを再起動する必要があります。


## <a name="post-installation-notes"></a>インストール後の注意  

PolyBase は、DWConfiguration、DWDiagnostics、および DWQueue の 3 つのユーザー データベースをインストールします。 これらのデータベースは PolyBase で使用されます。 変更したり削除しないでください。  
   
### <a id="confirminstall"></a> インストールの確認方法  

次のコマンドを実行します。 PolyBase がインストールされている場合は 1 が返されます。 それ以外の場合は 0 が返されます。  

```sql  
SELECT SERVERPROPERTY ('IsPolyBaseInstalled') AS IsPolyBaseInstalled;  
```  

### <a name="firewall-rules"></a>ファイアウォール規則  

SQL Server PolyBase のセットアップでは、コンピューターに次のファイアウォール規則が作成されます。  
   
- SQL Server PolyBase - Database Engine - \<SQLServerInstanceName> (TCP-In)  
   
- SQL Server PolyBase - PolyBase Services - \<SQLServerInstanceName> (TCP-In)  

- SQL Server PolyBase - SQL Browser - (UDP-In)  
   
インストール時に、PolyBase スケール アウト グループの一部として SQL Server インスタンスを使用する場合は、これらの規則が有効になります。 ファイアウォールが開かれて、着信接続が許可されます。 SQL Server データベース エンジン、SQL Server PolyBase エンジン、SQL Server PolyBase Data Movement サービス、および SQL ブラウザーへの接続が許可されます。 インストール中にコンピューターでファイアウォール サービスが実行されていない場合、SQL Server セットアップはこれらの規則を有効にできません。 その場合は、コンピューターでファイアウォール サービスを開始し、これらの規則をインストール後に有効にします。  
   
#### <a name="to-enable-the-firewall-rules"></a>ファイアウォール規則を有効にするには  

1. **コントロール パネル**を開きます。  

2. **[システムとセキュリティ]** を選択し、**[Windows ファイアウォール]** を選択します。  
   
3. **[詳細設定]** を選択して、**[受信の規則]** を選択します。  
   
4. 無効になっている規則を右クリックして、**[規則の有効化]** を選択します。  
   
### <a name="polybase-service-accounts"></a>PolyBase サービス アカウント

PolyBase エンジンと PolyBase Data Movement サービスのサービス アカウントを変更するには、PolyBase 機能をアンインストールし、再インストールします。

## <a name="next-steps"></a>次の手順  

「 [PolyBase configuration](../../relational-databases/polybase/polybase-configuration.md)」を参照してください。
