---
title: ジョブの開始 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], starting
- SQL Server Agent jobs, starting
- starting jobs
ms.assetid: cec9f7f7-d0a7-4239-9dc5-a69c011ebaa0
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6c375c8776f7c33b445676e45ce70839353d469f
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/13/2018
ms.locfileid: "53376624"
---
# <a name="start-a-job"></a>Start a Job
  このトピックでは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、[!INCLUDE[tsql](../../includes/tsql-md.md)]、または SQL Server 管理オブジェクトを使用して、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブの実行を開始する方法について説明します。  
  
 ジョブとは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントで実行される特定の一連の処理のことです。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブは、1 つのローカル サーバーで実行することも、複数のリモート サーバーで実行することもできます。  
  
-   **作業を開始する準備:**  
  
     [Security](#Security)  
  
-   **ジョブを開始する方法:**  
  
     [SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [SQL Server 管理オブジェクト](#SMO)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Security"></a> セキュリティ  
 詳細については、「 [SQL Server エージェントのセキュリティの実装](implement-sql-server-agent-security.md)」をご覧ください。  
  
##  <a name="SSMS"></a> SQL Server Management Studio の使用  
  
#### <a name="to-start-a-job"></a>ジョブを開始するには  
  
1.  **オブジェクト エクスプローラー** で、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスに接続し、そのインスタンスを展開します。  
  
2.  **[SQL Server エージェント]** を展開し、 **[ジョブ]** を展開します。 ジョブの開始方法に応じて、次のいずれかを行います。  
  
    -   単一のサーバーまたはターゲット サーバー上で作業を行っている場合、またはマスター サーバー上でローカル サーバー ジョブを実行している場合、開始するジョブを右クリックして、**[ジョブの開始]** をクリックします。  
  
    -   複数のジョブを開始するには、 **[ジョブの利用状況モニター]** を右クリックし、 **[ジョブの利用状況の表示]** をクリックします。 ジョブの利用状況モニターでは、複数のジョブを選択し、選択内容を右クリックして、 **[ジョブの開始]** をクリックできます。  
  
    -   マスター サーバー上で作業を行っていて、すべての対象サーバーで同時にジョブを実行する場合、開始するジョブを右クリックし、 **[ジョブの開始]** をクリックします。次に、 **[すべての対象サーバーで開始]** をクリックします。  
  
    -   マスター サーバー上で作業を行っていて、ジョブの対象サーバーを指定する場合、開始するジョブを右クリックし、 **[ジョブの開始]** をクリックします。次に、 **[特定の対象サーバーで開始]** をクリックします。 **[ダウンロード命令の通知]** ダイアログ ボックスの **[特定の対象サーバー]** チェック ボックスをオンにし、このジョブが実行される各対象サーバーを選択します。  
  
##  <a name="TSQL"></a> Transact-SQL の使用  
  
#### <a name="to-start-a-job"></a>ジョブを開始するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。  
  
    ```  
    -- starts a job named Weekly Sales Data Backup.    
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_start_job N'Weekly Sales Data Backup' ;  
    GO  
    ```  
  
 詳細については、「[sp_start_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-start-job-transact-sql)」をご覧ください。  
  
##  <a name="SMO"></a> SQL Server 管理オブジェクトの使用  
 **ジョブを開始するには**  
  
 Visual Basic、Visual C#、PowerShell などのプログラミング言語で `Start` クラスの `Job` メソッドを呼び出します。 詳細については、「 [SQL Server 管理オブジェクト (SMO) プログラミング ガイド](https://msdn.microsoft.com/library/ms162169.aspx)」を参照してください。  
  
  
