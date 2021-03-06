---
title: システムベーステーブル |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- system base tables [SQL Server]
- hobt [SQL Server]
- base tables
ms.assetid: 31f2df90-651f-4699-8067-19f59b60904f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 43f5e96a280614d3f69472c7d794489bf1a5ba58
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68029561"
---
# <a name="system-base-tables"></a>システム ベース テーブル
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  システム ベース テーブルは、特定のデータベースのメタデータを実際に格納する、基になるテーブルです。 **Master**データベースには、他のどのデータベースにも存在しない追加のテーブルが含まれているので、この点で特別なことです。 これらのテーブルには、サーバー全体のスコープを持つ永続化されたメタデータが含まれています。  
  
> [!IMPORTANT]  
>  システム ベース テーブルは、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]内のみで使用されるテーブルであり、一般ユーザーが使用するテーブルではありません。 これらは変更される可能性があり、互換性は保証されていません。  
  
## <a name="system-base-table-metadata"></a>システム ベース テーブルのメタデータ  
 データベースに対する CONTROL、ALTER、または VIEW DEFINITION 権限を持つ権限付与対象ユーザーは、システムベーステーブルのメタデータを使用して、システム**のカタログビュー**を表示できます。 権限付与対象ユーザーは、 [OBJECT_NAME](../../t-sql/functions/object-name-transact-sql.md)や[OBJECT_ID](../../t-sql/functions/object-id-transact-sql.md)などの組み込み関数を使用して、システムベーステーブルの名前とオブジェクト id を解決することもできます。  
  
 システムベーステーブルにバインドするには、ユーザーが専用管理者接続 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DAC) を使用してのインスタンスに接続する必要があります。 DAC で接続せずにシステム ベース テーブルから SELECT クエリを実行しようとすると、エラーが発生します。  
  
> [!IMPORTANT]  
>  DAC を使用したシステムベーステーブルへのアクセスは[!INCLUDE[msCoName](../../includes/msconame-md.md)] 、担当者向けに設計されており、サポートされている顧客シナリオではありません。  
  
## <a name="system-base-tables"></a>システム ベース テーブル  
 次の表に、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のシステム ベース テーブルの一覧とその説明を示します。  
  
|ベーステーブル|[説明]|  
|----------------|-----------------|  
|**sys.sysschobjs**|すべてのデータベースに存在します。 各行は、データベース内のオブジェクトを表します。|  
|**sysbinobjs**|すべてのデータベースに存在します。 データベース内の Service Broker エンティティごとに1行のデータを格納します。 Service Broker エンティティには次のものがあります。<br /><br /> メッセージ型<br /><br /> サービスコントラクト<br /><br /> サービス<br /><br /> 名前および型では、固定されているバイナリ照合順序を使用します。|  
|**sys.sysclsobjs**|すべてのデータベースに存在します。 次のような共通プロパティを共有する、分類されたエンティティごとに1行の情報を格納します。<br /><br /> アセンブリ<br /><br /> バックアップ デバイス<br /><br /> フルテキスト カタログ<br /><br /> パーティション関数<br /><br /> パーティション構成<br /><br /> ファイルグループ<br /><br /> 隠ぺいキー|  
|**sys.sysnsobjs**|すべてのデータベースに存在します。 名前空間スコープのエンティティごとに1行の値を格納します。 このテーブルは、XML コレクション エンティティの格納に使用されます。|  
|**sys.syscolpars**|すべてのデータベースに存在します。 テーブル、ビュー、またはテーブル値関数内のすべての列に対応する行が含まれています。 また、プロシージャまたは関数のパラメーターごとの行も格納します。|  
|**sys.systypedsubobjs**|すべてのデータベースに存在します。 型指定されたサブエンティティごとに 1 行のデータを格納します。 パーティション関数のパラメーターだけがこのカテゴリに分類されます。|  
|**sys.sysidxstats**|すべてのデータベースに存在します。 テーブルおよびインデックス付きビューのインデックスまたは統計ごとに 1 行のデータを格納します。<br /><br /> 注: すべてのインデックス (ヒープを除く) は、インデックスと同じ名前の統計に関連付けられています。|  
|**sysiscols**|すべてのデータベースに存在します。 保持されるインデックスと統計の列ごとに1行のデータを格納します。|  
|**sysscalartypes**|すべてのデータベースに存在します。 ユーザー定義型またはシステム型ごとに1行の値を格納します。|  
|**sys.sysdbreg**|**Master**データベースのみに存在します。 登録されたデータベースごとに 1 行のデータを格納します。|  
|**sys.sysxsrvs**|**Master**データベースのみに存在します。 ローカル サーバー、リンク サーバー、またはリモート サーバーごとに 1 行のデータを格納します。|  
|**sys.sysrmtlgns**|このシステムベーステーブルは、 **master**データベースにのみ存在します。 リモートログインマッピングごとに1行の値を格納します。 対応するサーバーから送信されてきたと称する受信ログインを、実際のローカル ログインにマップするために使用します。|  
|**syslnklgns**|**Master**データベースのみに存在します。 リンク ログイン マッピングごとに 1 行のデータを格納します。 リンクされたログインのマッピングは、リモートプロシージャコールおよびローカルサーバーから対応するリンクサーバーに送信される分散クエリによって使用されます。|  
|**sys. sysxlgns**|**Master**データベースのみに存在します。 サーバープリンシパルごとに1行の値を格納します。|  
|**sys.sysdbfiles**|すべてのデータベースに存在します。 列**dbid**が0の場合、行はこのデータベースに属するファイルを表します。 **Master**データベースでは、列**dbid**を0以外にすることができます。 その場合、該当する行は master ファイルを表します。|  
|**sys.sysusermsg**|**Master**データベースのみに存在します。 各行は、ユーザー定義のエラーメッセージを表します。|  
|**sys.sysprivs**|すべてのデータベースに存在します。 データベース レベルまたはサーバー レベルの権限ごとに 1 行のデータを格納します。<br /><br /> 注: サーバーレベルの権限は**master**データベースに格納されます。|  
|**sys.sysowners**|すべてのデータベースに存在します。 各行は、データベースプリンシパルを表します。|  
|**sys.sysobjkeycrypts**|すべてのデータベースに存在します。 オブジェクトに関連付けられた対称キー、暗号化、または暗号化プロパティごとに1行の値を格納します。|  
|**sys.syscerts**|すべてのデータベースに存在します。 データベース内の証明書ごとに 1 行のデータを格納します。|  
|**sys.sysasymkeys**|すべてのデータベースに存在します。 各行は、非対称キーを表します。|  
|**ftinds**|すべてのデータベースに存在します。 データベース内のフルテキスト インデックスごとに 1 行のデータを格納します。|  
|**sys. sysxprops**|すべてのデータベースに存在します。 拡張プロパティごとに 1 行のデータを格納します。|  
|**sys.sysallocunits**|すべてのデータベースに存在します。 ストレージアロケーションユニットごとに1行のデータを格納します。|  
|**sys.sysrowsets**|すべてのデータベースに存在します。 インデックスまたはヒープのパーティション行セットごとに1行の値を格納します。|  
|**sys.sysrowsetrefs**|すべてのデータベースに存在します。 行セット参照へのインデックスごとに1行の値を格納します。|  
|**sys. syslogshippers 業者**|**Master**データベースのみに存在します。 データベース ミラーリング監視サーバーごとに 1 行のデータを格納します。|  
|**sys.sysremsvcbinds**|すべてのデータベースに存在します。 リモートサービスバインドごとに1行の値を格納します。|  
|**sys.sysconvgroup**|すべてのデータベースに存在します。 Service Broker 内のサービスインスタンスごとに1行の値を格納します。|  
|**sysxmitqueue**|すべてのデータベースに存在します。 Service Broker 転送キューごとに1行の値を格納します。|  
|**sys. sysdesend**|すべてのデータベースに存在します。 Service Broker メッセージ交換の送信エンドポイントごとに 1 行のデータを格納します。|  
|**sys.sysdercv**|すべてのデータベースに存在します。 Service Broker メッセージ交換の受信エンドポイントごとに1行の値を格納します。|  
|**sys. sysendpts**|**Master**データベースのみに存在します。 サーバー内で作成されたエンドポイントごとに 1 行のデータを格納します。|  
|**syswebmethods**|**Master**データベースのみに存在します。 サーバーで作成される SOAP 対応 HTTP エンドポイントで定義されている SOAP メソッドごとに1行の値を格納します。|  
|**sys.sysqnames**|すべてのデータベースに存在します。 4バイト ID トークンの名前空間または修飾名ごとに1行のデータを格納します。|  
|**sys. sysxmlcomponent**|すべてのデータベースに存在します。 各行は、XML スキーマ コンポーネントを表します。|  
|**sys. sysxmlfacet**|すべてのデータベースに存在します。 XML 型定義の XML ファセット (制限) ごとに1行の値を格納します。|  
|**sys. sysxmlplacement**|すべてのデータベースに存在します。 XML コンポーネントの XML 配置ごとに 1 行のデータを格納します。|  
|**sys.syssingleobjrefs**|すべてのデータベースに存在します。 一般的な N 対 1 参照ごとに 1 行のデータを格納します。|  
|**sys.sysmultiobjrefs**|すべてのデータベースに存在します。 一般的な N から N への参照ごとに1行の値を格納します。|  
|**sys. sysobjvalues**|すべてのデータベースに存在します。 エンティティの一般値プロパティごとに1行の値を格納します。|  
|**sys.sysguidrefs**|すべてのデータベースに存在します。 GUID で分類された ID 参照ごとに 1 行のデータを格納します。|  
  
  
