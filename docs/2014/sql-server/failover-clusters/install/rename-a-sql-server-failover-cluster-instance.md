---
title: SQL Server のフェールオーバー クラスター インスタンスの名前変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- clusters [SQL Server], virtual servers
- renaming virtual servers
- virtual servers [SQL Server], failover clustering
- failover clustering [SQL Server], virtual servers
ms.assetid: 2a49d417-25fb-4760-8ae5-5871bfb1e6f3
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4ce98bacfcc5f3aa8814a9253d1796fd18c4a735
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63126020"
---
# <a name="rename-a-sql-server-failover-cluster-instance"></a>SQL Server のフェールオーバー クラスター インスタンスの名前変更
  フェールオーバー クラスターに含まれる [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスの場合、仮想サーバーの名前を変更する手順は、スタンドアロン インスタンスでの手順とは異なります。 詳細については、 [SQL Server のスタンドアロン インスタンスをホストするコンピューターの名前変更](../../../database-engine/install-windows/rename-a-computer-that-hosts-a-stand-alone-instance-of-sql-server.md)を参照してください。  
  
 仮想サーバーの名前は、常に SQL ネットワーク名 (SQL 仮想サーバー ネットワーク名) と同じになります。 仮想サーバー名は変更できますが、インスタンス名は変更できません。 たとえば、VS1\instance1 という仮想サーバー名を SQL35\instance1 などの別の名前に変更することはできますが、名前のインスタンスの部分 instance1 は変更されません。  
  
 名前の変更処理を開始する前に、次の項目を確認します。  
  
-   
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、レプリケーションにログ配布が使用されている場合を除いて、レプリケーション対象サーバーの名前は変更できません。 プライマリ サーバーが完全に存在しなくなった場合は、ログ配布対象のセカンダリ サーバーの名前を変更することができます。 詳細については、「[ログ配布とレプリケーション &#40;SQL Server&#41;](../../../database-engine/log-shipping/log-shipping-and-replication-sql-server.md)」 を参照してください。  
  
-   データベース ミラーリングを使用するよう構成されている仮想サーバーの名前を変更する場合は、名前の変更を行う前にデータベース ミラーリングを無効にし、名前の変更後に新しい仮想サーバー名でデータベース ミラーリングを再確立する必要があります。 データベース ミラーリングのメタデータは、新しい仮想サーバー名に、自動的には更新されません。  
  
### <a name="to-rename-a-virtual-server"></a>仮想サーバーの名前を変更するには  
  
1.  クラスター アドミニストレーターを使用して、SQL ネットワーク名を新しい名前に変更します。  
  
2.  ネットワーク名リソースをオフラインにします。 これにより、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] リソースや、他の依存リソースもオフラインになります。  
  
3.  
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] リソースをオンラインに戻します。  
  
## <a name="verify-the-renaming-operation"></a>名前の変更操作の確認  
 仮想サーバーの名前を変更したら、このサーバーの古い名前を使用している接続は、新しい名前を使用して接続するように変更する必要があります。  
  
 名前の変更が完了していることを確認するには、`@@servername` または `sys.servers` のいずれかを使用して情報を取得します。 
  `@@servername` 関数は新しい仮想サーバー名を返し、`sys.servers` テーブルには新しい仮想サーバー名が表示されます。 また、フェールオーバー処理が新しい名前を使って正常に機能していることを確認するには、他のノードに対する [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] リソースのフェールオーバーが発生するように試行します。  
  
 クラスター内のノードからの接続については、新しい名前を直ちに使用できます。 ただし、クライアント コンピューターから新しい名前を使用して接続する場合は、クライアント コンピューターが新しい名前を認識できるようにならないと、新しい名前を使用してサーバーに接続することはできません。 新しい名前がネットワーク全体に伝達されるのに必要な時間は、ネットワークの構成により異なり、数秒で済むことも、3 ～ 5 分かかることもあります。ネットワークから古い仮想サーバー名が消去されるには、さらに時間がかかる場合があります。  
  
 仮想サーバー名の変更をネットワークに伝達する時間を最小限に抑えるには、次の手順を実行します。  
  
#### <a name="to-minimize-network-propagation-delay"></a>ネットワークの伝達の遅延を最小限に抑えるには  
  
1.  サーバー ノードでコマンド プロンプトから次のコマンドを実行します。  
  
    ```  
    ipconfig /flushdns  
    ipconfig /registerdns  
    nbtstat -RR  
    ```  
  
## <a name="additional-considerations-after-the-renaming-operation"></a>名前変更操作後のその他の考慮事項  
 フェールオーバー クラスターのネットワーク名を変更した後は、以下の点を検証および実行して、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェントと [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]のすべてのシナリオを有効にする必要があります。  
  
 **[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]:** Windows クラスターアドミニストレーターツールを使用して[!INCLUDE[ssASCurrent](../../../includes/ssascurrent-md.md)]フェールオーバークラスターインスタンスのネットワーク名を変更した後、今後のアップグレードまたはアンインストール操作が失敗する場合があります。 この問題を解決するには、[この](https://go.microsoft.com/fwlink/?LinkId=244002)記事の「解決方法」の手順に従っhttps://go.microsoft.com/fwlink/?LinkId=244002)て、 **ClusterName**レジストリエントリを更新します (「」を参照してください。  
  
 ** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]エージェントサービス:** 次のエージェントサービスの[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]追加アクションを確認して実行します。  
  
-   SQL エージェントがイベントの転送用に構成されている場合は、レジストリ設定を修正します。 詳細については、[イベントの転送先サーバーの指定 &#40;SQL Server Management Studio&#41;](../../../ssms/agent/designate-an-events-forwarding-server-sql-server-management-studio.md) を参照してください。  
  
-   コンピューター/クラスターのネットワーク名が変更されている場合は、マスター サーバー (MSX) とターゲット サーバー (TSX) のインスタンス名を修正します。 詳細については、次のトピックを参照してください。  
  
    -   [マスター サーバーからの複数のターゲット サーバーの参加の解除](../../../ssms/agent/defect-multiple-target-servers-from-a-master-server.md)  
  
    -   [マルチサーバー環境の作成](../../../ssms/agent/create-a-multiserver-environment.md)  
  
-   ログ配布を再構成して、更新されたサーバー名を使ってログがバックアップおよび復元されるようにします。 詳細については、次のトピックを参照してください。  
  
    -   [ログ配布 &#40;SQL Server&#41;を構成する](../../../database-engine/log-shipping/configure-log-shipping-sql-server.md)  
  
    -   [ログ配布 &#40;SQL Server の削除&#41;](../../../database-engine/log-shipping/remove-log-shipping-sql-server.md)  
  
-   サーバー名を使用するジョブ ステップを更新します。 詳細については、 [ジョブ ステップの管理](../../../ssms/agent/manage-job-steps.md)を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQL Server のスタンドアロン インスタンスをホストするコンピューターの名前変更](../../../database-engine/install-windows/rename-a-computer-that-hosts-a-stand-alone-instance-of-sql-server.md)  
  
  
