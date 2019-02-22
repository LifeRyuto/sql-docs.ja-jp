---
title: 動的管理ビュー (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- database scoped dynamic management objects [SQL Server]
- dynamic management objects [SQL Server], about dynamic management objects
- server state information [SQL Server]
- dynamic management functions [SQL Server]
- metadata [SQL Server], dynamic management objects
- dynamic management views [SQL Server]
- DMVs [SQL Server]
- functions [SQL Server], dynamic management
- server scoped dynamic management objects [SQL Server]
- dynamic management objects [SQL Server]
ms.assetid: cf893ecb-0bf6-4cbf-ac00-8a1099e405b1
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1a61d3826cd7a4421eb621d549dfc49155ddadd0
ms.sourcegitcommit: b3d84abfa4e2922951430772c9f86dce450e4ed1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/22/2019
ms.locfileid: "56662746"
---
# <a name="system-dynamic-management-views"></a>システム動的管理ビュー
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  動的管理ビューと動的管理関数では、サーバーの状態情報が返されます。返された情報は、サーバー インスタンスのヘルス状態の監視、問題の診断、パフォーマンスのチューニングに使用できます。  
  
> [!IMPORTANT]  
>  動的管理ビューと動的管理関数では、実装固有の内部状態データが返されます。 これらのスキーマと返されるデータは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の将来のリリースで変更される可能性があります。 したがって、将来のリリースでは、このリリースの動的管理ビューおよび動的管理関数との互換性がなくなる場合があります。 たとえば、今後の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のリリースでは、列のリストの末尾に列を追加することにより、動的管理ビューの定義が拡張される可能性があります。 返される列の数が変化し、アプリケーションが機能しなくなる可能性があるため、製品コードでは `SELECT * FROM dynamic_management_view_name` という構文を使用しないことをお勧めします。  
  
 動的管理ビューと動的管理関数には次の 2 種類があります。  
  
-   サーバー スコープの動的管理ビューと動的管理関数。 これらには、サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
-   データベース スコープの動的管理ビューと動的管理関数。 これらには、データベースに対する VIEW DATABASE STATE 権限が必要です。  
  
## <a name="querying-dynamic-management-views"></a>動的管理ビューのクエリ  
 動的管理ビューは、[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントで 2 部、3 部、または 4 部構成の名前を使用して参照できます。 また動的管理関数は、[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントで 2 部または 3 部構成の名前を使用して参照できます。 動的管理ビューと動的管理関数は、[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントで 1 部構成の名前を使用して参照することはできません。  
  
 すべての動的管理ビューと動的管理関数は sys スキーマに含まれ、dm_* という名前付け規則に従います。 動的管理ビューまたは動的管理関数を使用するときには、sys スキーマを使用して、ビューまたは関数の名前にプレフィックスを付ける必要があります。 たとえば、動的管理ビュー dm_os_wait_stats をクエリするには、次のクエリを実行します。  
  
 ```sql
SELECT wait_type, wait_time_ms  
FROM sys.dm_os_wait_stats;  
```  
  
### <a name="required-permissions"></a>必要な権限  
 動的管理ビューまたは動的管理関数をクエリするには、オブジェクトに対する SELECT 権限と、VIEW SERVER STATE または VIEW DATABASE STATE 権限が必要です。 これらの権限を使用することにより、動的管理ビューと動的管理関数に対するユーザーまたはログインのアクセスを選択的に制限できます。 これを行うには、まず master にユーザーを作成し、次にアクセスを禁止する動的管理ビューまたは動的管理関数に対するユーザーの SELECT 権限を拒否します。 これで、このユーザーはデータベース コンテキストに関係なく、設定された動的管理ビューまたは動的管理関数を選択できなくなります。  
  
> [!NOTE]  
>  DENY は優先されるため、ユーザーに VIEW SERVER STATE 権限が許可され、VIEW DATABASE STATE 権限が拒否されている場合、そのユーザーはサーバー レベルの情報は参照できますが、データベース レベルの情報は参照できません。  
  
## <a name="in-this-section"></a>このセクションの内容  
 動的管理ビューと動的管理関数は次のカテゴリに分類されています。  
  
|||  
|-|-|  
|[Always On 可用性グループの動的管理ビューおよび関数 (TRANSACT-SQL)](../../relational-databases/system-dynamic-management-views/always-on-availability-groups-dynamic-management-views-functions.md)|[メモリ最適化テーブルの動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)|  
|[変更データ キャプチャに関連した動的管理ビュー &#40;Transact-SQL&#41;](change-data-capture-sys-dm-cdc-errors.md)|[オブジェクト関連の動的管理ビューおよび関数&#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/object-related-dynamic-management-views-and-functions-transact-sql.md)|  
|[変更の追跡関連の動的管理ビュー](change-tracking-sys-dm-tran-commit-table.md)|[通知関連の動的管理ビューに対してクエリを&#40;TRANSACT-SQL&#41;](query-notifications-sys-dm-qn-subscriptions.md)|  
|[共通言語ランタイム関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/common-language-runtime-related-dynamic-management-views-transact-sql.md)|[レプリケーション関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/replication-related-dynamic-management-views-transact-sql.md)|  
|[データベース ミラーリング関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](database-mirroring-sys-dm-db-mirroring-auto-page-repair.md)|[リソース ガバナー関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md)|  
|[データベース関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)|[セキュリティ関連の動的管理ビューおよび関数 &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/security-related-dynamic-management-views-and-functions-transact-sql.md)|  
|[実行関連の動的管理ビューおよび関数 &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)|[サーバー関連の動的管理ビューおよび関数 &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/server-related-dynamic-management-views-and-functions-transact-sql.md)|  
|[拡張イベントの動的管理ビュー](../../relational-databases/system-dynamic-management-views/extended-events-dynamic-management-views.md)|[Service Broker 関連の動的管理ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/service-broker-related-dynamic-management-views-transact-sql.md)|  
|[Filestream および FileTable 動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/filestream-and-filetable-dynamic-management-views-transact-sql.md)|[空間データ関連の動的管理ビューおよび関数&#40;TRANSACT-SQL&#41;](https://msdn.microsoft.com/library/c542ac38-451f-43a5-bf8c-4edd38bb738e)|  
|[フルテキスト検索とセマンティック検索の動的管理ビューおよび関数&#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)|[SQL Data Warehouse と Parallel Data Warehouse の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)|  
|[地理的レプリケーション動的管理ビューおよび関数&#40;Azure SQL Database&#41;](../../relational-databases/system-dynamic-management-views/geo-replication-dynamic-management-views-and-functions-azure-sql-database.md)|[SQL Server オペレーティング システム関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)|  
|[インデックス関連の動的管理ビューおよび関数&#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/index-related-dynamic-management-views-and-functions-transact-sql.md)|[Stretch Database の動的管理ビュー &#40;TRANSACT-SQL&#41;](https://msdn.microsoft.com/library/1193efce-a105-49a9-a8b8-26b063485567)|  
|[O 関連の動的管理ビューおよび関数&#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/i-o-related-dynamic-management-views-and-functions-transact-sql.md)|[トランザクション関連の動的管理ビューおよび関数 &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/transaction-related-dynamic-management-views-and-functions-transact-sql.md)|  

  
## <a name="see-also"></a>参照  
 [アクセス許可の付与 Server &#40;TRANSACT-SQL&#41;](../../t-sql/statements/grant-server-permissions-transact-sql.md)   
 [GRANT (データベースの権限の許可) &#40;Transact-SQL&#41;](../../t-sql/statements/grant-database-permissions-transact-sql.md)   
 [システム ビュー &#40;TRANSACT-SQL&#41;](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)  
  
  
