---
title: システム テーブル (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- status information [SQL Server]
- tables [SQL Server], system tables
- information retrieval [SQL Server]
- status information [SQL Server], system tables
- system information [SQL Server]
- system tables [SQL Server]
- system tables [SQL Server], about system tables
- system tables [SQL Server], retrieving information from
- retrieving system table information
ms.assetid: 56b8ad51-930c-4e5c-8d99-8c939d5b70ac
author: stevestein
ms.author: sstein
ms.openlocfilehash: 98f9a51b2248a1d218e9cbed576dc41bf64c91b5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68029620"
---
# <a name="system-tables-transact-sql"></a>システム テーブル (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  このセクションでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内のシステム テーブルについて説明します。  
  
 システム テーブルは、すべてのユーザーが直接変更しないでください。 たとえば、システム テーブルを DELETE、UPDATE、INSERT ステートメント、またはユーザー定義のトリガーで変更しないでください。  
  
 システム テーブル内の列で、このドキュメントに記載されている列の参照は許可されています。 ただし、システム テーブルの列の多くは記載されていません。 アプリケーションは必要があります記載されていない列を直接クエリには書き込まれません。 代わりに、システム テーブル内に保存されている情報を取得するには、アプリケーションでは次のコンポーネントのいずれかを使用します。  
  
-   システム ストアド プロシージャ  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントおよび関数  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理オブジェクト (SMO)  
  
-   レプリケーション管理オブジェクト (RMO)  
  
-   データベース API カタログ関数  
  
 システム情報を取得するため、これらのコンポーネントが公開された API を構成する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] リリースごとにこれらのコンポーネントとの互換性を維持します。 システム テーブルの形式は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の内部アーキテクチャに依存し、リリースごとに変化する可能性があります。 このため、ドキュメントに記載されていないシステム テーブルの列に直接アクセスするアプリケーションを作成すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の最新バージョンにアクセスするために変更を余儀なくされることがあります。  
  
## <a name="in-this-section"></a>このセクションの内容  
 次の機能領域では、システム テーブルのトピックが構成されています。  
  
|||  
|-|-|  
|[バックアップし、復元テーブル&#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)|[ログ配布テーブル &#40;Transact-SQL&#41;](../../relational-databases/system-tables/log-shipping-tables-transact-sql.md)|  
|[変更データ キャプチャ テーブル&#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/change-data-capture-tables-transact-sql.md)|[レプリケーション テーブル &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)|  
|[データベース メンテナンス プラン テーブル&#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/database-maintenance-plan-tables-transact-sql.md)|[SQL Server エージェント テーブル&#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/sql-server-agent-tables-transact-sql.md)|  
|[SQL Server 拡張イベント テーブル&#40;TRANSACT-SQL&#41;](https://msdn.microsoft.com/library/6d52ff03-f5aa-4f0f-8c98-9b49dc76f94e)|[sys.sysoledbusers &#40;TRANSACT-SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysoledbusers-transact-sql.md)|  
|[Integration Services テーブル&#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/integration-services-tables-transact-sql.md)|[systranschemas &#40;TRANSACT-SQL&#41;](../../relational-databases/system-views/systranschemas-transact-sql.md)|  
  
## <a name="see-also"></a>関連項目  
 [互換性ビュー &#40;TRANSACT-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
