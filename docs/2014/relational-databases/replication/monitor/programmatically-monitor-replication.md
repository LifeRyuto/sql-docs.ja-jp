---
title: プログラムによるレプリケーションの監視 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- sp_replmonitorhelppublisher
- sp_replmonitorhelpmergesessiondetail
- monitoring performance [SQL Server replication], publication status
- sp_replmonitorhelpmergesession
- sp_replmonitorhelppublicationthresholds
- monitoring performance [SQL Server replication], subscription status
- monitoring performance [SQL Server replication], Transact-SQL programming
- sp_replmonitorsubscriptionpendingcmds
- sp_replmonitorchangepublicationthreshold
- transactional replication, monitoring
- sp_replmonitorhelppublication
- sp_replmonitorhelpsubscription
- monitoring performance [SQL Server replication], thresholds and warnings
- merge replication monitoring [SQL Server replication]
- snapshot replication [SQL Server], monitoring
ms.assetid: e8bf8850-8da5-4a4f-a399-64232b4e476d
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 949c8585b3886d0d3f422e76d031b390d248e9a4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62667248"
---
# <a name="programmatically-monitor-replication"></a>プログラムによるレプリケーションの監視
  レプリケーション モニターは、レプリケーション トポロジを監視するためのグラフィカル ツールです。 [!INCLUDE[tsql](../../../includes/tsql-md.md)] レプリケーション ストアド プロシージャまたはレプリケーション管理オブジェクト (RMO) を使用すると、同じ監視データにプログラムからアクセスできます。 このオブジェクトにより、次のタスクをプログラムできます。  
  
-   パブリッシャー、パブリケーション、およびサブスクリプションの状態を監視する。  
  
-   1 つ以上のサブスクライバーにおけるマージ エージェント セッションを監視する。  
  
-   1 つ以上のサブスクライバーで適用を待機しているトランザクション コマンドを監視する。  
  
-   パブリケーションにユーザーの介入が必要となるしきい値の基準を定義する。  
  
-   トレーサー トークンのステータスを監視する。  
  
 **このトピックの内容:**  
  
 [Transact-SQL](#Tsql)  
  
 [レプリケーション管理オブジェクト (RMO)](#RMO)  
  
##  <a name="Tsql"></a> Transact-SQL  
  
#### <a name="to-monitor-publishers-publications-and-subscriptions-from-the-distributor"></a>ディストリビューターからパブリッシャー、パブリケーション、サブスクリプションを監視するには  
  
1.  ディストリビューターのディストリビューション データベースで、 [sp_replmonitorhelppublisher](/sql/relational-databases/system-stored-procedures/sp-replmonitorhelppublisher-transact-sql)を実行します。 これにより、このディストリビューターを利用している全パブリッシャーの監視情報が返されます。 結果セットを1つのパブリッシャーに限定するに**@publisher**は、を指定します。  
  
2.  ディストリビューターのディストリビューション データベースで、 [sp_replmonitorhelppublication](/sql/relational-databases/system-stored-procedures/sp-replmonitorhelppublication-transact-sql)を実行します。 これにより、このディストリビューターを利用している全パブリケーションの監視情報が返されます。 結果セットを1つのパブリッシャー、パブリケーション、またはパブリッシュされたデータベース**@publisher**に**@publication**制限する**@publisher_db**には、それぞれ、、またはを指定します。  
  
3.  ディストリビューターのディストリビューション データベースで、 [sp_replmonitorhelpsubscription](/sql/relational-databases/system-stored-procedures/sp-replmonitorhelpsubscription-transact-sql)を実行します。 これにより、このディストリビューターを利用しているすべてのサブスクリプションの監視情報が返されます。 結果セットを1つのパブリッシャー、パブリケーション、またはパブリッシュ済みデータベースに属するサブスクリプションに限定**@publisher**する**@publication**には**@publisher_db**、それぞれ、、またはを指定します。  
  
#### <a name="to-monitor-transactional-commands-waiting-to-be-applied-at-the-subscriber"></a>サブスクライバーで適用を待機しているトランザクション コマンドを監視するには  
  
1.  ディストリビューターのディストリビューション データベースで、 [sp_replmonitorsubscriptionpendingcmds](/sql/relational-databases/system-stored-procedures/sp-replmonitorsubscriptionpendingcmds-transact-sql)を実行します。 これにより、このディストリビューターを利用しているすべてのサブスクリプションの、待機中の全コマンドに関する監視情報が返されます。 結果セットを、1つのパブリッシャー、サブスクライバー、パブリケーション、またはパブリッシュされたデータベースに属するサブスクリプションの保留**@publisher**中**@subscriber**の**@publication**コマンドに**@publisher_db**限定するには、それぞれ、、、またはを指定します。  
  
#### <a name="to-monitor-merge-changes-waiting-to-be-uploaded-or-downloaded"></a>アップロードまたはダウンロードされるのを待機しているマージ変更を監視するには  
  
1.  パブリッシャーのパブリケーション データベースで、 [sp_showpendingchanges](/sql/relational-databases/system-stored-procedures/sp-showpendingchanges-transact-sql)を実行します。 返される結果セットには、サブスクライバーへのレプリケートを待機している変更に関する情報が示されます。 結果セットを1つのパブリケーションまたはアーティクルに属する変更に限定するに**@publication**は**@article**、それぞれまたはを指定します。  
  
2.  サブスクライバーのサブスクリプション データベースで、 [sp_showpendingchanges](/sql/relational-databases/system-stored-procedures/sp-showpendingchanges-transact-sql)を実行します。 返される結果セットには、パブリッシャーへのレプリケートを待機している変更に関する情報が示されます。 結果セットを1つのパブリケーションまたはアーティクルに属する変更に限定するに**@publication**は**@article**、それぞれまたはを指定します。  
  
#### <a name="to-monitor-merge-agent-sessions"></a>マージ エージェント セッションを監視するには  
  
1.  ディストリビューターのディストリビューション データベースで、 [sp_replmonitorhelpmergesession](/sql/relational-databases/system-stored-procedures/sp-replmonitorhelpmergesession-transact-sql)を実行します。 これにより、このディストリビューターを利用する全サブスクリプションのすべてのマージ エージェント セッションに関する監視情報 ( **Session_id**を含む) が返されます。 また、 **MSmerge_sessions** システム テーブルにクエリを実行することでも、 [Session_id](/sql/relational-databases/system-tables/msmerge-sessions-transact-sql) を取得できます。  
  
2.  ディストリビューターのディストリビューション データベースで、 [sp_replmonitorhelpmergesessiondetail](/sql/relational-databases/system-stored-procedures/sp-replmonitorhelpmergesessiondetail-transact-sql)を実行します。 手順 1. で取得した **Session_id** の値を **@session_id**を実行します。 これにより、セッションに関する詳細な監視情報が表示されます。  
  
3.  目的の各セッションについて、手順 2. を実行します。  
  
#### <a name="to-monitor-merge-agent-sessions-for-pull-subscriptions-from-the-subscriber"></a>サブスクライバーからのプル サブスクリプションのマージ エージェント セッションを監視するには  
  
1.  サブスクライバーのサブスクリプション データベースで、 [sp_replmonitorhelpmergesession](/sql/relational-databases/system-stored-procedures/sp-replmonitorhelpmergesession-transact-sql)を実行します。 特定のサブスクリプションについて**@publisher**、 **@publication**、、およびに**@publisher_db**パブリケーションデータベースの名前を指定します。 これにより、このサブスクリプションの過去 5 回のマージ エージェント セッションに関する監視情報が返されます。 結果セットで、目的のセッションの **Session_id** の値を確認します。  
  
2.  サブスクライバーのサブスクリプション データベースで、 [sp_replmonitorhelpmergesessiondetail](/sql/relational-databases/system-stored-procedures/sp-replmonitorhelpmergesessiondetail-transact-sql)を実行します。 手順 1. で取得した **Session_id** の値を **@session_id**を実行します。 これにより、セッションに関する詳細な監視情報が表示されます。  
  
3.  目的の各セッションについて、手順 2. を実行します。  
  
#### <a name="to-view-and-modify-the-monitor-threshold-metrics-for-a-publication"></a>パブリケーションのしきい値を表示して変更するには  
  
1.  ディストリビューターのディストリビューション データベースで、 [sp_replmonitorhelppublicationthresholds](/sql/relational-databases/system-stored-procedures/sp-replmonitorhelppublicationthresholds-transact-sql)を実行します。 これにより、このディストリビューターを利用している全パブリケーションの監視しきい値が返されます。 結果セットを、単一のパブリッシャーまたはパブリッシュされたデータベースまたは1つのパブリケーションに属するパブリケーションに対する**@publisher**監視**@publisher_db**しきい値**@publication**を制限するには、それぞれ、、またはを指定します。 変更する必要があるしきい値に対応する **Metric_id** の値を確認します。 詳細については、「 [Set Thresholds and Warnings in Replication Monitor](set-thresholds-and-warnings-in-replication-monitor.md)」を参照してください。  
  
2.  ディストリビューターのディストリビューション データベースで、 [sp_replmonitorchangepublicationthreshold](/sql/relational-databases/system-stored-procedures/sp-replmonitorchangepublicationthreshold-transact-sql)を実行します。 必要に応じて、次の値を指定します。  
  
    -   手順 1. で得た **Metric_id** の値を **@metric_id**を実行します。  
  
    -   モニタしきい値メトリックの新しい値を指定**@value**します。  
  
    -   このしきい値に到達したときに警告をログに記録するには、 **@shouldalert** に **@shouldalert** を指定します。警告が不要な場合には、 **0** を指定します。  
  
    -   このしきい値に到達したときに警告をログに記録するには、 **@shouldalert** に **@mode** を指定し、無効にするには **2** を指定します。  
  
##  <a name="RMO"></a> レプリケーション管理オブジェクト (RMO)  
  
#### <a name="to-monitor-a-subscription-to-a-merge-publication-at-the-subscriber"></a>サブスクライバーでマージ パブリケーションのサブスクリプションを監視するには  
  
1.  <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、サブスクライバーへの接続を作成します。  
  
2.  <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor> クラスのインスタンスを作成し、サブスクリプションの <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.Publisher%2A>、 <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.Publication%2A>、 <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.PublisherDB%2A>、 <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.SubscriberDB%2A> の各プロパティを設定します。次に、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティに対し、手順 1. で作成した <xref:Microsoft.SqlServer.Management.Common.ServerConnection> を設定します。  
  
3.  次のいずれかのメソッドを呼び出して、このサブスクリプションのマージ エージェント セッションの情報を取得します。  
  
    -   <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.GetSessionsSummary%2A> - 過去に発生したマージ エージェント セッションの情報を保持する <xref:Microsoft.SqlServer.Replication.MergeSessionSummary> オブジェクトの配列を返します (最大 5 セッション)。 監視対象のすべてのセッションについて、 <xref:Microsoft.SqlServer.Replication.MergeSessionSummary.SessionId%2A> 値を確認してください。  
  
    -   <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.GetSessionsSummary%2A> - 過去に発生したマージ エージェント セッションの情報を保持する <xref:Microsoft.SqlServer.Replication.MergeSessionSummary> パラメーターに指定された期間内に発生したマージ エージェント セッションの情報を保持する *T:Microsoft.SqlServer.Replication.MergeSessionSummary* オブジェクトの配列を返します (最大 5 セッション)。 監視対象のすべてのセッションについて、 <xref:Microsoft.SqlServer.Replication.MergeSessionSummary.SessionId%2A> 値を確認してください。  
  
    -   <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.GetLastSessionSummary%2A> - 前回のマージ エージェント セッションの情報を保持する <xref:Microsoft.SqlServer.Replication.MergeSessionSummary> オブジェクトを返します。 このセッションの <xref:Microsoft.SqlServer.Replication.MergeSessionSummary.SessionId%2A> 値を確認してください。  
  
    -   <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.GetSessionsSummaryDataSet%2A> - 過去のマージ エージェント セッション (最大 5 セッション) の情報を、1 行あたり 1 セッションの形式で保持する <xref:System.Data.DataSet> オブジェクトを返します。 監視対象のすべてのセッションについて、 **Session_id** 列の値を確認してください。  
  
    -   <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.GetLastSessionSummaryDataRow%2A> - 前回のマージ エージェント セッションの情報を保持する <xref:System.Data.DataRow> オブジェクトを返します。 このセッションの **Session_id** 列の値を確認してください。  
  
4.  (省略可) <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.RefreshSessionSummary%2A> を呼び出して、 <xref:Microsoft.SqlServer.Replication.MergeSessionSummary> として渡された *T:Microsoft.SqlServer.Replication.MergeSessionSummary* オブジェクトのデータを更新します。または、 <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.RefreshSessionSummary%2A> を呼び出して、 <xref:System.Data.DataRow> として渡された *T:System.Data.DataRow*を実行します。  
  
5.  手順 3. で取得したセッション ID を使用して次のいずれかのメソッドを呼び出し、特定のセッションの詳細情報を取得します。  
  
    -   <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.GetSessionDetails%2A>-指定された<xref:Microsoft.SqlServer.Replication.MergeSessionDetail> *sessionID*のオブジェクトの配列を返します。  
  
    -   <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.GetSessionDetailsDataSet%2A>-指定さ<xref:System.Data.DataSet>れた*sessionID*の情報を含むオブジェクトを返します。  
  
#### <a name="to-monitor-replication-properties-for-all-publications-at-a-distributor"></a>ディストリビューターですべてのパブリケーションについてレプリケーション プロパティを監視するには  
  
1.  <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、ディストリビューターへの接続を作成します。  
  
2.  <xref:Microsoft.SqlServer.Replication.ReplicationMonitor> クラスのインスタンスを作成します。  
  
3.  <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティに、手順 1. で作成した <xref:Microsoft.SqlServer.Management.Common.ServerConnection> を設定します。  
  
4.  <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドを呼び出して、オブジェクトのプロパティを取得します。  
  
5.  次の 1 つまたは複数のメソッドを実行して、このディストリビューターを使用している、すべてのパブリッシャーのレプリケーション情報を取得します。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumDistributionAgents%2A> - このディストリビューターのすべてのディストリビューション エージェントに関する情報を保持する <xref:System.Data.DataSet> オブジェクトを返します。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumErrorRecords%2A> - ディストリビューターに保存されているエラー情報を保持する <xref:System.Data.DataSet> オブジェクトを返します。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumLogReaderAgents%2A> - ディストリビューターのすべてのログ リーダー エージェントに関する情報を保持する <xref:System.Data.DataSet> オブジェクトを返します。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumMergeAgents%2A> - ディストリビューターのすべてのマージ エージェントに関する情報を保持する <xref:System.Data.DataSet> オブジェクトを返します。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumMiscellaneousAgents%2A> - ディストリビューターのその他すべてのレプリケーション エージェントに関する情報を保持する <xref:System.Data.DataSet> オブジェクトを返します。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumPublishers%2A> - このディストリビューターのすべてのパブリッシャーに関する情報を保持する <xref:System.Data.DataSet> オブジェクトを返します。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumPublishers2%2A> - このディストリビューターを使用しているパブリッシャーを返す <xref:System.Data.DataSet> オブジェクトを返します。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumQueueReaderAgents%2A> - ディストリビューターのすべてのキュー リーダー エージェントに関する情報を保持する <xref:System.Data.DataSet> オブジェクトを返します。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumQueueReaderAgentSessionDetails%2A> - 指定されたキュー リーダー エージェントおよびセッションの情報を保持する <xref:System.Data.DataSet> オブジェクトを返します。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumQueueReaderAgentSessions%2A> - 指定されたキュー リーダー エージェントのセッション情報を保持する <xref:System.Data.DataSet> オブジェクトを返します。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumSnapshotAgents%2A> - ディストリビューターのすべてのスナップショット エージェントに関する情報を保持する <xref:System.Data.DataSet> オブジェクトを返します。  
  
#### <a name="to-monitor-publication-properties-for-a-specific-publisher-at-the-distributor"></a>ディストリビューターで特定のパブリッシャーのパブリケーション プロパティを監視するには  
  
1.  <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、ディストリビューターへの接続を作成します。  
  
2.  次のいずれかの方法で <xref:Microsoft.SqlServer.Replication.PublisherMonitor> オブジェクトを取得します。  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor> クラスのインスタンスを作成します。 パブリッシャーの <xref:Microsoft.SqlServer.Replication.PublisherMonitor.Name%2A> プロパティを設定し、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティに手順 1. で作成した <xref:Microsoft.SqlServer.Management.Common.ServerConnection> を設定します。 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドを呼び出して、オブジェクトのプロパティを取得します。 このメソッドから `false` が返された場合、パブリッシャー名が正しく定義されていないか、パブリケーションが存在していません。  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitorCollection> から取得します。このコレクションには、既存の <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.PublisherMonitors%2A> オブジェクトの <xref:Microsoft.SqlServer.Replication.ReplicationMonitor> プロパティを使用してアクセスできます。  
  
3.  次の 1 つまたは複数のメソッドを実行して、このパブリッシャーに属している、すべてのパブリケーションのレプリケーション情報を取得します。  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumDistributionAgentSessionDetails%2A> - 指定されたディストリビューション エージェントおよびセッションの情報を保持する <xref:System.Data.DataSet> オブジェクトを返します。  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumDistributionAgentSessions%2A> - 指定されたディストリビューション エージェントのセッション情報を保持する <xref:System.Data.DataSet> オブジェクトを返します。  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumErrorRecords%2A> - 指定されたエラーのエラー レコード情報を保持する <xref:System.Data.DataSet> オブジェクトを返します。  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumLogReaderAgentSessionDetails%2A> - 指定されたログ リーダー エージェントおよびセッションの情報を保持する <xref:System.Data.DataSet> オブジェクトを返します。  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumLogReaderAgentSessions%2A> - 指定されたログ リーダー エージェントのセッション情報を保持する <xref:System.Data.DataSet> オブジェクトを返します。  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumMergeAgentSessionDetails%2A> - 指定されたマージ エージェントおよびセッションの情報を保持する <xref:System.Data.DataSet> オブジェクトを返します。  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumMergeAgentSessionDetails2%2A> - 指定されたマージ エージェントおよびセッションの追加情報を保持する <xref:System.Data.DataSet> オブジェクトを返します。  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumMergeAgentSessions%2A> - 指定されたマージ エージェントのセッション情報を保持する <xref:System.Data.DataSet> オブジェクトを返します。  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumMergeAgentSessions2%2A> - 指定されたマージ エージェントの追加のセッション情報を保持する <xref:System.Data.DataSet> オブジェクトを返します。  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumPublications%2A> - このディストリビューターのすべてのパブリケーションに関する情報を保持する <xref:System.Data.DataSet> オブジェクトを返します。  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumPublications2%2A> - このディストリビューターのすべてのパブリケーションに関する追加情報を保持する <xref:System.Data.DataSet> オブジェクトを返します。  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumSnapshotAgentSessionDetails%2A> - 指定されたスナップショット エージェントおよびセッションの情報を保持する <xref:System.Data.DataSet> オブジェクトを返します。  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumSnapshotAgentSessions%2A> - 指定されたスナップショット エージェントのセッション情報を保持する <xref:System.Data.DataSet> オブジェクトを返します。  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumSubscriptions%2A> - このディストリビューターのパブリケーションに対するすべてのサブスクリプションに関する情報を保持する <xref:System.Data.DataSet> オブジェクトを返します。  
  
#### <a name="to-monitor-properties-for-a-specific-publication-at-the-distributor"></a>ディストリビューターで特定のパブリッシャーのプロパティを監視するには  
  
1.  <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、ディストリビューターへの接続を作成します。  
  
2.  次のいずれかの方法で <xref:Microsoft.SqlServer.Replication.PublicationMonitor> オブジェクトを取得します。  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitor> クラスのインスタンスを作成します。 パブリケーションの <xref:Microsoft.SqlServer.Replication.PublicationMonitor.DistributionDBName%2A>、 <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublisherName%2A>、 <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublicationDBName%2A>、 <xref:Microsoft.SqlServer.Replication.PublicationMonitor.Name%2A> の各プロパティを設定し、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティに手順 1. で作成した <xref:Microsoft.SqlServer.Management.Common.ServerConnection> を設定します。 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドを呼び出して、オブジェクトのプロパティを取得します。 このメソッドから `false` が返された場合、パブリケーションのプロパティが正しく定義されていないか、パブリケーションが存在していません。  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitorCollection> から取得します。このコレクションには、既存の <xref:Microsoft.SqlServer.Replication.PublisherMonitor.PublicationMonitors%2A> オブジェクトの <xref:Microsoft.SqlServer.Replication.PublisherMonitor> プロパティを使用してアクセスできます。  
  
3.  次の 1 つまたは複数のメソッドを実行して、このパブリケーションに関する情報を取得します。  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumErrorRecords%2A> - 指定されたエラーのエラー レコードを保持する <xref:System.Data.DataSet> オブジェクトを返します。  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumLogReaderAgent%2A> - このパブリケーションのログ リーダー エージェントに関する情報を保持する <xref:System.Data.DataSet> オブジェクトを返します。  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumMonitorThresholds%2A> - このパブリケーションに設定されている監視警告のしきい値情報を保持する <xref:System.Data.DataSet> オブジェクトを返します。  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumQueueReaderAgent%2A> - このパブリケーションで使用されるキュー リーダー エージェントに関する情報を保持する <xref:System.Data.DataSet> オブジェクトを返します。  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumSnapshotAgent%2A> - このパブリケーションのスナップショット エージェントに関する情報を保持する <xref:System.Data.DataSet> オブジェクトを返します。  
  
    -   <xref:Microsoft.SqlServer.Replication.Publication.EnumSubscriptions%2A> - このパブリケーションのサブスクリプションに関する情報を保持する <xref:System.Data.DataSet> オブジェクトを返します。  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumSubscriptions2%2A> - このパブリケーションのサブスクリプションに関する追加情報を保持する <xref:System.Data.DataSet> オブジェクトを、指定された <xref:Microsoft.SqlServer.Replication.SubscriptionResultOption>に基づいて返します。  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumTracerTokenHistory%2A> - 指定されたトレーサー トークンの待機時間情報を保持する <xref:System.Data.DataSet> オブジェクトを返します。  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumTracerTokens%2A> - このパブリケーションに挿入されたすべてのトレーサー トークンに関する情報を保持する <xref:System.Data.DataSet> オブジェクトを返します。  
  
#### <a name="to-monitor-transactional-commands-that-are-waiting-to-be-applied-at-the-subscriber"></a>サブスクライバーで適用待ち状態になっているトランザクション コマンドを監視するには  
  
1.  <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、ディストリビューターへの接続を作成します。  
  
2.  次のいずれかの方法で <xref:Microsoft.SqlServer.Replication.PublicationMonitor> オブジェクトを取得します。  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitor> クラスのインスタンスを作成します。 パブリケーションの <xref:Microsoft.SqlServer.Replication.PublicationMonitor.DistributionDBName%2A>、 <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublisherName%2A>、 <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublicationDBName%2A>、 <xref:Microsoft.SqlServer.Replication.PublicationMonitor.Name%2A> の各プロパティを設定し、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティに手順 1. で作成した <xref:Microsoft.SqlServer.Management.Common.ServerConnection> を設定します。 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドを呼び出して、オブジェクトのプロパティを取得します。 このメソッドから `false` が返された場合、パブリケーションのプロパティが正しく定義されていないか、パブリケーションが存在していません。  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitorCollection> から取得します。このコレクションには、既存の <xref:Microsoft.SqlServer.Replication.PublisherMonitor.PublicationMonitors%2A> オブジェクトの <xref:Microsoft.SqlServer.Replication.PublisherMonitor> プロパティを使用してアクセスできます。  
  
3.  <xref:Microsoft.SqlServer.Replication.PublicationMonitor.TransPendingCommandInfo%2A> メソッドを実行して <xref:Microsoft.SqlServer.Replication.PendingCommandInfo> オブジェクトを取得します。  
  
4.  この <xref:Microsoft.SqlServer.Replication.PendingCommandInfo> オブジェクトのプロパティを使用して、保留状態の推定コマンド数と、コマンドを配信を完了するまでの時間を調べます。  
  
#### <a name="to-set-the-monitor-warning-thresholds-for-a-publication"></a>パブリケーションに対して監視警告のしきい値を設定するには  
  
1.  <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、ディストリビューターへの接続を作成します。  
  
2.  次のいずれかの方法で <xref:Microsoft.SqlServer.Replication.PublicationMonitor> オブジェクトを取得します。  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitor> クラスのインスタンスを作成します。 パブリケーションの <xref:Microsoft.SqlServer.Replication.PublicationMonitor.DistributionDBName%2A>、 <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublisherName%2A>、 <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublicationDBName%2A>、 <xref:Microsoft.SqlServer.Replication.PublicationMonitor.Name%2A> の各プロパティを設定し、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティに手順 1. で作成した <xref:Microsoft.SqlServer.Management.Common.ServerConnection> を設定します。 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドを呼び出して、オブジェクトのプロパティを取得します。 このメソッドから `false` が返された場合、パブリケーションのプロパティが正しく定義されていないか、パブリケーションが存在していません。  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitorCollection> から取得します。このコレクションには、既存の <xref:Microsoft.SqlServer.Replication.PublisherMonitor.PublicationMonitors%2A> オブジェクトの <xref:Microsoft.SqlServer.Replication.PublisherMonitor> プロパティを使用してアクセスできます。  
  
3.  <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumMonitorThresholds%2A> メソッドを実行します。 返された <xref:System.Collections.ArrayList> オブジェクトの <xref:Microsoft.SqlServer.Replication.MonitorThreshold> で、現在のしきい値設定を確認します。  
  
4.  <xref:Microsoft.SqlServer.Replication.PublicationMonitor.ChangeMonitorThreshold%2A> メソッドを実行します。 次のパラメーターを指定します。  
  
    -   *metricID* - 監視しきい値の基準を表す <xref:System.Int32> 値です。次の表に示す値を使用します。  
  
        |Value|説明|  
        |-----------|-----------------|  
        |1|
  `expiration` - トランザクション パブリケーションへのサブスクリプションに期限が迫っていないかを監視します。|  
        |2|
  `latency` - トランザクション パブリケーションへのサブスクリプションのパフォーマンスを監視します。|  
        |4|
  `mergeexpiration` - マージ パブリケーションへのサブスクリプションに期限が迫っていないかを監視します。|  
        |5|
  `mergeslowrunduration` - 低速回線 (ダイヤルアップ) 接続でのマージの同期時間を監視します。|  
        |6|
  `mergefastrunduration` - 高帯域 (LAN) 接続でのマージ同期の期間を監視します。|  
        |7|
  `mergefastrunspeed` : 高帯域幅 (LAN) 接続経由でのマージ同期の同期速度を監視します。|  
        |8|
  `mergeslowrunspeed` - 低速回線 (ダイヤルアップ) 接続でのマージの同期速度を監視します。|  
  
    -   *enable* - <xref:System.Boolean> 値です。  
  
    -   *thresholdValue* - しきい値を設定する整数値です。  
  
    -   *shouldAlert* - このしきい値に対して警告を生成するかどうかを示す整数値です。  
  
  
