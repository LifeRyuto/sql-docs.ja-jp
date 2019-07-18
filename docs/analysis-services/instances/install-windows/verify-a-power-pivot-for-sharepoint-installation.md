---
title: For SharePoint のインストール verify a Power Pivot |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ppvt-sharepoint
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f047593657806b872aafdda802c9c85ac4526b56
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68209471"
---
# <a name="verify-a-power-pivot-for-sharepoint-installation"></a>Power Pivot for SharePoint インストールの確認
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  SharePoint ファームにインストールした [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint インスタンスは、SharePoint サーバーの全体管理から管理されます。 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] のサーバー コンポーネントと機能が使用可能になっているかどうかは、少なくとも、サーバーの全体管理および SharePoint サイトのページを調べれば確認できます。 インストールを完全に確認するには、SharePoint にパブリッシュでき、ライブラリからアクセスできる [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] ブックが必要になります。 テスト時には、既に [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] データが含まれているサンプル ブックをパブリッシュし、それを使用して SharePoint 統合が正しく構成されているかどうかを確認できます。  

  
##  <a name="verifyinstall"></a> 全体管理統合の確認  
 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] のサーバーの全体管理との統合を確認するには、次の操作を行います。  
  
1.  [スタート] メニューの **[すべてのプログラム]** をクリックし、Microsoft SharePoint 2016 製品または Microsoft SharePoint 2013 製品を開いて、 **[SharePoint 2016 サーバーの全体管理] または [SharePoint 2013 サーバーの全体管理]** をクリックします。  
  
2.  ユーザー名とパスワードを入力し、 **[OK]** をクリックします。  
  
     サーバーの全体管理を開くたびにユーザー名とパスワードを入力せずに済むように、ブラウザーの設定を変更することもできます。 サーバーの全体管理を信頼済みサイトとして追加するには、次の操作を行います。  
  
    1.  Internet Explorer で、[ツール] メニューの **[インターネット オプション]** をクリックします。  
  
    2.  [セキュリティ] タブの **[セキュリティ設定を表示または変更するゾーンを選択してください。]** セクションで、[信頼済みサイト] をクリックし、[サイト] をクリックします。  
  
    3.  **[このゾーンのサイトにはすべてサーバーの確認 (https:) を必要とする]** チェック ボックスをオフにします。  
  
    4.  **[次の Web サイトをゾーンに追加する]** に、サイトの URL を入力し、 **[追加]** をクリックします。  
  
    5.  **[閉じる]** をクリックし、 **[OK]** をクリックします。  
  
        > [!NOTE]  
        >  SharePoint のインストールに関するドキュメントには、プロキシ サーバーのエラーを解決する手順や、更新プログラムをダウンロードしてインストールできるように Internet Explorer セキュリティ強化の構成を無効にする手順も示されています。 詳細については、Microsoft Web サイトの「 **SQL Server を使用する単一サーバーを展開する (SharePoint Server 2010)** 」の「 [追加のタスクの実行](http://go.microsoft.com/fwlink/?LinkId=177754) 」を参照してください。  
  
3.  サーバーの全体管理で、[システム設定] の **[ファーム機能の管理]** をクリックします。  
  
4.  **[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 統合機能** が **[アクティブ]** になっていることを確認します。  
  
5.  サーバーの全体管理で、[システム設定] の **[サーバーのサービスの管理]** をクリックします。  
  
6.  **[SQL Server [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] システム サービス]** が開始されていることを確認します。  
  
     複数サーバーの SharePoint ファームでは、表示しているサーバーを変更して、 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] を展開したすべてのサーバーが実行されていることを検証する必要がある場合があります。  
  
7.  サーバーの全体管理で、[アプリケーション構成の管理] の **[サービス アプリケーションの管理]** をクリックします。  
  
8.  **[既定の [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] サービス アプリケーション]** をクリックして、このアプリケーションの [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 管理ダッシュボードを開きます。 最初に使用するときは、ダッシュボードの読み込みに数分かかります。  
  
     または、 **[既定の [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] サービス アプリケーション]** の横の空白部分をクリックして行を選択し、 **[プロパティ]** をクリックしてこのサービス アプリケーションの構成設定を表示します。 構成設定とアプリケーション プロパティの両方を修正して、サーバーの構成を変更できます。 これらの設定の詳細については、「 [サーバーの全体管理での Power Pivot サービス アプリケーションの作成および構成](../../../analysis-services/power-pivot-sharepoint/create-and-configure-power-pivot-service-application-in-ca.md)」を参照してください。  
  
## <a name="verify-integration-at-the-site-level"></a>サイト レベルでの統合の確認  
 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] の SharePoint サイトとの統合を確認するには、次の操作を行います。  
  
1.  ブラウザーで、作成した Web アプリケーションを開きます。 既定値を使用した場合は、 http:// を指定できます\<コンピューター名 >、URL アドレス。  
  
2.  [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] のデータ アクセス機能とデータ処理機能がアプリケーションで使用可能になっていることを確認します。 そのためには、 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)]から提供されるライブラリ テンプレートがあるかどうかを確認します。  
  
    1.  **[サイト コンテンツ]** を選択します。  
  
    2.  アプリの一覧には、 **[データ フィード ライブラリ]** と **[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] ギャラリー**が表示されます。 これらのライブラリ テンプレートは [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 機能によって提供されるものであり、機能が正しく統合されている場合に [ライブラリ] に表示されます。  
  
## <a name="verify-data-access-on-the-server"></a>サーバーでのデータ アクセスの確認  
 サーバーで [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] データ アクセスを確認するには、次の操作を行います。  
  
1.  Reporting Services のチュートリアルにある Picnic のデータ サンプルを[ダウンロード](http://go.microsoft.com/fwlink/?LinkID=219108) します。 このダウンロードに含まれるサンプル ブックを使用して、 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] データのアクセスを確認します。 ファイルを抽出します。  
  
2.  Excel ブック (.xlsx) を Shared Documents にアップロードします。 ブックに埋め込み [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] データが含まれます。  
  
3.  ドキュメントをクリックしてライブラリから開きます。  
  
4.  ブックの上部にあるスライサーまたはフィルターをクリックします。 このブックのスライサーは、月、色、および種類です。 スライサーをクリックすると、 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] クエリが開始され、サーバーが動作することを確認できます。 サーバーは [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] データをバックグラウンドで読み込んで結果を返します。  
  
5.  ライブラリに戻ります。 ブックの右側にある下矢印を選択して、 **[Power View の起動]** をクリックします。 この手順により、Reporting Services で [!INCLUDE[ssCrescent](../../../includes/sscrescent-md.md)] 機能が動作することを確認します。 Reporting Services をインストールしていない場合は、この手順は省略します。  
  
     次の手順で、Management Studio のサーバーに接続して、データの読み込みとキャッシュが行われたことを確認します。  
  
6.  [スタート] メニューの [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)] プログラム グループから SQL Server Management Studio を起動します。 このツールがサーバーにインストールされていない場合は、以降の手順はスキップし、最後の手順でキャッシュされたファイルがあるかどうかを確認します。  
  
7.  [サーバーの種類] で **[Analysis Services]** を選択します。  
  
8.  サーバー名 で次のように入力します **\<サーバー名 > \powerpivot**ここで、 **\<サーバー名 >** されているコンピューターの名前を指定します、 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint。インストールします。  
  
9. **[接続]** をクリックします。 これにより、Analysis Services サーバーが使用可能であることを確認します。  
  
10. オブジェクト エクスプローラーで、 **[データベース]** をクリックして、読み込まれた [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] データ ファイルの一覧を確認します。  
  
11. コンピューターのファイル システムのフォルダーで、ファイルがディスクにキャッシュされているかどうかを確認します。 キャッシュされたファイルが存在していれば、配置が機能していることの確認になります。 ファイル キャッシュを表示するには、 [!INCLUDE[ssInstallPathVar](../../../includes/ssinstallpathvar-md.md)]MSAS13.POWERPIVOT\OLAP\Backup\Sandboxes\Default [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] サービス アプリケーションのフォルダーに移動します。 キャッシュされた各データベースは、名前が一意になるように、GUID ベースの名前付け規則を使用してそれぞれのフォルダーに格納されます。  
  
  
