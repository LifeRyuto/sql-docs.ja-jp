---
title: MSSQLSERVER_10537 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10537 (Database Engine error)
ms.assetid: 728469a4-6523-4a37-925f-a950d75420fa
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4a3dfb73f5ca3b073cf0d5ded864669f977c6aee
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63048583"
---
# <a name="mssqlserver10537"></a>MSSQLSERVER_10537
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|10537|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|PG_DUP_ENABLED|  
|メッセージ テキスト|プラン ガイド '%.*ls' を作成できません。有効なプラン ガイド '%.\*ls' に、ステートメントと同じスコープと開始オフセット値が含まれています。 指定したプラン ガイドを有効にする前に、既存のプラン ガイドを無効にします。|  
  
## <a name="explanation"></a>説明  
既存のプラン ガイドに、指定したプラン ガイドのステートメントと同じスコープと開始オフセット値が含まれています。  
  
## <a name="user-action"></a>ユーザーの操作  
指定したプラン ガイドを有効にする前に、既存のプラン ガイドを無効にします。  
  
## <a name="see-also"></a>参照  
[sp_create_plan_guide &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[プラン ガイド](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
