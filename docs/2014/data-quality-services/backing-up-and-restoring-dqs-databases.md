---
title: DQS データベースのバックアップと復元 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: f3091f62-2234-4a80-a615-cf14c2a1da85
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: c139e5e9487dc703b3a24b159e17c7495fb88c3e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62755786"
---
# <a name="backing-up-and-restoring-dqs-databases"></a>DQS データベースのバックアップと復元
  このトピックでは、DQS データベースのバックアップと復元を行う方法について説明します。  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Prerequisites"></a> 前提条件  
  
-   DQS サーバーのインストール中に入力したデータベース マスター キーのパスワードを知っている必要があります。  
  
-   DQS で実行中のアクティビティまたはプロセスがないことを確認します。 これは **[アクティビティ監視]** 画面を使用して確認できます。 この画面の操作の詳細については、「 [Monitor DQS Activities](../../2014/data-quality-services/monitor-dqs-activities.md)」を参照してください。  
  
-   DQS サーバーにログオンしているユーザーがないことを確認します。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
  
-   バックアップおよび復元操作を実行するには、使用する Windows ユーザー アカウントが、SQL Server インスタンスの sysadmin 固定サーバー ロールのメンバーであることが必要です。  
  
-   DQS の実行中のアクティビティを終了させたり実行中のプロセスを停止させたりするには、DQS_MAIN データベースの dqs_administrator ロールが必要です。  
  
##  <a name="BackupRestore"></a> DQS データベースのバックアップと復元  
  
1.  Microsoft SQL Server Management Studio を起動し、適切な SQL Server インスタンスに接続します。  
  
2.  オブジェクト エクスプローラーで、 **[データベース]** ノードを展開します。  
  
3.  DQS_STAGING_DATA データベースをバックアップします。 SQL Server データベースのバックアップ手順について詳しくは、「[データベースの完全バックアップの作成 &#40;SQL Server&#41;](../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)」をご覧ください。  
  
4.  DQS_PROJECTS データベースをバックアップします。  
  
5.  DQS_MAIN データベースをバックアップします。  
  
6.  SQL Server の現在のインスタンスから切断し、データベースを復元する SQL Server インスタンスに接続します。  
  
7.  DQS_MAIN データベースを復元します。 SQL Server データベースを復元する手順については、次を参照してください。[データベース バックアップを復元&#40;SQL Server Management Studio&#41;](../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md)します。  
  
8.  DQS_PROJECTS データベースを復元します。  
  
9. DQS_STAGING_DATA データベースを復元します。  
  
10. オブジェクト エクスプローラーでサーバーを右クリックし、 **[新しいクエリ]** をクリックします。  
  
11. クエリ エディター ウィンドウに次の SQL ステートメントをコピーし、*\<PASSWORD>* を DQS サーバーのインストール中に入力したデータベース マスター キーのパスワードで置き換えます。  
  
    ```  
    USE [DQS_MAIN]  
    GO  
    EXECUTE [internal_core].[RestoreDQDatabases] '<PASSWORD>'  
    GO  
  
    ```  
  
12. F5 キーを押してステートメントを実行します。 **[結果]** ペインを確認してステートメントが正常に実行されたことを確認します。  
  
## <a name="see-also"></a>参照  
 [DQS データベースの管理](../../2014/data-quality-services/manage-dqs-databases.md)  
  
  
