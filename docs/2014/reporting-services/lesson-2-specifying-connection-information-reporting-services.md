---
title: レッスン 2:接続情報 (Reporting Services) の指定 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 54405a3a-d7fa-4d95-8963-9aa224e5901e
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 67336ec0829c810a087ddfdcf79628408c045a76
ms.sourcegitcommit: 31800ba0bb0af09476e38f6b4d155b136764c06c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2019
ms.locfileid: "56290180"
---
# <a name="lesson-2-specifying-connection-information-reporting-services"></a>レッスン 2:(Reporting Services) の接続情報を指定します。
  チュートリアル プロジェクトにレポートを追加した後、リレーショナル データベース、多次元データベース、その他のリソースのデータにアクセスするためにレポートで使用される接続情報である *データ ソース*を定義する必要があります。  
  
 このレッスンでは、[!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] サンプル データベースをデータ ソースとして使用します。 このチュートリアルでは、ローカル コンピューターにインストールされている既定の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] インスタンスにこのデータベースが配置されているものとします。  
  
### <a name="to-set-up-a-connection"></a>接続を設定するには  
  
1.  **レポート データ**ウィンドウで、をクリックして**新規** をクリックし、**データ ソース.**.  
  
    > [!NOTE]  
    >  **レポート データ** ペインが表示されていない場合は、 **[表示]** メニューの **[レポート データ]** をクリックします。  
  
2.  **[名前]** に「 [!INCLUDE[ssSampleDBUserInputNonLocal](../includes/sssampledbuserinputnonlocal-md.md)]」と入力します。  
  
3.  **[埋め込み接続]** が選択されていることを確認します。  
  
4.  **[種類]** で **[Microsoft SQL Server]** を選択します。  
  
5.  **[接続文字列]** に次を入力します。  
  
    ```  
    Data source=localhost; initial catalog=AdventureWorks2012  
    ```  
  
     この接続文字列は、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]、レポート サーバー、および [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] データベースがすべてローカル コンピューターにインストールされていることと、ユーザーが [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] データベースにログオンする権限を持っていることが前提となります。  
  
    > [!NOTE]  
    >  [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Advanced Services または名前付きインスタンスを使用している場合は、接続文字列にインスタンス情報を含める必要があります。  
    >   
    >  `Data source=localhost\SQLEXPRESS; initial catalog=AdventureWorks2012`  
    >   
    >  接続文字列の詳細については、次を参照してください。[データ接続、データ ソース、および Reporting Services の接続文字列](data-connections-data-sources-and-connection-strings-in-reporting-services.md)と[データ ソースのプロパティ ダイアログ ボックスの [全般]](data-source-properties-dialog-box-general.md)します。  
  
6.  左ペインで **[資格情報]** をクリックし、 **[Windows 認証 (統合セキュリティ) を使用する]** をクリックします。  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)] データ ソース[!INCLUDE[ssSampleDBnormal](../includes/sssampledbnormal-md.md)]に追加されます、**レポート データ**ウィンドウ。  
  
## <a name="next-task"></a>次の作業  
 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] サンプル データベースへの接続が正常に定義されました。 次に、レポートを作成します。 参照してください[レッスン 3。テーブル レポートのデータセットを定義する&#40;Reporting Services&#41;](lesson-3-defining-a-dataset-for-the-table-report-reporting-services.md)します。  
  
## <a name="see-also"></a>参照  
 [Reporting Services でのデータ接続、データ ソース、および接続文字列](data-connections-data-sources-and-connection-strings-in-reporting-services.md)  
  
  
