---
title: レポート サーバー データベースのアップグレード | Microsoft Docs
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- upgrading databases
- report server database
- upgrading Reporting Services
ms.assetid: 4091cf87-9d97-4048-a393-67f1f9207401
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e3ba4d9ee2e0b92617c2d2bcadae3bf87c8b5414
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66108638"
---
# <a name="upgrade-a-report-server-database"></a>レポート サーバー データベースのアップグレード
  レポート サーバー データベースは、1 台以上のレポート サーバー インスタンスの記憶域になります。 レポート サーバー データベースのスキーマは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]が新たにリリースされるたびに変更される可能性があります。そのため、使用中のレポート サーバー インスタンスのバージョンとデータベースのバージョンを一致させる必要があります。 ほとんどの場合、レポート サーバー データベースは自動的にアップグレードされます。ユーザーは何も処理する必要がありません。  
  
 **ネイティブモード:** ネイティブ[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]モードでは、レポートサーバーデータベースは、実際には "ReportServer と ReportServerTempDB" という既定の名前を持つ2つのデータベースで構成されています。  
  
 **SharePoint モード:** SharePoint [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]モードでは、実際には、レポートサーバーデータベースは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]サービスアプリケーションの各インスタンスに対して作成されるデータベースのコレクションです。  
  
## <a name="ways-to-upgrade-a-native-mode-report-server-database"></a>ネイティブ モードのレポート サーバー データベースをアップグレードする方法  
 次に、レポート サーバー データベースのアップグレード条件を示します。  
  
-   
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップは、レポート サーバーの単一のインスタンスをアップグレードします。 サービスが開始され、レポート サーバーによってデータベース スキーマのバージョンがサーバーのバージョンと一致しないことが検出されると、レポート サーバー データベース スキーマが自動的にアップグレードされます。  
  
     レポート サーバーは、サービスの開始時に、データベース スキーマのバージョンとサーバーのバージョンが一致しているかどうかを確認します。 データベース スキーマのバージョンが古い場合、レポート サーバーで必要なバージョンのスキーマに自動的にアップグレードされます。 自動アップグレードは、古いレポート サーバー データベースを復元またはアタッチした場合に特に役立ちます。 データベース スキーマのバージョンがアップグレードされたことを示すメッセージが、レポート サーバーのトレース ログ ファイルに入力されます。  
  
-   新しいバージョンのレポート サーバー インスタンスで古いバージョンのレポート サーバー データベースを使用するように選択した場合、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーは、ローカルまたはリモートのレポート サーバー データベースをアップグレードします。 この場合、アップグレード操作を事前に確認する必要があります。  
  
     
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーには、個別の [アップグレード] ボタンまたはアップグレード スクリプトが用意されていません。 
  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降では、レポート サーバー サービスの自動アップグレード機能の導入に伴って、これらの機能が廃止されました。  
  
 スキーマを更新した後で、アップグレードを以前のバージョンにロールバックすることはできません。 以前のインストールを再作成する必要が生じる場合に備えて、必ずレポート サーバー データベースをバックアップしてください。  
  
## <a name="how-the-schema-metadata-and-report-server-content-is-updated"></a>スキーマ、メタデータ、およびレポート サーバー コンテンツの更新方法  
 レポート サーバー データベースは、次の 3 段階でアップグレードされます。  
  
1.  スキーマは、セットアップとサービス開始の後、または以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーで [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ネイティブ モードのレポート サーバー データベースを選択したときに、自動的にアップグレードされます。 さらに、レポート サーバー サービスは、起動時にデータベース バージョンを確認します。 レポート サーバーは、接続先のデータベースが以前のバージョンである場合、起動時にデータベースを更新します。  
  
2.  セキュリティ記述子は、スキーマの更新後にレポート サーバー データベースを最初に使用するときにアップグレードされます。  
  
3.  パブリッシュ済みのレポートとコンパイル済みのレポート スナップショットは最初に使用するときに更新されます。 詳細については、「 [Upgrade Reports](upgrade-reports.md)」を参照してください。  
  
 レポート サーバーは、レポート サーバー データベース以外に一時データベースも使用します。 一時データベースは、レポート サーバー データベースをアップグレードするときに自動的にアップグレードされます。  
  
## <a name="permissions-required-to-upgrade-a-report-server-database"></a>レポート サーバー データベースのアップグレードに必要な権限  
 レポート サーバー データベースを含む [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] をアップグレードする場合に、不十分な権限でデータベースのアップグレードが行われると、エラー メッセージが表示されることがあります。 既定では、リモートの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスへの接続とスキーマの更新には、セットアップ プログラムを実行しているユーザーのセキュリティ トークンが使用されます。 レポート サーバー データベースをホストするデータベース サーバーの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **sysadmin** アクセス許可がある場合は、データベースのアップグレードは成功します。 同様に、リモート コンピューターのスキーマを変更する **sysadmin** アクセス許可のあるアカウントの RSUPGRADEDATABASEACCOUNT 引数と RSUPGRADEPASSWORD 引数を指定してコマンド プロンプトからセットアップを実行すると、データベースのアップグレードは正しく行われます。  
  
 しかし、リモート コンピューターのデータベースに対する **sysadmin** アクセス許可がないと、接続が拒否され、次のエラー メッセージが表示されます。  
  
 `"Setup was not able to upgrade the report server database schema. You must update the database schema manually after setup is finished. To update the schema, run the Reporting Services Configuration Manager, open the Database Setup page, re-select the database, and click Apply. The database will be upgraded automatically."`  
  
 この時点で、レポート サーバーのプログラム ファイルはアップグレードされますが、レポート サーバー データベースは以前のバージョンの形式のままになります。 データベースを手動でアップグレードしてアップグレード プロセスを完了するまで、レポート サーバーは使用できません。  
  
#### <a name="to-upgrade-a-native-mode-database-with-scripts"></a>スクリプトを使用してネイティブ モードのデータベースをアップグレードするには  
 WMI スクリプトを使用して、レポート サーバー データベースをアップグレードできます。 詳細については、「[GenerateDatabaseUpgradeScript メソッド &#40;WMI MSReportServer_ConfigurationSetting&#41;](../wmi-provider-library-reference/configurationsetting-method-generatedatabaseupgradescript.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Reporting Services 構成マネージャー &#40;ネイティブ モード&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)   
 [レポート サーバー データベースの作成 &#40;SSRS 構成マネージャー&#41;](../../sql-server/install/create-a-report-server-database-ssrs-configuration-manager.md)   
 [データベースの変更ウィザード &#40;SSRS ネイティブモード&#41;](../../sql-server/install/change-database-wizard-ssrs-native-mode.md)   
 [Reporting Services のアップグレードと移行](upgrade-and-migrate-reporting-services.md)   
 [Reporting Services インストール &#40;ネイティブモードに移行する&#41;](migrate-a-reporting-services-installation-native-mode.md)  
  
  
