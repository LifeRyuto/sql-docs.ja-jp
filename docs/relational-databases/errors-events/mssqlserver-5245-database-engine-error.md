---
title: MSSQLSERVER_5245 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 5245 (Database Engine error)
ms.assetid: 6005c9ec-ccdd-4def-9eb4-37cdb599ddb3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c1d0c05f5439bbeea03895a4c0611b1aca6f35ed
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2020
ms.locfileid: "68062622"
---
# <a name="mssqlserver_5245"></a>MSSQLSERVER_5245
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|5245|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|DBCC4_TABLE_LOCK_TIMEOUT_EXCEEDED|  
|メッセージ テキスト|オブジェクト ID O_ID (オブジェクト 'NAME'): DBCC ではこのオブジェクトをロックできませんでした。ロック要求がタイムアウトしました。 このオブジェクトはスキップされたので、処理されません。|  
  
## <a name="explanation"></a>説明  
DBCC が、指定されたオブジェクト用にテーブルのロック獲得を待機している間に、ロック要求のタイムアウトが発生しました。  
  
## <a name="user-action"></a>ユーザーの操作  
DBCC コマンドを再実行します。  
  
