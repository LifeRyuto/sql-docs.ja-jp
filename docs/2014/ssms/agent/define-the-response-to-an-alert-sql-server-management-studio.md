---
title: 警告への応答の定義 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, alerts
- alerts [SQL Server], responding to
- responding to alerts
ms.assetid: c86ca6eb-c59f-46e9-bc32-d474e7c3b170
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6ac3e9ee443f0c10a39128fc1d6aab6813ec4f4d
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52795864"
---
# <a name="define-the-response-to-an-alert-sql-server-management-studio"></a>警告への応答の定義 (SQL Server Management Studio)
  このトピックでは、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)] を使用して、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの警告に対して [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がどのように応答するかを定義する方法について説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [Security](#Security)  
  
-   **警告に対する応答を定義する方法:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   今後のバージョンの **では、** エージェントからポケットベル オプションと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] net send [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]オプションが削除される予定です。 新しい開発作業では、これらの機能の使用を避け、現在これらの機能を使用しているアプリケーションは修正するようにしてください。  
  
-   SQL Server エージェントは、データベース メールを使用して、電子メールおよびポケットベルによる通知をオペレーターへ送信するように構成する必要があります。 詳細については、「 [オペレーターへの警告の割り当て](assign-alerts-to-an-operator.md)」を参照してください。  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] は、ジョブを簡単に管理できるグラフィカルなツールです。ジョブのインフラストラクチャを作成し、管理するには、このツールを使用することをお勧めします。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 警告に対する応答を定義できるのは、 **sysadmin** 固定サーバー ロールのメンバーだけです。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-define-the-response-to-an-alert"></a>警告に対する応答を定義するには  
  
1.  **オブジェクト エクスプローラー**で、応答を定義する警告を格納するサーバーをプラス記号をクリックして展開します。  
  
2.  プラス記号をクリックして **[SQL Server エージェント]** を展開します。  
  
3.  プラス記号をクリックして **[警告]** フォルダーを展開します。  
  
4.  応答を定義する警告を右クリックし、**[プロパティ]** を選択します。  
  
5.  [_alert_name_ **警告のプロパティ**] ダイアログ ボックスで、**[ページの選択]** から **[応答]** を選択します。  
  
6.  **[ジョブの実行]** チェック ボックスをオンにし、 **[ジョブの実行]** チェック ボックスの下に表示されている一覧から、警告の発生時に実行するジョブを選択します。 **[新しいジョブ]** をクリックすることで、新しいジョブを作成できます。 **[ジョブの表示]** をクリックすると、ジョブに関するより詳しい情報を表示できます。 **[新しいジョブ]** ダイアログ ボックスと [**ジョブのプロパティ** _job_name_] ダイアログ ボックスで使用できるオプションの詳細については、「[ジョブの作成](create-a-job.md)」と「[ジョブの表示](view-a-job.md)」を参照してください。  
  
7.  警告がアクティブになったときにオペレーターに通知する場合は、 **[オペレーターに通知する]** チェック ボックスをオンにします。 **演算子一覧**、オペレーターまたはオペレーターに通知するための次の方法の 1 つ以上選択します。**電子メール**、**ポケットベル**、または**Net Send**します。 **[新しいオペレーター]** をクリックすることで、新しいオペレーターを作成できます。 **[オペレーターの表示]** をクリックすることで、オペレーターに関するより詳しい情報を表示できます。 **[新しいオペレーター]** ダイアログ ボックスと **[オペレーターのプロパティの表示]** ダイアログ ボックスで使用できるオプションの詳細については、「 [Create an Operator](create-an-operator.md) 」と「 [View Information About an Operator](view-information-about-an-operator.md)」を参照してください。  
  
8.  完了したら、 **[OK]** をクリックします。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-define-the-response-to-an-alert"></a>警告に対する応答を定義するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。  
  
    ```  
    -- adds an e-mail notification for Test Alert.  
    -- assumes that Test Alert already exists and that Fran??ois Ajenstat is a valid operator name   
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_notification  
     @alert_name = N'Test Alert',  
     @operator_name = N'Fran??ois Ajenstat',  
     @notification_method = 1 ;  
    GO  
    ```  
  
 詳細については、[sp_add_notification &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql)を参照してください。  
  
  
