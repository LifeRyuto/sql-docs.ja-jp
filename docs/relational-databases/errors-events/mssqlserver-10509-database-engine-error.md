---
title: MSSQLSERVER_10509 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10509 (Database Engine error)
ms.assetid: e9dd5357-ee3d-420a-9a89-d12ab5404e73
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 419b45c688f755d6e5f7cf86154ce6cc527fc6ea
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63048246"
---
# <a name="mssqlserver10509"></a>MSSQLSERVER_10509
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|10509|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|PG_INVALID_STMT|  
|メッセージ テキスト|プラン ガイド '%.\*ls' を作成できません。 **@stmt** または **@statement_start_offset** で指定したステートメントが構文エラーを含んでいるか、またはプラン ガイドでの使用に適していません。 有効な [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを 1 つだけ指定するか、またはバッチ内のステートメントの有効な開始位置を指定します。 有効な開始位置を取得するには、動的管理関数 sys.dm_exec_query_stats の statement_start_offset 列のクエリを実行します。|  
  
## <a name="explanation"></a>説明  
**@stmt** または **@statement_start_offset** で指定したステートメントが構文エラーを含んでいるか、またはプラン ガイドでの使用に適していません。  
  
## <a name="user-action"></a>ユーザーの操作  
有効な [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを 1 つだけ指定するか、またはバッチ内のステートメントの有効な開始位置を指定します。 有効な開始位置を取得するには、動的管理関数 sys.dm_exec_query_stats の statement_start_offset 列のクエリを実行します。  
  
## <a name="see-also"></a>参照  
[sp_create_plan_guide &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[プラン ガイド](~/relational-databases/performance/plan-guides.md)  
[sys.dm_exec_query_stats &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)  
[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
