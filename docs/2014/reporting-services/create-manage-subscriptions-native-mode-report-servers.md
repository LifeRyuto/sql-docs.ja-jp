---
title: ネイティブ モード レポート サーバーのサブスクリプションの作成と管理 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [Reporting Services], managing
ms.assetid: 7f46cbdb-5102-4941-bca2-5e0ff9012c6b
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 44bf77f23724f51ddc75f708e5663b43e607df0e
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56023913"
---
# <a name="create-and-manage-subscriptions-for-native-mode-report-servers"></a>ネイティブ モード レポート サーバーのサブスクリプションの作成と管理
  このセクションでは、サブスクリプションの処理、管理、および制御について説明します。 サブスクリプションの管理は、標準のサブスクリプションとデータ ドリブン サブスクリプションで異なります。 標準のサブスクリプションは、通常、ユーザーが所有および管理します。 一方、データ ドリブン サブスクリプションは、通常、レポート サーバー管理者が作成およびメンテナンスします。  
  
 サブスクリプション機能および配信機能は、既定で使用できます (電子メールの配信は構成しないと使用できません)。 既定の配信拡張機能には、レポート サーバーの電子メールおよびファイル共有の配信が含まれます。 カスタム配信拡張機能を作成またはインストールしない限り、ネイティブ モードのレポート サーバー上のサブスクリプションに使用できる配信方法は、これらの既定の配信拡張機能のみとなります。  
  
## <a name="permissions-for-subscribing-to-reports-on-a-native-mode-report-server"></a>ネイティブ モードのレポート サーバーからレポートをサブスクライブするための権限  
 ロールの使用方法に応じて、異なるロールのサブスクリプション タスクを有効または無効にすることにより、選択したユーザー グループにサブスクリプション機能を指定できます。 サブスクリプション機能をユーザーが使用するには、以下の 2 つのタスクを使用します。  
  
-   "個別のサブスクリプションを管理" タスクでは、ユーザーが特定のレポートのサブスクリプションを作成、変更、および削除できます。 定義済みのロールである閲覧者ロールとレポート ビルダー ロールには、このタスクが含まれています。 このタスクを含むロールの割り当てを使用すると、ユーザーは自分が作成するサブスクリプションのみを管理できます。  
  
-   "すべてのサブスクリプションを管理" タスクでは、ユーザーがすべてのサブスクリプションにアクセスしてそれらを変更できます。 このタスクは、データ ドリブン サブスクリプションを作成する場合に必要です。 定義済みのロールでは、コンテンツ マネージャー ロールにのみ、このタスクが含まれます。  
  
## <a name="disabling-subscriptions"></a>サブスクリプションの無効化  
 ユーザーがサブスクリプションを作成できないようにするには、ロールから "個別のサブスクリプションを管理" タスクをオフにします。 このタスクを削除すると、[サブスクリプション] ページは使用できなくなります。 レポート マネージャーでは、[個人用サブスクリプション] ページには、既にサブスクリプションが含まれていても、何も表示されません (このページは削除できません)。 サブスクリプション関連タスクを削除すると、ユーザーはサブスクリプションを作成および変更できなくなりますが、既存のサブスクリプションは削除されません。 既存のサブスクリプションは、それらを削除するまでの実行を継続します。 サブスクリプションを削除する方法についての詳細については、[Create, Modify, and 標準サブスクリプションの削除&#40;Reporting Services ネイティブ モードの&#41;](subscriptions/create-and-manage-subscriptions-for-native-mode-report-servers.md)を参照してください。  
  
 サブスクリプションのレポート サーバーで処理を無効にするには設定、`ScheduleEventsAndReportDeliveryEnabled`プロパティを`False`で、 **Reporting Services のセキュリティ構成**のファセット[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]ポリシー ベースの管理。 この場合、スケジュールされている処理は一切実行されません。 レポート サーバーのサブスクリプション処理だけを無効にすることはできません。  
  
 レポート サーバーで処理されているサブスクリプションをキャンセルする方法については、[を実行しているプロセスを管理する](subscriptions/manage-a-running-process.md)を参照してください。  
  
## <a name="disabling-delivery-extensions"></a>配信拡張機能の無効化  
 レポート サーバーにインストールされたすべての配信拡張機能は、特定のレポートのサブスクリプションを作成する権限を持つユーザーが使用できます。 使用できる配信拡張機能は次のとおりです。自動的に構成されます。  
  
-   Windows ファイル共有  
  
-   SharePoint ライブラリ (SharePoint 統合モードのレポート サーバーと統合されている SharePoint サイトからのみ使用可能)  
  
 電子メール配信は使用前に構成する必要があります。 構成が済んでいない場合、使用できません。 詳細については、[レポート サーバー電子メール配信用に構成&#40;SSRS 構成マネージャー&#41;](../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)を参照してください。  
  
 特定の拡張機能を無効にするには、RSReportServer.config ファイルから拡張機能のエントリを削除します。 詳細については、[RSReportServer Configuration File](report-server/rsreportserver-config-configuration-file.md)と[レポート サーバー電子メール配信用に構成&#40;SSRS 構成マネージャー&#41;](../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)を参照してください。  
  
 配信拡張機能の削除後は、この機能はレポート マネージャーまたは SharePoint サイトで使用できなくなります。 配信拡張機能を削除すると、サブスクリプションが無効になることがあります。 配信拡張機能を削除する前に、このようなサブスクリプションを削除するか、または別の配信拡張機能を使用するように構成する必要があります。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [個人用サブスクリプションを使用する](subscriptions/use-my-subscriptions-native-mode-report-server.md)  
 [個人用サブスクリプション] ページを使用して、所有するサブスクリプションを管理する方法を説明します。  
  
 [レポートとサブスクリプションの処理を一時停止する](subscriptions/disable-or-pause-report-and-subscription-processing.md)  
 レポートのロールの割り当てを使用して、レポート サーバーのリソースを無効にするなど、処理を一時停止するさまざまな方法について説明します。  
  
 [レポートの配信を制御する](../../2014/reporting-services/control-report-distribution.md)  
 レポートの配信を制御するために使用する構成設定および配信オプションについて説明します。  
  
 [Reporting Services のサブスクリプションを監視する](subscriptions/monitor-reporting-services-subscriptions.md)  
 サブスクリプションが成功したか失敗したかを判断する方法、および既存のサブスクリプションに対するレポート変更の影響について説明します。  
  
## <a name="see-also"></a>参照  
 [作成、変更、および標準のサブスクリプションを削除&#40;Reporting Services のネイティブ モード&#41;](subscriptions/create-and-manage-subscriptions-for-native-mode-report-servers.md)  
  
  
