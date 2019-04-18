---
title: データベース エンジンへの暗号化接続の有効化 | Microsoft Docs
ms.custom: ''
ms.date: 04/09/2019
ms.prod: sql
ms.prod_service: security
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server], encrypted
- SSL [SQL Server]
- Secure Sockets Layer (SSL)
- encryption [SQL Server], connections
- cryptography [SQL Server], connections
- certificates [SQL Server], installing
- requesting encrypted connections
- installing certificates
- security [SQL Server], encryption
ms.assetid: e1e55519-97ec-4404-81ef-881da3b42006
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 28a2c9bd527fb4996730630a6121d205fbaebf04
ms.sourcegitcommit: 5f38c1806d7577f69d2c49e66f06055cc1b315f1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59429348"
---
# <a name="enable-encrypted-connections-to-the-database-engine"></a>データベース エンジンへの暗号化接続の有効化
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  このトピックでは、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 構成マネージャーを使用して [!INCLUDE[ssDE](../../includes/ssde-md.md)] の証明書を指定することにより、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスへの暗号化接続を有効にする方法について説明します。 サーバー コンピューターには証明書を提供し、クライアント マシンは証明書のルート機関を信頼するように設定する必要があります。 提供は、証明書を Windows にインポートすることでインストールする処理です。  
  
 **サーバー認証**用の証明書が発行されている必要があります。 証明書の名前は、コンピューターの完全修飾ドメイン名 (FQDN) である必要があります。  
  
 証明書は、コンピューター上のユーザーにローカルに格納されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が使用する証明書をインストールするには、ローカル管理者特権を持つアカウントで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを実行している必要があります。

 クライアントは、サーバーが使用する証明書の所有権を検証できる必要があります。 サーバー証明書に署名した証明機関の公開キー証明書をクライアントが持っている場合は、それ以上の構成は必要ありません。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows には、多くの証明機関の公開キー証明書が含まれています。 サーバー証明書に署名した公的または私的な証明機関に対する公開キー証明書をクライアントが持っていない場合は、サーバー証明書に署名した証明機関の公開キー証明書をインストールする必要があります。  
  
> [!NOTE]  
> フェールオーバー クラスターで暗号化を使用する場合、フェールオーバー クラスター内のすべてのノードに対して、仮想サーバーの完全修飾 DNS 名を使用してサーバー証明書をインストールする必要があります。 たとえば、test1.*\<your company>*.com および test2.*\<your company>*.com という 2 つのノードと、virtsql という仮想サーバーがあるクラスターがあるとします。この場合、virtsql.*\<your company>*.com の証明書を両方のノードにインストールする必要があります。 **[ForceEncryption]** オプションの値を **[はい]** に設定できます。

> [!NOTE]
> Azure VM の SQL Server に対する Azure Search インデクサーの暗号化された接続を作成するときは、「 [Azure VM での Azure Search インデクサーから SQL Server への接続の構成](https://azure.microsoft.com/documentation/articles/search-howto-connecting-azure-sql-iaas-to-azure-search-using-indexers/)」をご覧ください。 

## <a name="certificate-requirements"></a>証明書の要件

SQL Server で SSL 証明書を読み込むには、証明書が次の条件を満たしている必要があります。

- 証明書がローカル コンピューターの証明書ストアまたは現在のユーザーの証明書ストアに存在すること。
- SQL Server のサービス アカウントに、SSL 証明書にアクセスするために必要なアクセス許可があること。
- 現在のシステム時刻が証明書の **Valid from** プロパティから証明書の Valid to プロパティまでの範囲であること。
- 証明書がサーバー認証に使用されていること。 つまり、証明書の **[拡張キー使用法]** プロパティで **[サーバー認証] (1.3.6.1.5.5.7.3.1)** が指定されている必要があります。
- 証明書が **AT_KEYEXCHANGE** の **KeySpec** オプションを使用して作成されていること。 通常、証明書のキー使用法プロパティ (**KEY_USAGE**) には、キーの暗号化 (**CERT_KEY_ENCIPHERMENT_KEY_USAGE**) も含まれます。
- 証明書の **Subject** プロパティで、共通名 (CN) がサーバー コンピューターのホスト名または完全修飾ドメイン名 (FQDN) と同一であると示されていること。 SQL Server がフェールオーバー クラスターで実行されている場合、共通名は仮想サーバーのホスト名または FQDN と一致する必要があり、フェールオーバー クラスター内のすべてのノードに証明書を提供する必要があります。
- SQL Server 2008 R2 と SQL Server 2008 R2 Native Client では、ワイルドカード証明書がサポートされます。 他のクライアントでは、ワイルドカード証明書がサポートされていない可能性があります。 詳しくは、クライアントのドキュメントと [KB258858](http://support.microsoft.com/kb/258858) をご覧ください。

## <a name="to-provision-install-a-certificate-on-the-server"></a>サーバーに証明書を提供 (インストール) するには  

> [!NOTE]
> 単一サーバーに証明書を追加するには、「[証明書の管理 (SQL Server 構成マネージャー)](manage-certificates.md)」を参照してください。
  
1. **[スタート]** メニューの **[ファイル名を指定して実行]** をクリックし、 **[名前]** ボックスに「 **MMC** 」と入力して **[OK]** をクリックします。  
  
2. MMC コンソールの **[ファイル]** メニューで、 **[スナップインの追加と削除]** をクリックします。  
  
3. **[スナップインの追加と削除]** ダイアログ ボックスで **[追加]** をクリックします。  
  
4. **[スタンドアロン スナップインの追加]** ダイアログ ボックスで **[証明書]** をクリックし、次に **[追加]** をクリックします。  
  
5. **[証明書スナップイン]** ダイアログ ボックスで **[コンピューター アカウント]** をクリックし、 **[完了]** をクリックします。  
  
6. **[スタンドアロン スナップインの追加]** ダイアログ ボックスで **[閉じる]** をクリックします。  
  
7. **[スナップインの追加と削除]** ダイアログ ボックスで **[OK]** をクリックします。  
  
8. **[証明書]** スナップインで、 **[証明書]**、 **[個人]** の順に展開し、 **[証明書]** を右クリックします。次に **[すべてのタスク]** をポイントし、 **[インポート]** をクリックします。  

9. インポートした証明書を右クリックし、 **[すべてのタスク]** をポイントして、 **[秘密キーの管理]** をクリックします。 **[セキュリティ]** ダイアログ ボックスで、SQL Server サービス アカウントが使用するユーザー アカウントの読み取りアクセス許可を追加します。  
  
10. **[証明書のインポート ウィザード]** を完了して証明書をコンピューターに追加し、MMC コンソールを閉じます。 コンピューターへの証明書の追加の詳細については、Windows のマニュアルを参照してください。  
  
## <a name="to-provision-install-a-certificate-across-multiple-servers"></a>複数のサーバーに証明書をプロビジョニング (インストール) するには

> [!NOTE]
> 複数のサーバーに証明書を追加するには、「[証明書の管理 (SQL Server 構成マネージャー)](manage-certificates.md)」を参照してください。

## <a name="to-export-the-server-certificate"></a>サーバー証明書をエクスポートするには  
  
1. **[証明書]** スナップインで、 **[証明書]** / **[個人]** フォルダーで証明書を探し、 **[証明書]** を右クリックします。次に **[すべてのタスク]** をポイントし、 **[エクスポート]** をクリックします。  
  
2. **証明書のエクスポート ウィザード**を実行して、証明書ファイルを使いやすい場所に格納します。  
  
## <a name="to-configure-the-server-to-force-encrypted-connections"></a>暗号化された接続を強制するサーバーを構成するには  
  
1. **SQL Server 構成マネージャー**で、**[SQL Server ネットワークの構成]** を展開し、**[**_\<server instance> のプロトコル]_ を右クリックします。次に **[プロパティ]** を選びます。  
  
2. **[**_\<instance name> のプロトコル]_ の **[プロパティ]** ダイアログ ボックスの **[証明書]** タブで、**[証明書]** ボックスのドロップダウンから必要な証明書を選択し、**[OK]** をクリックします。  
  
3. **[フラグ]** タブの **[ForceEncryption]** ボックスの一覧の **[はい]** をクリックし、 **[OK]** をクリックしてダイアログ ボックスを閉じます。  
  
4. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスを再開します。  

> [!NOTE]
> クライアントとサーバーの間で安全な接続を確立するには、暗号化された接続を要求するようにクライアントを構成します。 詳細については、[この記事の後半で](#to-configure-the-client-to-request-encrypted-connections)説明します。

### <a name="wildcard-certificates"></a>ワイルドカード証明書

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 以降の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client では、ワイルドカード証明書がサポートされます。 他のクライアントでは、ワイルドカード証明書がサポートされていない可能性があります。 詳しくは、クライアントのドキュメントをご覧ください。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager を使ってワイルドカード証明書を選択することはできません。 ワイルドカード証明書を使うには、`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQLServer\SuperSocketNetLib` のレジストリ キーを編集し、**Certificate** の値に証明書の拇印を (スペースを含めずに) 入力する必要があります。  

> [!WARNING]  
> [!INCLUDE[ssnoteregistry_md](../../includes/ssnoteregistry-md.md)]  

## <a name="to-configure-the-client-to-request-encrypted-connections"></a>暗号化された接続を要求するクライアントを構成するには  

1. 元の証明書ファイルまたはエクスポートした証明書ファイルを、クライアント コンピューターにコピーします。  
  
2. クライアント コンピューターで、 **証明書** スナップインを使用して、ルート証明書またはエクスポートした証明書ファイルをインストールします。  
  
3. コンソール ペインで **[SQL Server Native Client の構成]** を右クリックし、 **[プロパティ]** をクリックします。  
  
4. **[フラグ]** ページの **[プロトコルの暗号化を設定する]** ボックスで、 **[はい]** をクリックします。  
  
## <a name="to-encrypt-a-connection-from-sql-server-management-studio"></a>SQL Server Management Studio から接続を暗号化するには  
  
1. オブジェクト エクスプローラー ツール バーで **[接続]** をクリックし、 **[データベース エンジン]** をクリックします。  
  
2. **[サーバーへの接続]** ダイアログ ボックスで接続情報を入力し、 **[オプション]** をクリックします。  
  
3. **[接続のプロパティ]** タブで **[暗号化接続]** をクリックします。  
  
## <a name="see-also"></a>参照

[Microsoft SQL Server の TLS 1.2 サポート](https://support.microsoft.com/kb/3135244)