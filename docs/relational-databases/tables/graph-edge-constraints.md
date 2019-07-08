---
title: グラフのエッジ制約 | Microsoft Docs
ms.custom: ''
ms.date: 06/21/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- edge constraints [SQL Server]
- CONNECTION constraints
- edge constraints [Azure SQL Database]
- graph edge constraints
- SQL Graph
author: shkale-msft
ms.author: shkale
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current||=azuresqldb-current'
ms.openlocfilehash: aa73858e6df29c814821ee9e24923cbfc0fbd4a2
ms.sourcegitcommit: 630f7cacdc16368735ec1d955b76d6d030091097
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/24/2019
ms.locfileid: "67343893"
---
# <a name="edge-constraints"></a>エッジ制約

[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md.md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

エッジ制約を使用して、データの整合性と特定のセマンティクスを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] グラフ データベース内のエッジ テーブルに適用できます。

##  <a name="Connection"></a> エッジ制約
 グラフ機能の初回のリリースでは、エッジ テーブルでエッジのエンドポイントに対して強制できることは何もありませんでした。 つまり、グラフ データベース内のエッジは、その種類に関係なく、任意のノードを他の任意のノードに接続することができました。 

 今回のリリースにはエッジ制約が導入され、ユーザーは、各自のエッジ テーブルに制約を追加することで特定のセマンティクスを適用でき、データの整合性も管理できます。 エッジ制約を持つエッジ テーブルに新しいエッジが追加される場合、[!INCLUDE[ssDE](../../includes/ssde-md.md)] では、エッジが接続を試みるノードが適切なノード テーブルに存在している必要があります。 また、ノードがエッジによって参照されている場合は、ノードを削除することはできません。 

 ### <a name="edge-constraint-clauses"></a>エッジ制約句
 各エッジ制約は、1 つまたは複数のエッジ制約句で構成されます。 1 つのエッジ制約句は、特定のエッジが接続する FROM ノードと TO ノードのペアです。 

 グラフ内に `Product` ノードと `Customer` ノードがあり、`Bought` エッジを使用してこれらのノードを接続することを考えてください。 エッジ制約句には、FROM ノードと TO ノードのペアとエッジの方向が指定されます。 この場合、エッジ制約句は `Customer` TO `Product` になります。 つまり、`Customer` から `Product` 方向への `Bought` の挿入が許可されます。 `Product` から `Customer` 方向へのエッジを挿入する試みは失敗します。 
  
- エッジ制約句には、エッジ制約が適用される FROM ノードと TO ノードのペアが含まれます。 
  
- ユーザーは、エッジ制約ごとに複数のエッジ制約句を指定でき、それらは論理和演算として適用されます。

- 1 つのエッジ テーブルに複数のエッジ制約が作成される場合、エッジはすべての制約を満たす必要があります。
  
### <a name="indexes-on-edge-constraints"></a>エッジ制約のインデックス
 エッジ制約を作成しても、エッジ テーブルの `$from_id` 列と `$to_id` 列の対応するインデックスは自動的に作成されることはありません。 ポイント ルックアップ クエリまたは OLTP ワークロードがある場合は、`$from_id`と `$to_id` のペアに対するインデックスを手動で作成することをお勧めします。 

##  <a name="Tasks"></a> 関連タスク  
 次の表は、エッジ制約に関連する一般的なタスクの一覧です。  
  
|タスク|[アーティクル]|  
|----------|-----------|  
|エッジ制約の作成方法について説明します。|[エッジ制約を作成する](../../relational-databases/tables/create-edge-constraints.md)|  
|エッジ制約の削除方法について説明します。|[エッジ制約を削除する](../../relational-databases/tables/delete-edge-constraint.md)|  
|エッジ制約の変更方法について説明します。|[エッジ制約を変更する](../../relational-databases/tables/modify-edge-constraint.md)|  
|エッジ制約のプロパティの表示方法について説明します。|[エッジ制約のプロパティを表示する](../../relational-databases/tables/view-edge-constraint-properties.md)|  
| SQL Server でのグラフ テクノロジの概要 | [SQL Server と Azure SQL Database でのグラフ処理](../graphs/sql-graph-overview.md) |
| &nbsp; | &nbsp; |
