---
title: SharePoint ライブラリへのレポートのパブリッシュ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- deploying [Reporting Services], reports in SharePoint integrated mode
- SharePoint integration [Reporting Services], publishing to a library
- publishing reports [Reporting Services], to a SharePoint library
ms.assetid: 3f6dfc28-50d8-4231-bd25-871b5f77cce6
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: fbc55765d8955c47f677c70968b33b35dfa641a1
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56037453"
---
# <a name="publish-a-report-to-a-sharepoint-library"></a>SharePoint ライブラリへのレポートのパブリッシュ
  SharePoint 統合用に構成されている SharePoint サイトにレポートをパブリッシュするには、レポート デザイナーでレポート プロジェクトのプロパティを設定する必要があります。 プロジェクトのプロパティでは、サーバー、レポート、および共有データ ソースへの参照はすべて、完全修飾 URL で指定する必要があります。 レポート定義では、サブレポートや詳細レポートへの参照、および Web ベースの画像などのリソースへの参照はすべて完全修飾 URL で指定する必要があります。  
  
 プロジェクトにプロパティを設定するには、SharePoint サイトの **メンバー** 権限または **所有者** 権限が必要です。 詳細については、「 [SharePoint モードのレポート サーバー上のパブリッシュされたレポート アイテムの URL の例 (SSRS)](../tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md)」を参照してください。  
  
### <a name="to-publish-a-report-to-a-sharepoint-site"></a>レポートを SharePoint サイトにパブリッシュするには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で既存または新規のレポート サーバー プロジェクトを開きます。  
  
2.  **[プロジェクト]** メニューの **[プロパティ]** をクリックします。 _[\<プロジェクト>_**プロパティ ページ]** ダイアログ ボックスが開きます。  
  
3.  **[構成]** ボックスで、レポートのビルドとパブリッシュに使用するソリューション ビルド構成の名前を選択します。 現在の構成は **[アクティブ]** (*\<configuration>*) として表示されます。  
  
4.  プロジェクトの共有データ ソースをパブリッシュし、以前にパブリッシュされた共有データ ソースを上書きするには、 **[OverwriteDataSources]** を **[True]** に設定します。  
  
5.  (省略可能)**TargetDataSourceFolder**、SharePoint ライブラリまたはライブラリ フォルダーの URL を入力 (たとえば、  *http://TestServer/TestSite/Documents/DataSources)* します。  
  
     値を指定しない場合は、 **[TargetReportFolder]** の値が使用されます。  
  
6.  **TargetReportFolder**、ライブラリまたはライブラリ フォルダーの URL を入力 (たとえば、  *http://TestServer/TestSite/Documents/Reports)* します。  
  
7.  **[TargetServerURL]** に、SharePoint トップレベル サイトまたはサブサイトの URL を入力します。 既定のトップレベル サイトが使用されるサイトを指定しない場合 (たとえば、 *http://servername*、 *http://servername/site*、または*http://servername/site/subsite*)。  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
9. ソリューション エクスプローラーで、パブリッシュするレポートを右クリックし、 **[配置]** をクリックします。 これで、 **[TargetReportFolder]** で指定した場所にレポートがパブリッシュされます。 配置エラーは出力ウィンドウに表示されます。  
  
## <a name="see-also"></a>参照  
 [[プロパティ ページ] ダイアログ ボックス](../tools/project-property-pages-dialog-box.md)   
 [配置プロパティを設定する &#40;Reporting Services&#41;](../tools/set-deployment-properties-reporting-services.md)   
 [レポート サーバーへのレポートのパブリッシュ](publishing-reports-to-a-report-server.md)   
 [SharePoint モードのレポート サーバー上のパブリッシュされたレポート アイテムの URL の例 (SSRS)](../tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md)   
 [レポートで Office Data Connection (.odc) を使用する (Reporting Services の SharePoint 統合モード)](../report-data/use-an-office-data-connection-odc-with-reports.md)  
  
  
