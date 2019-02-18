---
title: sp_addpublication (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addpublication_TSQL
- sp_addpublication
helpviewer_keywords:
- sp_addpublication
ms.assetid: c7167ed1-2b7e-4824-b82b-65f4667c4407
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c39d3b5dc054de3e9433e5f90b706bfc9fead7ee
ms.sourcegitcommit: 78e32562f9c1fbf2e50d3be645941d4aa457e31f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54100917"
---
# <a name="spaddpublication-transact-sql"></a>sp_addpublication (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  スナップショット パブリケーションまたはトランザクション パブリケーションを作成します。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_addpublication [ @publication = ] 'publication'  
    [ , [ @taskid = ] tasked ]  
    [ , [ @restricted = ] 'restricted' ]  
    [ , [ @sync_method = ] 'sync_method' ]  
    [ , [ @repl_freq = ] 'repl_freq' ]  
    [ , [ @description = ] 'description' ]  
    [ , [ @status = ] 'status' ]  
    [ , [ @independent_agent = ] 'independent_agent' ]  
    [ , [ @immediate_sync = ] 'immediate_sync' ]  
    [ , [ @enabled_for_internet = ] 'enabled_for_internet' ]  
    [ , [ @allow_push = ] 'allow_push'  
    [ , [ @allow_pull = ] 'allow_pull' ]  
    [ , [ @allow_anonymous = ] 'allow_anonymous' ]  
    [ , [ @allow_sync_tran = ] 'allow_sync_tran' ]  
    [ , [ @autogen_sync_procs = ] 'autogen_sync_procs' ]  
    [ , [ @retention = ] retention ]  
    [ , [ @allow_queued_tran= ] 'allow_queued_updating' ]  
    [ , [ @snapshot_in_defaultfolder= ] 'snapshot_in_default_folder' ]  
    [ , [ @alt_snapshot_folder= ] 'alternate_snapshot_folder' ]  
    [ , [ @pre_snapshot_script= ] 'pre_snapshot_script' ]  
    [ , [ @post_snapshot_script= ] 'post_snapshot_script' ]  
    [ , [ @compress_snapshot= ] 'compress_snapshot' ]  
    [ , [ @ftp_address = ] 'ftp_address' ]  
    [ , [ @ftp_port= ] ftp_port ]  
    [ , [ @ftp_subdirectory = ] 'ftp_subdirectory' ]  
    [ , [ @ftp_login = ] 'ftp_login' ]  
    [ , [ @ftp_password = ] 'ftp_password' ]  
    [ , [ @allow_dts = ] 'allow_dts' ]  
    [ , [ @allow_subscription_copy = ] 'allow_subscription_copy' ]  
    [ , [ @conflict_policy = ] 'conflict_policy' ]  
    [ , [ @centralized_conflicts = ] 'centralized_conflicts' ]   
    [ , [ @conflict_retention = ] conflict_retention ]  
    [ , [ @queue_type = ] 'queue_type' ]  
    [ , [ @add_to_active_directory = ] 'add_to_active_directory' ]  
    [ , [ @logreader_job_name = ] 'logreader_agent_name' ]  
    [ , [ @qreader_job_name = ] 'queue_reader_agent_name' ]  
    [ , [ @publisher = ] 'publisher' ]   
    [ , [ @allow_initialize_from_backup = ] 'allow_initialize_from_backup' ]  
    [ , [ @replicate_ddl = ] replicate_ddl ]  
    [ , [ @enabled_for_p2p = ] 'enabled_for_p2p' ]  
    [ , [ @publish_local_changes_only = ] 'publish_local_changes_only' ]  
    [ , [ @enabled_for_het_sub = ] 'enabled_for_het_sub' ]  
    [ , [ @p2p_conflictdetection = ] 'p2p_conflictdetection' ]  
    [ , [ @p2p_originator_id = ] p2p_originator_id  
    [ , [ @p2p_continue_onconflict = ] 'p2p_continue_onconflict'  
    [ , [ @allow_partition_switch = ] 'allow_partition_switch'  
    [ , [ @replicate_partition_switch = ]'replicate_partition_switch'  
```  
  
## <a name="arguments"></a>引数  
 [ **\@パブリケーション =**] **'**_パブリケーション_**'**  
 作成するパブリケーションの名前を指定します。 *パブリケーション*は**sysname**、既定値はありません。 この名前は、データベース内で一意であることが必要です。  
  
 [  **\@taskid =**] *taskid*  
 旧バージョンとの互換性だけです。 サポートされています使用して、 [sp_addpublication_snapshot &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md)します。  
  
 [ **\@制限付き =**] **'**_制限_**'**  
 旧バージョンとの互換性だけです。 サポートされています使用して、 *default_access*します。  
  
 [  **\@sync_method =**] _' sync_method_**'**  
 同期モードを指定します。 *sync_method*は**nvarchar (13)** 値は次のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**native**|すべてのテーブルのネイティブ モード BCP 出力を作成する。 *Oracle パブリッシャーに対してはサポートされていません*します。|  
|**character**|すべてのテーブルのキャラクタモード BCP 出力を作成する。 _Oracle パブリッシャーの場合、_ **文字**_はスナップショット レプリケーションでのみ有効です_します。|  
|**同時実行**|すべてのテーブルのネイティブ モード BCP 出力を作成するが、スナップショット中はテーブルをロックしない。 トランザクション パブリケーションでのみサポートされます。 *Oracle パブリッシャーに対してはサポートされていません*します。|  
|**concurrent_c**|すべてのテーブルのキャラクタモードの BCP 出力を作成するが、スナップショット中はテーブルをロックしない。 トランザクション パブリケーションでのみサポートされます。|  
|**データベース スナップショット**|データベース スナップショットから、すべてのテーブルのネイティブ モードの一括コピー プログラム出力を作成します。 データベース スナップショットは、すべてのエディションで使用可能な[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の各エディションでサポートされる機能の一覧については、「 [SQL Server 2016 の各エディションがサポートする機能](~/sql-server/editions-and-supported-features-for-sql-server-2016.md)」を参照してください。|  
|**データベース スナップショットの文字**|データベース スナップショットから、すべてのテーブルのキャラクター モードの一括コピー プログラム出力を作成します。 データベース スナップショットは、すべてのエディションで使用可能な[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の各エディションでサポートされる機能の一覧については、「 [SQL Server 2016 の各エディションがサポートする機能](~/sql-server/editions-and-supported-features-for-sql-server-2016.md)」を参照してください。|  
|NULL (既定値)|既定値は**ネイティブ**の[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。 非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーの場合、既定値は**文字**ときの値*repl_freq*は**スナップショット**と**concurrent_c**それ以外の場合。|  
  
 [  **\@repl_freq =**] **'**_repl_freq_**'**  
 レプリケーションの頻度の種類は、 *repl_freq*は**nvarchar (10)** 値は次のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**継続的な**(既定値)|すべてのログベースのトランザクションの出力をパブリッシュする。 非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーの場合、このことが必要*sync_method*に設定する**concurrent_c**します。|  
|**スナップショット**|スケジュールされた同期イベントのみをパブリッシュする。 非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーの場合、このことが必要*sync_method*に設定する**文字**します。|  
  
 [ **\@説明 =**] **'**_説明_**'**  
 パブリケーションに関する説明を指定します (省略可能)。 *説明*は**nvarchar (255)**、既定値は NULL です。  
  
 [ **\@状態 =**] **'**_状態_**'**  
 パブリケーション データを使用できるかどうかを指定します。 *ステータス*は**nvarchar (8)** 値は次のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**アクティブ**|サブスクライバーでパブリケーション データを直ちに使用できる。|  
|**非アクティブな**(既定値)|パブリケーションが最初に作成されたときは、サブスクライバーでパブリケーション データを使用できない (サブスクライブすることはできますが、サブスクリプションは処理されません)。|  
  
 *Oracle パブリッシャーに対してはサポートされていません*します。  
  
 [  **\@independent_agent =**] **'**_independent_agent_**'**  
 このパブリケーションに対して、スタンドアロン ディストリビューション エージェントが存在するかどうかを指定します。 *independent_agent*は**nvarchar (5)**、既定値は FALSE。 場合**true**、このパブリケーション用のスタンドアロン ディストリビューション エージェントが存在します。 場合**false**パブリケーションは共有ディストリビューション エージェント、およびパブリッシャー データベース/サブスクライバー データベースの各ペアが 1 つの共有エージェント。  
  
 [  **\@immediate_sync =**] **'**_immediate_synchronization_**'**  
 スナップショット エージェントが実行されるたびに、パブリケーションに対して同期ファイルが作成されるかどうかを指定します。 *immediate_synchronization*は**nvarchar (5)**、既定値は FALSE。 場合**true**、同期ファイルが作成またはスナップショット エージェントを実行するたびに再作成します。 サブスクリプションが作成される前にスナップショット エージェントが完了していれば、サブスクライバーでは直ちに同期ファイルを取得できます。 新しいサブスクリプションは、最近実行されたスナップショット エージェントによって生成された最新の同期ファイルを取得します。 *independent_agent*必要があります**true**の*immediate_synchronization*する**true**します。 場合**false**、新しいサブスクリプションがある場合にのみ、同期ファイルが作成されます。 呼び出す必要があります[sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)既存のパブリケーションを段階的に新しいアーティクルを追加するときに、サブスクリプションごとにします。 サブスクリプションの後、スナップショット エージェントが起動して完了するまでは、サブスクライバーでは同期ファイルを取得できません。  
  
 [  **\@enabled_for_internet =**] **'**_enabled_for_internet_**'**  
 パブリケーションをインターネット対応にするかどうかを指定し、サブスクライバーへのスナップショット ファイルの転送にファイル転送プロトコル (FTP) を使用できるかどうかを決定します。 *enabled_for_internet*は**nvarchar (5)**、既定値は FALSE。 場合**true**パブリケーションの同期ファイルは C:\Program files \microsoft SQL Server\MSSQL\MSSQL.x\Repldata\Ftp ディレクトリに格納します。 ユーザーは Ftp ディレクトリを作成する必要があります。  
  
 [  **\@allow_push =**] **'**_allow_push_**'**  
 特定のパブリケーションに対して、プッシュ サブスクリプションを作成できるかどうかを指定します。 *allow_push*は**nvarchar (5)**、既定値は TRUE、パブリケーションに対してプッシュ サブスクリプションを許可します。  
  
 [  **\@allow_pull =**] **'**_allow_pull_**'**  
 特定のパブリケーションに対して、プル サブスクリプションを作成できるかどうかを指定します。 *allow_pull*は**nvarchar (5)**、既定値は FALSE。 場合**false**、パブリケーションに対してプル サブスクリプションが許可されていません。  
  
 [  **\@allow_anonymous =**] **'**_allow_anonymous_**'**  
 特定のパブリケーションに対して、匿名サブスクリプションを作成できるかどうかを指定します。 *allow_anonymous*は**nvarchar (5)**、既定値は FALSE。 場合**true**、 *immediate_synchronization*に設定する必要がありますも**true**します。 場合**false**、パブリケーションに対して匿名サブスクリプションを許可しません。  
  
 [  **\@allow_sync_tran =**] **'**_allow_sync_tran_**'**  
 パブリケーションでサブスクリプションの即時更新を許可するかどうかを指定します。 *allow_sync_tran*は**nvarchar (5)**、既定値は FALSE。 **true**は*Oracle パブリッシャーに対してサポートされていません*します。  
  
 [  **\@autogen_sync_procs =**] **'**_autogen_sync_procs_**'**  
 更新サブスクリプションの同期ストアド プロシージャがパブリッシャーで生成されるかどうかを指定します。 *autogen_sync_procs*は**nvarchar (5)** 値は次のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**true**|更新サブスクリプションが有効の場合、自動的に生成される。|  
|**false**|更新サブスクリプションが無効の場合、または Oracle パブリッシャーの場合、自動的に生成される。|  
|NULL (既定値)|既定値は**true**更新サブスクリプションを有効にして**false**とサブスクリプションの更新が有効になっていません。|  
  
> [!NOTE]  
>  ユーザーが値を指定した*autogen_sync_procs*の指定した値によってオーバーライドされます*allow_queued_tran*と*allow_sync_tran*します。  
  
 [ **\@保有期間 =**]*保有期間*  
 サブスクリプション処理の保有期間を時間数で指定します。 *保有期間*は**int**、既定値は 336 時間です。 サブスクリプションは、保有期間内に非アクティブになると、期限切れとなって削除されます。 この値には、パブリッシャーによって使用されるディストリビューション データベースの最大保有期間を上回る値を指定することもできます。 場合**0**、パブリケーションに対するサブスクリプションのよく知られているが決して期限切れ、期限切れサブスクリプション クリーンアップ エージェントによって削除されます。  
  
 [  **\@allow_queued_tran =** ] **'**_allow_queued_updating_**'**  
 変更をパブリッシャーに適用できるようになるまで、サブスクライバーでの変更のキュー登録を有効または無効にします。 *allow_queued_updating*は**nvarchar (5)** 既定値は FALSE。 場合**false**、サブスクライバーの変更はキュー登録されません。 **true**は*Oracle パブリッシャーに対してサポートされていません*します。  
  
 [  **\@snapshot_in_defaultfolder =** ] **'**_snapshot_in_default_folder_**'**  
 スナップショット ファイルを既定のフォルダーに格納するかどうかを指定します。 *snapshot_in_default_folder*は**nvarchar (5)** 既定値は TRUE。 場合**true**、スナップショット ファイルは既定のフォルダーにあります。 場合**false**、スナップショット ファイルがで指定された代替位置に格納されている*alternate_snapshot_folder*します。 代替位置は、他のサーバー、ネットワーク ドライブ、CD-ROM やリムーバブル ディスクなどのリムーバブル メディアに設定できます。 スナップショット ファイルを FTP サイトに保存し、後でサブスクライバーで取得することもできます。 このパラメーターが true し、もに、場所があることができますに注意してください、  **\@alt_snapshot_folder**パラメーター。 これらのパラメーターを組み合わせて指定した場合、スナップショット ファイルは、既定のフォルダーと代替位置の両方に格納されます。  
  
 [  **\@alt_snapshot_folder =** ] **'**_alternate_snapshot_folder_**'**  
 スナップショットの代替フォルダーの場所を指定します。 *alternate_snapshot_folder*は**nvarchar (255)** 既定値は NULL です。  
  
 [  **\@pre_snapshot_script =** ] **'**_pre_snapshot_script_**'**  
 ポインターを指定します、 **.sql**ファイルの場所。 *pre_snapshot_script*は**nvarchar (255)、** 既定値は NULL です。 ディストリビューション エージェントでは、サブスクライバーでスナップショットが適用されるとき、レプリケートされたオブジェクト スクリプトよりも前に、プリスナップショット スクリプトが実行されます。 このスクリプトは、サブスクリプション データベースへの接続時にディストリビューション エージェントによって使用されるセキュリティ コンテキストで実行されます。  
  
 [  **\@post_snapshot_script =** ] **'**_post_snapshot_script_**'**  
 ポインターを指定します、 **.sql**ファイルの場所。 *post_snapshot_script*は**nvarchar (255)**、既定値は NULL です。 最初の同期時、ディストリビューション エージェントでは、他のすべてのレプリケートされたオブジェクト スクリプトとデータが適用された後、ポスト スナップショット スクリプトが実行されます。 このスクリプトは、サブスクリプション データベースへの接続時にディストリビューション エージェントによって使用されるセキュリティ コンテキストで実行されます。  
  
 [  **\@compress_snapshot =** ] **'**_compress_snapshot_**'**  
 指定に書き込まれたスナップショット、  **\@alt_snapshot_folder**の場所を圧縮するには、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] CAB 形式です。 *compress_snapshot*は**nvarchar (5)**、既定値は FALSE。 **false**こと、スナップショットは圧縮されません。 を指定します。**true**スナップショットが圧縮されることを指定します。 2 GB を超えるスナップショット ファイルは圧縮できません。 圧縮されたスナップショット ファイルは、ディストリビューション エージェントが実行される場所に展開されます。プル サブスクリプションでは通常、ファイルがサブスクライバーで展開されるよう、圧縮されたスナップショットが使用されます。 既定のフォルダー内のスナップショットは圧縮できません。  
  
 [  **\@ftp_address =** ] **'**_ftp_address_**'**  
 ディストリビューター用の FTP サービスのネットワーク アドレスです。 *ftp_address*は**sysname**、既定値は NULL です。 ここでは、サブスクライバーのディストリビューション エージェントまたはマージ エージェントがパブリケーション スナップショット ファイルを取得する場所を指定します。 各パブリケーションを別に持つことができますので、このプロパティはパブリケーションごとに格納されている、 *ftp_address*します。 パブリケーションでは、FTP を使用したスナップショットの配布がサポートされている必要があります。  
  
 [  **\@ftp_port =** ] *ftp_port*  
 ディストリビューター用の FTP サービスのポート番号です。 *ftp_port*は**int**、既定値は 21 です。 サブスクライバーのディストリビューション エージェントまたはマージ エージェントがパブリケーション スナップショット ファイルを取得する場所を示します。 このプロパティはパブリケーションごとに格納されている、ために各パブリケーションが持つことができます独自*ftp_port*します。  
  
 [  **\@ftp_subdirectory =** ] **'**_ftp_subdirectory_**'**  
 パブリケーションで FTP を利用したスナップショット配布がサポートされている場合に、サブスクライバーのディストリビューション エージェントまたはマージ エージェントがパブリケーション スナップショット ファイルを取得する場所。 *ftp_subdirectory*は**nvarchar (255)**、既定値は NULL です。 このプロパティはパブリケーションごとに格納されている、ために各パブリケーションが持つことができます独自*ftp_subdirctory*に NULL 値を持つ、サブディレクトリがないこともできます。  
  
 [  **\@ftp_login =** ] **'**_ftp_login_**'**  
 FTP サービスに接続するときに使用するユーザー名です。 *ftp_login*は**sysname**、既定値は ANONYMOUS です。  
  
 [  **\@ftp_password =** ] **'**_ftp_password_**'**  
 FTP サービスに接続するときに使用するユーザー パスワードです。 *ftp_password*は**sysname**、既定値は NULL です。  
  
 [  **\@allow_dts を含む =** ] **'**_allow_dts を含む_**'**  
 パブリケーションでデータを変換できるかどうかを指定します。 サブスクリプションを作成するときに DTS パッケージを指定できます。 *allow_transformable_subscriptions*は**nvarchar (5)** 既定値は FALSE には、これはいない DTS 変換が許可されます。 ときに*allow_dts を含む*が true の場合*sync_method*する必要がありますに設定する**文字**または**concurrent_c**します。  
  
 **true**は*Oracle パブリッシャーに対してサポートされていません*します。  
  
 [  **\@allow_subscription_copy =** ] **'**_allow_subscription_copy_**'**  
 このパブリケーションにサブスクライブするサブスクリプション データベースをコピーする機能を有効または無効にします。 *allow_subscription_copy*は**nvarchar (5)**、既定値は FALSE。  
  
 [  **\@conflict_policy =** ] **'**_conflict_policy_**'**  
 キュー更新サブスクライバー オプションを使用するときの競合の解決方法。 *conflict_policy*は**nvarchar (100)** 既定値は null の場合、次の値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**pub wins**|パブリッシャーを優先。|  
|**sub reinit**|サブスクライバーを再初期化。|  
|**sub wins**|サブスクライバーを優先。|  
|NULL (既定値)|Null の場合、およびパブリケーションがスナップショット パブリケーションの場合、既定のポリシーは次のようになります。 **sub reinit**します。 NULL で、パブリケーションがスナップショット パブリケーションでない場合、既定値は次のようになります。 **pub wins**します。|  
  
 *Oracle パブリッシャーに対してはサポートされていません*します。  
  
 [  **\@centralized_conflicts =** ] **'**_centralized_conflicts_**'**  
 パブリッシャーに競合レコードを格納するかどうかを指定します。 *centralized_conflicts*は**nvarchar (5)**、既定値は TRUE。 場合**true**、競合レコードはパブリッシャーに保存されます。 場合**false**、競合レコードはパブリッシャー側の両方と、競合の原因となったサブスクライバーで格納されます。 *Oracle パブリッシャーに対してはサポートされていません*します。  
  
 [  **\@conflict_retention =** ] *conflict_retention*  
 競合の保有期間の日数を指定します。 これは、ピア ツー ピア トランザクション レプリケーションおよびキュー更新サブスクリプションの競合メタデータが格納される期間です。 *conflict_retention*は**int**、既定値は 14 です。 *Oracle パブリッシャーに対してはサポートされていません*します。  
  
 [  **\@queue_type =** ] **'**_queue_type_**'**  
 使用されるキューの種類。 *queue_type*は**nvarchar (10)**、既定値は null の場合、これらの値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**sql**|トランザクションの保存に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を使用。|  
|NULL (既定値)|既定値は**sql**、使用することを指定する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]トランザクションを格納します。|  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Message Queuing (MSMQ) の使用は現在サポートされていません。 値を指定する**msmq** 、警告が発生して、レプリケーションの値自動的に設定されます**sql**します。  
  
 *Oracle パブリッシャーに対してはサポートされていません*します。  
  
 [  **\@add_to_active_directory =** ] **'**_追加_*\_*_to_active_directory_**'**  
 このパラメーターは、旧バージョンのスクリプトとの互換性を保つために用意されており、非推奨とされます。 現在、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Active Directory にはパブリケーション情報を追加できません。  
  
 [  **\@logreader_job_name =** ] **'**_logreader_agent_name_**'**  
 既存のエージェント ジョブの名前を指定します。 *logreader_agent_name*は**sysname**既定値は NULL です。 このパラメーターは、ログ リーダー エージェントで、新しく作成されるジョブではなく既存のジョブが使用される場合にのみ指定します。  
  
 [  **\@qreader_job_name =** ] **'**_queue_reader_agent_name_**'**  
 既存のエージェント ジョブの名前を指定します。 *queue_reader_agent_name*は**sysname**既定値は NULL です。 このパラメーターは、キュー リーダー エージェントで、新しく作成されるジョブではなく既存のジョブが使用される場合にのみ指定します。  
  
 [  **\@publisher =** ] **'**_パブリッシャー_**'**  
 以外を指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。 *パブリッシャー*は**sysname**、既定値は NULL です。  
  
> [!NOTE]  
>  *パブリッシャー*にパブリケーションを追加するときに使用されません、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。  
  
 [  **\@allow_initialize_from_backup =** ] **'**_allow_initialize_from_backup_**'**  
 サブスクライバーでは、最初のスナップショットではなくバックアップから、このパブリケーションへのサブスクリプションを初期化できるかどうかを示します。 *allow_initialize_from_backup*は**nvarchar (5)**、これらの値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**true**|バックアップからの初期化を有効にする。|  
|**false**|バックアップからの初期化を無効にする。|  
|NULL (既定値)|既定値は**true** 、ピア ツー ピア レプリケーション トポロジでパブリケーションのおよび**false**の他のすべてのパブリケーション。|  
  
 詳細については、「 [Initialize a Transactional Subscription Without a Snapshot](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)を使用して、サブスクリプションを手動で初期化する方法について説明します。  
  
> [!WARNING]  
>  サブスクライバー データの欠落を回避するために、 **sp_addpublication** で `@allow_initialize_from_backup = N'true'`を使用する場合は、常に `@immediate_sync = N'true'`を使用します。  
  
 [  **\@replicate_ddl =** ] *replicate_ddl*  
 スキーマ レプリケーションがパブリケーションに対してサポートされているかどうかを示します。 *replicate_ddl*は**int**、既定値は**1**の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーと**0**の非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャー。 **1** 、パブリッシャーで実行されるデータ定義言語 (DDL) ステートメントがレプリケートされることを示しますと**0** DDL ステートメントがレプリケートされないことを示します。 *スキーマ レプリケーションが Oracle パブリッシャーに対してサポートされていません。* 詳細については、「[パブリケーション データベースでのスキーマの変更](../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)」を参照してください。  
  
 *\@Replicate_ddl* DDL ステートメントは、列を追加するときは、パラメーターを有効にします。 *\@Replicate_ddl* DDL ステートメントが変更または次の理由により、列を削除するときに、パラメーターは無視されます。  
  
-   列が削除されるとき、ディストリビューション エージェントは失敗の原因となる、削除された列を含むから新しい DML ステートメントを防ぐために sysarticlecolumns を更新する必要があります。 *\@Replicate_ddl*レプリケーションは、スキーマの変更を常にレプリケートする必要がありますので、パラメーターは無視されます。  
  
-   列が変更される場合は、ソースのデータ型または NULL 値の許容属性が変更され、サブスクライバーにあるテーブルと互換性のない値が DML ステートメントに含まれる可能性があります。 そうした DML ステートメントは、ディストリビューション エージェントが失敗する原因となる場合があります。 *\@Replicate_ddl*レプリケーションは、スキーマの変更を常にレプリケートする必要がありますので、パラメーターは無視されます。  
  
-   DDL ステートメントは、新しい列を追加するときに sysarticlecolumns では、新しい列が含まれません。 DML ステートメントによって、新しい列のデータがレプリケートされることはありません。 DDL をレプリケートするかしないかのどちらかが許容されるため、パラメーターは有効になります。  
  
 [  **\@enabled_for_p2p =** ] **'**_enabled_for_p2p_**'**  
 ピア ツー ピア レプリケーション トポロジでパブリケーションを使用できるようにします。 *enabled_for_p2p*は**nvarchar (5)**、既定値は FALSE。 **true**パブリケーションがピア ツー ピア レプリケーションをサポートしていることを示します。 設定するときに*enabled_for_p2p*に**true**、次の制限が適用されます。  
  
-   *allow_anonymous*あります**false**します。  
  
-   *allow_dts を含む*あります**false**します。  
  
-   *allow_initialize_from_backup*あります**true**します。  
  
-   *allow_queued_tran*あります**false**します。  
  
-   *allow_sync_tran*あります**false**します。  
  
-   *conflict_policy*あります**false**します。  
  
-   *independent_agent*あります**true**します。  
  
-   *repl_freq*あります**連続**します。  
  
-   *replicate_ddl*あります**1**します。  
  
 詳細については、「 [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)」を参照してください。  
  
 [  **\@publish_local_changes_only =** ] **'**_publish_local_changes_only_**'**  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [  **\@enabled_for_het_sub =** ] **'**_enabled_for_het_sub_**'**  
 パブリケーションで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外のサブスクライバーのサポートを有効にします。 *enabled_for_het_sub*は**nvarchar (5)** で既定値は FALSE。 値**true**パブリケーションをサポートしている以外は意味[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サブスクライバー。 ときに*enabled_for_het_sub*は**true**、次の制限が適用されます。  
  
-   *allow_initialize_from_backup*あります**false**します。  
  
-   *allow_push*あります**true**します。  
  
-   *allow_queued_tran*あります**false**します。  
  
-   *allow_subscription_copy*あります**false**します。  
  
-   *allow_sync_tran*あります**false**します。  
  
-   *autogen_sync_procs*あります**false**します。  
  
-   *conflict_policy* NULL にする必要があります。  
  
-   *enabled_for_internet*あります**false**します。  
  
-   *enabled_for_p2p*あります**false**します。  
  
-   *ftp_address* NULL にする必要があります。  
  
-   *ftp_subdirectory* NULL にする必要があります。  
  
-   *ftp_password* NULL にする必要があります。  
  
-   *pre_snapshot_script* NULL にする必要があります。  
  
-   *post_snapshot_script* NULL にする必要があります。  
  
-   *replicate_ddl* 0 にする必要があります。  
  
-   *qreader_job_name* NULL にする必要があります。  
  
-   *queue_type* NULL にする必要があります。  
  
-   *sync_method*することはできません**ネイティブ**または**同時**します。  
  
 詳細については、「 [Non-SQL Server Subscribers](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md)」を参照してください。  
  
 [  **\@p2p_conflictdetection =** ] **'**_p2p_conflictdetection_**'**  
 パブリケーションでピア ツー ピア レプリケーションが有効である場合に、ディストリビューション エージェントが競合を検出できるようにします。 *p2p_conflictdetection*は**nvarchar (5)** を既定値は TRUE。 詳細については、「 [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md)」を参照してください。  
  
 [  **\@p2p_originator_id =** ] *p2p_originator_id*  
 ピア ツー ピア トポロジ内のノードの ID を指定します。 *p2p_originator_id*は**int**、既定値は NULL です。 場合、この ID は競合検出に対して使用*p2p_conflictdetection*が TRUE に設定します。 トポロジで使用されていない、正の値、0 以外の ID を指定します。 既に使用されている Id の一覧は、実行[sp_help_peerconflictdetection](../../relational-databases/system-stored-procedures/sp-help-peerconflictdetection-transact-sql.md)します。  
  
 [  **\@p2p_continue_onconflict =** ] **'**_p2p_continue_onconflict_**'**  
 競合の検出後にディストリビューション エージェントで変更の処理を続行するかどうかを示します。 *このとき p2p_continue_onconflict*は**nvarchar (5)** で既定値は FALSE。  
  
> [!CAUTION]  
>  既定値の FALSE を使用することをお勧めします。 このオプションを TRUE に設定すると、ディストリビューション エージェントは、発信元 ID が最も大きいノードから競合する行を適用してトポロジ内のデータを収束しようとします。 この方法では収束が保証されません。 競合が検出された後に、トポロジに一貫性があることを確認する必要があります。 詳細については、「 [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md)」の「競合の処理」を参照してください。  
  
  
 [  **\@allow_partition_switch =** ] **'**_allow_partition_switch_**'**  
 指定するかどうか ALTER TABLE.パブリッシュされたデータベースに対して SWITCH ステートメントを実行できます。 *allow_partition_switch*は**nvarchar (5)** で既定値は FALSE。 詳細については、「[パーティション テーブルとパーティション インデックスのレプリケート](../../relational-databases/replication/publish/replicate-partitioned-tables-and-indexes.md)」を参照してください。  
  
 [  **\@replicate_partition_switch =** ] **'**_replicate_partition_switch_**'**  
 指定するかどうか ALTER TABLE.パブリッシュされたデータベースに対して実行される SWITCH ステートメントをサブスクライバーにレプリケートする必要があります。 *replicate_partition_switch*は**nvarchar (5)** で既定値は FALSE。 このオプションは有効な場合にのみ*allow_partition_switch*が TRUE に設定します。  

## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_addpublication**スナップショット レプリケーションおよびトランザクション レプリケーションで使用されます。  
  
 同じデータベース オブジェクトを使用するパブリケーションのみをパブリッシュする複数のパブリケーションが存在しない場合、 *replicate_ddl* @property **1** ALTER TABLE、ALTER VIEW、ALTER PROCEDURE、ALTER FUNCTION、レプリケートとALTER TRIGGER DDL ステートメント。 ただし、ALTER TABLE DROP COLUMN DDL ステートメントは、削除された列をパブリッシュするすべてのパブリケーションでレプリケートされます。  
  
 DDL レプリケーションが有効になっている (*replicate_ddl* = **1**)、パブリケーションに対してレプリケーションなしの DDL 変更を行う、パブリケーション[sp_changepublication](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md)設定に最初に実行する必要があります*replicate_ddl*に**0**します。 レプリケーションなしの DDL ステートメントが実行された後[sp_changepublication](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md) DDL レプリケーションをオンにもう一度実行することができます。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_AddTranPub](../../relational-databases/replication/codesnippet/tsql/sp-addpublication-transa_1.sql)]  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_addpublication**します。 Windows 認証ログインを行うには、Windows ユーザー アカウントを表すユーザー アカウントがデータベースに必要です。 Windows グループを表すユーザー アカウントでは不十分です。  
  
## <a name="see-also"></a>参照  
 [sp_addlogreader_agent &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md)   
 [sp_addpublication_snapshot &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md)   
 [sp_changepublication (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md)   
 [sp_droppublication &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droppublication-transact-sql.md)   
 [sp_helppublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md)   
 [sp_replicationdboption &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md)   
 [データとデータベース オブジェクトのパブリッシュ](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
