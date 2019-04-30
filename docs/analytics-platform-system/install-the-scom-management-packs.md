---
title: Analytics Platform System の SCOM 管理パックのインストール |Microsoft Docs
description: 以下の手順をダウンロードして SQL Server PDW の System Center Operations Manager (SCOM) 管理パックをインストールします。 管理パックが SCOM から SQL Server PDW の監視に必要です。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: f0acfa636a3432dcffb18cfec57ee7625c1eb01b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63215510"
---
# <a name="install-sql-server-operations-manager-scom-management-packs-for-analytics-platform-system"></a>Analytics Platform System の SQL Server Operations Manager (SCOM) 管理パックをインストールします。
以下の手順をダウンロードして SQL Server PDW の System Center Operations Manager (SCOM) 管理パックをインストールします。 管理パックが SCOM から SQL Server PDW の監視に必要です。  
  
## <a name="BeforeBegin"></a>はじめに  
**前提条件**  
  
System Center Operations Manager は、インストールして実行する必要があります。 SQL Server PDW 2012 では、System Center Operations Manager 2007 R2、System Center Operations Manager 2012、または System Center Operations Manager 2012 service pack 1 が必要です。  
  
## <a name="Step1"></a>手順 1:管理パックをダウンロードします。  
APS PDW ワークロードでは、ダウンロード、 [Microsoft Analytics Platform System 用の System Center 管理パック](https://go.microsoft.com/fwlink/?LinkId=396857)します。  
  
アプライアンスの管理、ダウンロード、 [SQL Server アプライアンス ベースの管理パック](https://www.microsoft.com/download/details.aspx?displaylang=en&id=11436)します。  
  
古いバージョンの PDW AP せず、ダウンロード、[System Center Monitoring Pack for Microsoft SQL Server 2012 並列データ ウェアハウス アプライアンス](https://go.microsoft.com/fwlink/p/?LinkId=282661)します。  
  
<!-- MISSING LINKS - For the HDInsight workload, download the [System Center Management Pack for HDInsight](https://go.microsoft.com/fwlink/?LinkId=390208).  -->
  
## <a name="Step2"></a>手順 2:管理パックをインストールします。  
  
### <a name="install-the-sql-server-appliance-base-management-pack"></a>SQL Server アプライアンス ベースの管理パックをインストールします。  
  
1.  インストールを実行するには、ダウンロードした SQL Server アプライアンス ベースの管理パックをダブルクリックします。  
  
2.  ライセンス条項に同意し、をクリックして**次**します。  
  
    ![ライセンス条項に同意](./media/install-the-scom-management-packs/SCOM_licnse_agrmt.png "SCOM_licnse_agrmt")  
  
3.  独自のインストール フォルダーを選択するか、既定の管理パックのインストール フォルダーを使用します。  
  
    ![インストール フォルダーの選択](./media/install-the-scom-management-packs/SCOM_licnse_agrmt2.png "SCOM_licnse_agrmt2")  
  
4.  **[インストール]** をクリックします。  
  
    ![インストールの確認](./media/install-the-scom-management-packs/SCOM_licnse_agrmt3.png "SCOM_licnse_agrmt3")  
  
5.  **[閉じる]** をクリックします。  
  
    ![[閉じる] をクリックして](./media/install-the-scom-management-packs/SCOM_licnse_agrmt4.png "SCOM_licnse_agrmt4")  
  
### <a name="install-the-monitoring-pack-for-sql-server-pdw-appliance"></a>SQL Server PDW アプライアンス用監視パックをインストールします。  
  
1.  インストールを実行するには、ダウンロードした SQL Server PDW アプライアンスの管理パックをダブルクリックします。  
  
2.  ライセンス条項に同意し、をクリックして**次**します。  
  
    ![使用許諾に同意](./media/install-the-scom-management-packs/SCOM_licnse_agmtB.png "SCOM_licnse_agmtB")  
  
3.  抽出したファイルを保持するディレクトリを選択します。 既定の管理パックのインストール フォルダーは、既定で表示されます。 既定値を選択するか、独自のインストール フォルダーを選択します。  
  
    ![インストール フォルダーの選択](./media/install-the-scom-management-packs/SCOM_licnse_agmtB1.png "SCOM_licnse_agmtB1")  
  
4.  **[インストール]** をクリックします。  
  
    ![インストールの確認](./media/install-the-scom-management-packs/SCOM_licnse_agmtB2.png "SCOM_licnse_agmtB2")  
  
5.  **[閉じる]** をクリックします。  
  
    ![インストールの完了](./media/install-the-scom-management-packs/SCOM_licnse_agmtB3.png "SCOM_licnse_agmtB3")  
  
## <a name="next-step"></a>次の手順  
管理パックをインストールしたら、次の手順に進みます。[PDW の SCOM 管理パックをインポート&#40;Analytics Platform System&#41;](import-the-scom-management-pack-for-pdw.md)します。  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
