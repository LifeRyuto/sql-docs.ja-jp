---
title: dm_xe_session_targets (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_xe_session_targets
- dm_xe_session_targets_TSQL
- dm_xe_session_targets
- sys.dm_xe_session_targets_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_xe_session_targets dynamic management view
- extended events [SQL Server], views
ms.assetid: 76fbc3e1-ad88-4a47-8bf1-471c3bee5ad8
author: stevestein
ms.author: sstein
ms.openlocfilehash: 977a5e0428f59a45a823dd82e30b3f4c63520c0c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68090209"
---
# <a name="sysdm_xe_session_targets-transact-sql"></a>sys.dm_xe_session_targets (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  セッション ターゲットに関する情報を返します。  
  
  |列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|event_session_address|**varbinary (8)**|イベントセッションのメモリアドレス。 sys.dm_xe_sessions.address との多対一のリレーションシップがあります。 NULL 値は許可されません。|  
|target_name|**nvarchar (60)**|セッション内のターゲットの名前。 NULL 値は許可されません。|  
|target_package_guid|**UNIQUEIDENTIFIER**|ターゲットを含むパッケージの GUID。 NULL 値は許可されません。|  
|execution_count|**bigint**|セッションに対してターゲットが実行された回数。 NULL 値は許可されません。|  
|execution_duration_ms|**bigint**|ターゲットが実行された時間の合計 (ミリ秒単位)。 NULL 値は許可されません。|  
|target_data|**nvarchar(max)**|イベント集計情報など、ターゲットが保持するデータ。 NULL 値が許可されます。|  
  
## <a name="permissions"></a>アクセス許可  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
### <a name="relationship-cardinalities"></a>リレーションシップ基数  
  
|移行元|To|リレーションシップ|  
|----------|--------|------------------|  
|sys.dm_xe_session_targets.event_session_address|sys.dm_xe_sessions.address|多対一|  
  
## <a name="change-history"></a>変更履歴  
  
|変更内容|  
|---------------------|  
|target_data 列のデータ型を修正しました。|  
|Target_data 列の説明を、null 値が許容される値であることを示すように修正しました。|  
|"Relationship 基数" テーブルを修正しました。|  
  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
  
  

