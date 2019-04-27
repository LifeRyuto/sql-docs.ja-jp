---
title: チュートリアル:SQL Server のバックアップと復元を Windows Azure Blob ストレージ サービス |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 9e1d94ce-2c93-45d1-ae2a-2a7d1fa094c4
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 2216674bec52dd4d4800aa1b03aa4a2834667974
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62524052"
---
# <a name="tutorial-sql-server-backup-and-restore-to-windows-azure-blob-storage-service"></a>チュートリアル:SQL Server のバックアップと Windows Azure Blob ストレージ サービスへの復元
  「Windows Azure BLOB ストレージ サービスを使用した SQL Server のバックアップと復元」チュートリアルへようこそ。 このチュートリアルにより、Windows Azure BLOB ストレージ サービスへのバックアップ書き込みと Windows Azure BLOB ストレージ サービスからの復元を実行する方法について把握できます。  
  
## <a name="what-you-will-learn"></a>学習する内容  
 このチュートリアルでは、Windows ストレージ アカウント、BLOB コンテナーを作成し、ストレージ アカウントにアクセスするための資格情報の作成、BLOB サービスへのバックアップの書き込み、簡単な復元の実行を行う方法について説明します。 このチュートリアルは、次の 4 つのレッスンで構成されています。  
  
 [レッスン 1:Windows Azure ストレージ オブジェクトを作成します。](../tutorials/lesson-1-create-windows-azure-storage-objects.md)  
 このレッスンでは、Windows Azure ストレージ アカウントおよび BLOB コンテナーを作成します。  
  
 [レッスン 2:SQL Server 資格情報を作成します。](../tutorials/lesson-2-create-a-sql-server-credential.md)  
 このレッスンでは、Windows Azure ストレージ アカウントへのアクセスに使用するセキュリティ情報を格納するための資格情報を作成します。  
  
 [レッスン 3:Windows Azure Blob ストレージ サービスに対するデータベースの完全バックアップを書き込み](../tutorials/lesson-3-write-a-full-database-backup-to-the-windows-azure-blob-storage-service.md)  
 このレッスンでは、T-SQL ステートメントを実行して、Windows Azure BLOB ストレージ サービスに AdventureWorks2012 データベースのバックアップを書き込みます。  
  
 [レッスン 4:データベースの完全バックアップから復元を実行します。](../tutorials/lesson-4-perform-a-restore-from-a-full-database-backup.md)  
 このレッスンでは、T-SQL ステートメントを実行して、前のレッスンで作成したデータベース バックアップから復元します。  
  
### <a name="requirements"></a>必要条件  
 このチュートリアルを完了するには、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のバックアップと復元の概念と T-SQL 構文についての知識が必要です。 このチュートリアルを使用するには、以下のシステム要件を満たしている必要があります。  
  
-   [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] インスタンス、およびインストールされた AdventureWorks2012 データベース。  
  
     SQL Server インスタンスは、内部設置型でも、Windows Azure バーチャル マシン内に存在してもかまいません。  
  
     AdventureWorks2012 の代わりにユーザー データベースを使用し、それに応じて TSQL コマンド構文を変更できます。  
  
-   BACKUP コマンドまたは RESTORE コマンドの発行に使用するユーザー アカウントは、 **資格情報の変更** 権限を持つ **db_backup operator** データベース ロールに属している必要があります。  
  
### <a name="additional-reading"></a>その他の情報  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] バックアップに Windows Azure BLOB ストレージ サービスを使用する場合の概念やベスト プラクティスを理解するための推奨トピックを次に示します。  
  
1.  [Windows Azure BLOB ストレージ サービスを使用した SQL Server のバックアップと復元](backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)  
  
2.  [SQL Server Backup to URL に関するベスト プラクティスとトラブルシューティング](backup-restore/sql-server-backup-to-url-best-practices-and-troubleshooting.md)  
  
  
