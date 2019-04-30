---
title: Analysis Services のインストール |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0904dc53e17ed140310df38d1f63dc9fe3fc45cb
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63054540"
---
# <a name="install-sql-server-analysis-services"></a>SQL Server Analysis Services をインストールします。
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  SQL Server Analysis Services は、表形式モデル、多次元キューブ、およびレポート、スプレッドシート、およびダッシュ ボードからアクセスできるデータ マイニング モデルをホストする分析データベース サーバーです。  
  
 Analysis Services は、複数のインスタンスが 1 台のコンピューターに複数のコピーをインストールまたは新旧バージョンを並列に実行できます。 インストールする任意のインスタンスは、セットアップ時に決定される 3 つのモードのいずれかで実行されます。多次元およびデータ マイニング、表形式、または SharePoint。 複数のモードを使用する場合は、それぞれに個別のインスタンスが必要です。  
  
 特定のモードでサーバーをインストールすると、そのモードに準拠しているホスト ソリューションを使用できます。 たとえば、ネットワーク上で表形式モデルのデータにアクセスする場合は、表形式モードのサーバーが必要です。  
  
## <a name="get-tools-and-designers"></a>ツールとデザイナーの取得  
 SQL Server セットアップでは、ソリューション デザインまたはサーバー管理に使用されるモデル デザイナーまたは管理ツールがインストールされなくなりました。 このリリースでは、ツールには次のリンクから入手できる個別のインストールが用意されています。  
  
-   [SQL Server Management Studio (SSMS) のダウンロード](../../../ssms/download-sql-server-management-studio-ssms.md)  
  
-   [SQL Server Data Tools (SSDT) のダウンロード](../../../ssdt/download-sql-server-data-tools-ssdt.md)  
  
 SSMS と SSDT が Analysis Services インスタンスとデータを操作する必要があります。 ツールは、どこにでもインストールできますが、接続を試行する前に、サーバーでポートを構成してください。 詳細については、「 [Analysis Services のアクセスを許可するための Windows ファイアウォールの構成](../../../analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access.md) 」を参照してください。  
  
## <a name="install-using-a-wizard"></a>ウィザードを使用したインストール  
 Analysis Services をインストールする場合に使用する SQL Server インストール ウィザードのページを次の一覧に示します。  
  
1.  セットアップの機能ツリーで **[Analysis Services]** をクリックします。  
  
     ![セットアップの機能ツリー Analsyis サービスを示す](../../../analysis-services/instances/install-windows/media/ssas-setupas.gif "Analsyis サービスを示すセットアップの機能ツリー")  
  
2.  Analysis Services の構成 ページで、モードを選択します。 表形式モードでは、既定値が、.  
  
     ![Analysis Services の構成オプションを使用してセットアップ ページ](../../../analysis-services/instances/install-windows/media/ssas-setupasconfig.png "Analysis Services の構成オプションを使用してセットアップ ページ")  
  
  表形式モードでは、表形式モデルの既定のストレージには、xVelocity メモリ内分析エンジン (VertiPaq) を使用します。 サーバーに表形式モデルを配置した後は、メモリ負荷の高いストレージする代わりに DirectQuery ディスク ストレージを使用する表形式ソリューションを選択的に構成できます。  
 
 多次元およびデータ マイニング モードの使用 MOLAP 既定のストレージとしての Analysis Services に配置されたモデル。 サーバーへの展開後、Analysis Services 多次元データベースにクエリ データを格納する代わりに、リレーショナル データベースに対してクエリを直接実行する場合は、ROLAP を使用するようにソリューションを構成できます。  
  

  
 既定以外のストレージ モードを使用する場合は、優れたパフォーマンスを実現するようにメモリ管理および IO 設定を調整できます。 詳細については、「 [Analysis Services のサーバー プロパティ](../../../analysis-services/server-properties/server-properties-in-analysis-services.md) 」をご覧ください。  
  
## <a name="command-line-setup"></a>コマンド ライン セットアップ  
 SQL Server セットアップにはサーバー モードを指定するパラメーター (**ASSERVERMODE**) があります。 次の例は、Analysis Services を表形式サーバー モードでインストールするコマンド ライン セットアップを示しています。  
  
```  
  
Setup.exe /q /IAcceptSQLServerLicenseTerms /ACTION=install /FEATURES=AS /ASSERVERMODE=TABULAR /INSTANCENAME=ASTabular /INDICATEPROGRESS /ASSVCACCOUNT=<DomainName\UserName> /ASSVCPASSWORD=<StrongPassword> /ASSYSADMINACCOUNTS=<DomainName\UserName>   
```  
  
 **INSTANCENAME** は 17 文字未満にする必要があります。  
  
 プレースホルダー アカウント値はすべて、有効なアカウントおよびパスワードに置き換える必要があります。  
  
 **ASSERVERMODE** では、大文字と小文字が区別されます。  値はすべて大文字で指定する必要があります。 次の表に、 **ASSERVERMODE**の有効な値を示します。  
  
|値|説明|  
|-----------|-----------------|  
|TABULAR|これが既定値です。 設定しない場合**ASSERVERMODE**、表形式モードで、サーバーがインストールされます。|
|MULTIDIMENSIONAL|この値は省略可能です。|  
|POWERPIVOT|この値は省略可能です。 実際には、 **ROLE** パラメーターを設定した場合、サーバー モードは自動的に 1 に設定され、SharePoint のインストール時に **の** ASSERVERMODE [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] が省略可能になります。 詳細については、「 [コマンド プロンプトからの Power Pivot のインストール](http://msdn.microsoft.com/7f1f2b28-c9f5-49ad-934b-02f2fa6b9328)」を参照してください。|  
  
  
## <a name="see-also"></a>参照  
 [Analysis Services インスタンスのサーバー モードの決定](../../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)   
 [テーブル モデリング](https://msdn.microsoft.com/library/hh212945(v=sql.110).aspx)  
  
  
