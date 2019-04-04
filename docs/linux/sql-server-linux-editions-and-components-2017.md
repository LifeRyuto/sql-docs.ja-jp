---
title: 各エディションと SQL Server 2017 の機能がサポートされている ~ Linux |Microsoft Docs
ms.custom: sql-linux
ms.date: 09/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: linux
ms.topic: conceptual
helpviewer_keywords:
- Enterprise Edition [SQL Server]
- Developer Edition [SQL Server]
- default components
- installing SQL Server, components
- Setup [SQL Server], components
- SQL Server, editions
- SQL Server, components
- editions [SQL Server]
- versions [SQL Server]
- Setup [SQL Server], editions
- SQL Server Installation Wizard
- components [SQL Server]
- Standard Edition [SQL Server]
- installing SQL Server, editions
- editions [SQL Server], about edition options
- Setup [SQL Server]
ms.assetid: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 07aae4f4e619e38d41cd16a08e1e8f7267f5ed29
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2018
ms.locfileid: "52533555"
---
# <a name="editions-and-supported-features-of-sql-server-2017-on-linux"></a>エディションと SQL Server 2017 on Linux のサポートされる機能

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

この記事では、SQL Server 2017 on Linux の各種エディションでサポートされる機能の詳細を説明します。 エディションと Windows 上の SQL Server のサポートされる機能は、[SQL Server 2017 - Windows](../sql-server/editions-and-components-of-sql-server-2017.md)を参照してください。  
  
インストールの前提条件は、アプリケーションのニーズによって異なります。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] にはさまざまなエディションがあり、組織や個人の独自のパフォーマンス、ランタイム、および価格に関する要件に対応できます。 インストールする [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] コンポーネントは、ユーザーの特定の要件によっても異なります。 この後のセクションでは、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の最適なエディションおよびコンポーネントを選択する方法について説明します。  

最新のリリース ノートと新機能については、以下の情報を参照してください。
- [Linux 上の SQL Server のリリース ノート](sql-server-linux-release-notes.md)
- [Linux 上の SQL Server の新機能新機能](sql-server-linux-whats-new.md)

Linux で使用できない SQL Server 機能の一覧は、[機能とサービスがサポートされていない](sql-server-linux-release-notes.md#Unsupported)を参照してください。

### <a name="try-sql-server"></a>SQL Server を試してください    
    
[SQL Server 2017 をダウンロードします。](https://www.microsoft.com/sql-server/sql-server-2017)

## <a name="includessnoversionincludesssnoversion-mdmd-editions"></a>[!INCLUDE[ssNoVersion](../includes/ssNoVersion-md.md)] のエディション  
 次の表で、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のエディションについて説明します。 
  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エディション|定義|  
|---------------------------------------|----------------|  
|Enterprise|Premium オファリング[!INCLUDE[ssNoVersion](../includes/ssNoVersion-md.md)]Enterprise edition は、ミッション クリティカルなワークロードの高度なサービス レベルを有効にすると、超高速パフォーマンスを包括的なハイエンド データ センター機能を提供します。|  
|Standard|[!INCLUDE[ssNoVersion](../includes/ssNoVersion-md.md)] Standard edition では、部門や小規模組織がアプリケーションを実行するための基本的なデータ管理を実現し、オンプレミスとクラウドの最小限の IT リソースで効果的なデータベース管理を有効にする一般的な開発ツールをサポートします。|  
|Web|[!INCLUDE[ssNoVersion](../includes/ssNoVersion-md.md)] Web Edition は、大小さまざまな規模の Web 資産に対応できるスケーラビリティ、経済性、および管理性を備えた、Web ホスティング企業および Web VAP 向けの総保有コストの低いオプションです。|  
|Developer|開発者は、[!INCLUDE[ssNoVersion](../includes/ssNoVersion-md.md)] Developer Edition を使用して、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]上で動作するあらゆる種類のアプリケーションを開発できます。 このエディションには Enterprise Edition の機能がすべて含まれていますが、実稼動サーバーとして使用するのではなく、開発およびテスト システムとしての利用に対してライセンスが供与されます。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Developer は、アプリケーションを作成し、テストするユーザーに適しています。|  
|Express Edition|Express Edition はエントリレベルの無料のデータベースで、学習や、デスクトップおよび小規模サーバー データ ドリブン アプリケーションの構築などに適しています。 このエディションは、独立系ソフトウェア ベンダー、開発者、クライアント アプリケーションを趣味で開発する開発者などに最適です。 さらに高度なデータベース機能が必要な場合には、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Express を [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の他の上位バージョンにシームレスにアップグレードできます。|  
  
## <a name="using-includessnoversionincludesssnoversion-mdmd-with-clientserver-applications"></a>[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] とクライアント/サーバー アプリケーションの使用  

[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のクライアント コンポーネントだけを、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のインスタンスに直接接続するクライアント/サーバー アプリケーションを実行するコンピューターにインストールできます。 クライアント コンポーネントをインストールすることは、データベース サーバー上にある [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスを管理する場合、または [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] アプリケーションを開発しようとしている場合にも適切なオプションです。  
  
## <a name="includessnoversionincludesssnoversion-mdmd-components"></a>[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] コンポーネント  

Linux 上の SQL Server 2017 には、SQL Server データベース エンジンがサポートされています。 次の表では、データベース エンジンの機能について説明します。   
  
|サーバー コンポーネント|説明|  
|-----------------------|-----------------|  
|[!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]|[!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] 含まれています、 [!INCLUDE[ssDE](../includes/ssde-md.md)]、およびデータベース analytics との統合の格納、処理、およびデータ、レプリケーション、フルテキスト検索、リレーショナルを管理するためのツールおよび XML データをセキュリティで保護するためのコア サービスです。|  

**Developer、Enterprise Core、および Evaluation edition**  
Developer、Enterprise Core、および Evaluation edition でサポートされる機能では、次の表に、SQL Server Enterprise edition の機能を参照してください。

Developer Edition は引き続き [SQL Server Distributed Replay](../tools/distributed-replay/sql-server-distributed-replay.md) のクライアントを 1 つだけサポートします。 
  
##  <a name="Cross-BoxScaleLimits"></a> スケールの制限  
  
|機能|Enterprise|Standard|Web|Express| 
|-------------|----------------|--------------|---------|------------------------|
|1 つのインスタンスで使用される最大計算容量 - [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]<sup>1</sup>|オペレーティング システムの最大容量|4 ソケットまたは 24 コアのいずれか小さいほうに制限|4 ソケットまたは 16 コアのいずれか小さいほうに制限|1 ソケットまたは 4 コアのいずれか小さいほうに制限| 
|1 つのインスタンスで使用される最大計算容量 - [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] または [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]|オペレーティング システムの最大容量|4 ソケットまたは 24 コアのいずれか小さいほうに制限|4 ソケットまたは 16 コアのいずれか小さいほうに制限|1 ソケットまたは 4 コアのいずれか小さいほうに制限|
|[!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] のインスタンスごとのバッファー プールの最大メモリ|オペレーティング システムの最大容量|128 GB|64 GB|1410 MB|
|[!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] のインスタンスごとの列ストア セグメント キャッシュの最大メモリ|メモリ制限なし| 32 GB| 16 GB| 352 MB|  
|[!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] のデータベースごとの最大メモリ最適化データ サイズ|メモリ制限なし| 32 GB| 16 GB| 352 MB|
|リレーショナル データベースの最大サイズ|524 PB|524 PB|524 PB|10 GB|  
  
<sup>1</sup> Enterprise edition with Server およびクライアント アクセス ライセンス (CAL) に基づくライセンス (新しい使用許諾契約は利用できません) は SQL Server インスタンスあたり 20 コアの最大数に制限されます。 コアベースのサーバー ライセンス モデルでは、制限はありません。 詳細については、[エディションの SQL Server での計算容量制限](../sql-server/compute-capacity-limits-by-edition-of-sql-server.md)を参照してください。  
 
##  <a name="RDBMSHA"></a> RDBMS の高可用性  
  
|機能|Enterprise|Standard|Web|Express|  
|-------------|----------------|--------------|---------|------------------------|  
|ログ配布|はい|[はい]|[はい]|いいえ|  
|バックアップ圧縮|はい|[はい]|いいえ|いいえ| 
|データベース スナップショット|はい|いいえ|いいえ|いいえ|
|Always On フェールオーバー クラスター インスタンス<sup>1</sup>|はい|[はい]|いいえ|いいえ| 
|Always On 可用性グループ<sup>2</sup>|はい|いいえ|いいえ|いいえ|
|基本的な可用性グループ<sup>3</sup>|いいえ|はい|いいえ|いいえ|
|最小レプリカ コミット可用性グループ|はい|[はい]|いいえ|いいえ|
|クラスターを使用しない可用性グループ|はい|[はい]|いいえ|いいえ|
|オンライン ページおよびファイルの復元|はい|いいえ|いいえ|いいえ|
|オンラインのインデックス構築|はい|いいえ|いいえ|いいえ|
|再開可能なオンライン インデックス再構築|はい|いいえ|いいえ|いいえ|
|オンラインのスキーマ変更|はい|いいえ|いいえ|いいえ|
|高速復旧|はい|いいえ|いいえ|いいえ|
|ミラー化バックアップ|はい|いいえ|いいえ|いいえ|
|ホット アド メモリと CPU|はい|いいえ|いいえ|いいえ|
|暗号化されたバックアップ|はい|[はい]|いいえ|いいえ|
|Windows Azure へのハイブリッド バックアップ (URL へのバックアップ)|はい|[はい]|いいえ|いいえ|
  
<sup>1</sup> Enterprise edition では、ノードの数は、オペレーティング システムの最大値。 Standard Edition では、2 つのノードがサポートされます。 

<sup>2</sup>の Enterprise edition では、2 つの同期セカンダリ レプリカを含む、最大 8 個のセカンダリ レプリカのサポートを提供します。 

<sup>3</sup> standard edition は、基本的な可用性グループをサポートしています。 基本的な可用性グループは、1 つのデータベースで、2 つのレプリカをサポートします。 基本的な可用性グループの詳細については、「[基本的な可用性グループ](../database-engine/availability-groups/windows/basic-availability-groups-always-on-availability-groups.md)」を参照してください。    

##  <a name="RDBMSSP"></a> RDBMS のスケーラビリティとパフォーマンス  
  
|機能|Enterprise|Standard|Web|Express|  
|-------------|----------------|--------------|---------|------------------------| 
|列ストア <sup>1</sup>|はい|[はい]|[はい]|はい|  
|クラスター化列ストア インデックス内のラージ オブジェクト バイナリ|はい|[はい]|[はい]|はい|  
|オンライン非クラスター化列ストア インデックスの再構築|はい|いいえ|いいえ|いいえ|
|インメモリ OLTP <sup>1</sup>|はい|[はい]|[はい]|はい|
|恒久的なメイン メモリ|はい|[はい]|[はい]|はい|
|テーブルとインデックスのパーティション分割|はい|[はい]|[はい]|はい|  
|データ圧縮|はい|[はい]|[はい]|はい|
|[リソース ガバナー]|はい|いいえ|いいえ|いいえ|  
|パーティション テーブルの並列処理|はい|いいえ|いいえ|いいえ|
|NUMA 対応のラージ ページ メモリとバッファー配列の割り当て|はい|いいえ|いいえ|いいえ|
|IO リソース管理|はい|いいえ|いいえ|いいえ|  
|遅延持続性|はい|[はい]|[はい]|はい|
|自動調整|はい|いいえ|いいえ|いいえ|
|バッチ モードの適応型結合|はい|いいえ|いいえ|いいえ|
|バッチ モード メモリ許可フィードバック|はい|いいえ|いいえ|いいえ|
|複数ステートメントのテーブル値関数のインターリーブ実行|はい|[はい]|[はい]|はい|
|一括挿入の機能強化|はい|[はい]|[はい]|はい|


<sup>1</sup> インメモリ OLTP データ サイズおよび列ストア セグメント キャッシュは、「スケールの制限」セクションでエディションごとに指定されているメモリ量に制限されます。 並列処理には最大限度があります。 インデックスの構築のプロセスの並列処理 (DOP) の度合いは、Standard edition では 2 DOP と Web および Express エディションでは 1 DOP に制限されます。 これは、ディスク ベース テーブルとメモリ最適化テーブルで作成された列ストア インデックスに当てはまります。

##  <a name="RDBMSS"></a> RDBMS のセキュリティ  
  
|機能|Enterprise|Standard|Web|Express|
|-------------|----------------|--------------|---------|------------------------------------| 
|行レベルのセキュリティ|はい|[はい]|[はい]|はい|  
|Always Encrypted|はい|[はい]|[はい]|はい| 
|動的なデータ マスキング|はい|[はい]|[はい]|はい|   
|基本的な監査|はい|[はい]|[はい]|はい| 
|詳細な監査|はい|[はい]|[はい]|はい| 
|透過的なデータベースの暗号化|はい|いいえ|いいえ|いいえ|   
|ユーザー定義ロール|はい|[はい]|[はい]|はい| 
|包含データベース|はい|[はい]|[はい]|はい| 
|バックアップの暗号化|はい|[はい]|いいえ|いいえ|  

##  <a name="RDBMSM"></a> RDBMS の管理の容易性  
  
|機能|Enterprise|Standard|Web|Express|   
|-------------|----------------|--------------|---------|------------------------|  
|専用管理者接続|はい|[はい]|はい|はい (トレース フラグを使用)|はい (トレース フラグを使用)|   
|PowerShell スクリプティングのサポート|はい|[はい]|[はい]|はい| 
|データ層アプリケーション コンポーネントの操作のサポート - 抽出、配置、アップグレード、削除|はい|[はい]|[はい]|はい| 
|ポリシー オートメーション (変更時とスケジュールに基づいて確認)|はい|[はい]|[はい]|いいえ|いいえ|   
|パフォーマンス データ コレクター|はい|[はい]|[はい]|いいえ|いいえ| 
|標準的なパフォーマンス レポート|はい|[はい]|[はい]|いいえ|いいえ| 
|プラン ガイドおよびプラン ガイドの固定計画|はい|[はい]|[はい]|いいえ|いいえ|   
|NOEXPAND ヒントを使用したインデックス付きビューの直接クエリ|はい|[はい]|[はい]|はい| 
|インデックス付きビューの自動メンテナンス|はい|[はい]|[はい]|いいえ|いいえ| 
|分散パーティション ビュー|はい|いいえ|いいえ|いいえ| 
|並列インデックス操作|はい|いいえ|いいえ|いいえ|  
|クエリ オプティマイザーによる自動的なインデックス付きのビュー使用|はい|いいえ|いいえ|いいえ| 
|並列整合性チェック|はい|いいえ|いいえ|いいえ| 
|SQL Server ユーティリティ コントロール ポイント|はい|いいえ|いいえ|いいえ|    

##  <a name="Programmability"></a> Programmability  
  
|機能|Enterprise|Standard|Web|Express 
|-------------|----------------|--------------|---------|------------------------|  
|JSON|はい|[はい]|[はい]|はい|   
|クエリ ストア|はい|[はい]|[はい]|はい|   
|テンポラル|はい|[はい]|[はい]|はい|   
|ネイティブ XML サポート|はい|[はい]|[はい]|はい| 
|XML インデックスの作成|はい|[はい]|[はい]|はい| 
|MERGE と UPSERT の機能|はい|[はい]|[はい]|はい|   
|日付および時刻データ型|はい|[はい]|[はい]|はい|  
|国際化サポート|はい|[はい]|[はい]|はい| 
|フルテキストおよびセマンティック検索|はい|[はい]|[はい]|[はい]|いいえ| 
|クエリ内の言語指定|はい|[はい]|[はい]|[はい]|いいえ|   
|Service Broker (メッセージング)|はい|はい|不可 (クライアントのみ)|不可 (クライアントのみ)|不可 (クライアントのみ)|   
|Transact-SQL エンドポイント|はい|[はい]|[はい]|いいえ|いいえ| 
|グラフ|はい|[はい]|[はい]|はい|  


<sup>1</sup> 複数のコンピューティング ノードでのスケール アウトにはヘッド ノードが必要です。

## <a name="IS"></a> Integration Services

各エディションでサポートされている Integration Services (SSIS) 機能について[!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)]を参照してください[Integration Services の機能が SQL Server のエディションでサポートされる](../integration-services/integration-services-features-supported-by-the-editions-of-sql-server.md)します。

##  <a name="SLS"></a> 空間およびロケーション サービス  
  
|機能名|Enterprise|Standard|Web|Express|  
|------------------|----------------|--------------|---------|------------------------------------|------------------------|
|空間インデックス|はい|[はい]|[はい]|はい|   
|平面データ型と測地データ型|はい|[はい]|[はい]|はい| 
|高度な空間的なライブラリ|はい|[はい]|[はい]|はい|   
|業界標準の空間データ形式のインポート/エクスポート|はい|[はい]|[はい]|はい|   

  
## <a name="next-steps"></a>次の手順 
 [各エディションと SQL Server 2017 - Windows のサポートされている機能](../sql-server/editions-and-components-of-sql-server-2017.md)  
 [各エディションと SQL Server 2016、Windows のサポートされている機能](../sql-server/editions-and-components-of-sql-server-2016.md)  
 [各エディションと SQL Server 2014 - Windows の機能がサポートされています。](https://msdn.microsoft.com/library/cc645993(v=sql.120).aspx)  
 [SQL Server をインストールする](../database-engine/install-windows/installation-for-sql-server-2016.md)  
 [SQL Server の製品仕様](https://msdn.microsoft.com/library/6445fd53-6844-4170-a86b-7fe76a9f64cb) 

  
  
