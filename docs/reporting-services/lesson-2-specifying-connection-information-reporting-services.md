---
title: レッスン 2:接続情報の指定 (Reporting Services) | Microsoft Docs
ms.date: 05/23/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.assetid: 54405a3a-d7fa-4d95-8963-9aa224e5901e
author: markingmyname
ms.author: maghan
ms.openlocfilehash: da47a0fd587d48dd9d932504d6a5cd45d0d54664
ms.sourcegitcommit: 31800ba0bb0af09476e38f6b4d155b136764c06c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2019
ms.locfileid: "56294700"
---
# <a name="lesson-2-specifying-connection-information-reporting-services"></a>レッスン 2:接続情報の指定 (Reporting Services)
レッスン 1 でチュートリアル プロジェクトに [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] のページ分割されたレポートを追加したら、ここでリレーショナル データベース、多次元データベース、その他のリソースのデータにアクセスするためにレポートで使用される接続情報である*データ ソース* を定義する必要があります。  
  
このレッスンでは、[!INCLUDE[ssSampleDBAdventureworks2014_md](../includes/sssampledbadventureworks2014-md.md)] サンプル データベースをデータ ソースとして使用します。 このチュートリアルでは、ローカル コンピューターにインストールされた既定の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] インスタンスにこのデータベースが配置されているものとします。  
  
### <a name="to-set-up-a-connection"></a>接続を設定するには  
  
1.  **レポート データ** ペインで、**[新規]** をクリックし、**[データ ソース]** をクリックします。  
**レポート データ** ペインが表示されていない場合は、 **[表示]** メニューの **[レポート データ]** をクリックします。  

    ![ssrs-table-tutorial-2-new-data-source](../reporting-services/media/ssrs-table-tutorial-2-new-data-source.png)
  
   2.  **[名前]** に、「 *AdventureWorks2014*」と入力します。  
  
3.  **[埋め込み接続]** が選択されていることを確認します。  
  
4.  **[種類]** で **[Microsoft SQL Server]** を選択します。  
  
5.  **[接続文字列]** に次を入力します。  
  
    ```  
    Data source=localhost; initial catalog=AdventureWorks2014  
    ```  
  
     この接続文字列は、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]、レポート サーバー、および [!INCLUDE[ssSampleDBAdventureworks2014_md](../includes/sssampledbadventureworks2014-md.md)] データベースがすべてローカル コンピューターにインストールされていることと、ユーザーが [!INCLUDE[ssSampleDBAdventureworks2014_md](../includes/sssampledbadventureworks2014-md.md)] データベースにログオンする権限を持っていることが前提となります。 AdventureWorks2014 データベースがローカル コンピューターにない場合、接続文字列を変更し、*loclahost* をデータベース サーバー インスタンスの名前に置き換えます。
  
     >[!NOTE]  
    >[!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Advanced Services または名前付きインスタンスを使用している場合は、接続文字列にインスタンス情報を含める必要があります。  
    >  
    >`Data source=localhost\SQLEXPRESS; initial catalog=AdventureWorks2014`  
    >  
    >接続文字列の詳細については、次を参照してください。[Reporting Services でのデータ接続、データ ソース、および接続文字列](../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)  
     
  
6.  左ペインで **[資格情報]** をクリックし、 **[Windows 認証 (統合セキュリティ) を使用する]** をクリックします。  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)] データ ソース **AdventureWorks2014** が **レポート データ** ペインに追加されます。  
![ssrs_adventureworks_datasource](../reporting-services/media/ssrs-adventureworks-datasource.png)  
## <a name="next-task"></a>次の作業  
[!INCLUDE[ssSampleDBAdventureworks2014_md](../includes/sssampledbadventureworks2014-md.md)] サンプル データベースへの接続が正常に定義されました。 次に、レポートを作成します。 「[レッスン 3:テーブル レポートのデータセットの定義 &#40;Reporting Services&#41;](../reporting-services/lesson-3-defining-a-dataset-for-the-table-report-reporting-services.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
[Reporting Services でのデータ接続、データ ソース、および接続文字列](../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)  
  
  
  

