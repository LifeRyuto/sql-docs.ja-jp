---
title: MSSQLSERVER_21862 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 21862 (Database Engine error)
ms.assetid: a1d393dd-453b-4d45-9aa5-7d371213e32b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f336c64ffc0d044fa0f7282f3c87451483353879
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62914953"
---
# <a name="mssqlserver21862"></a>MSSQLSERVER_21862
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|MSSQLSERVER|  
|イベント ID|21862|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|SQLErrorNum21862|  
|メッセージ テキスト|FILESTREAM 列は、同期方法 'database snapshot' または 'database snapshot character' を使用して、パブリケーションでパブリッシュすることはできません。|  
  
## <a name="explanation"></a>説明  
データベース スナップショットから FILESTREAM データにアクセスできないため、パブリケーションの同期方法に *database snapshot* パラメーターまたは *database_snapshot_character* パラメーターが指定されている場合、スナップショット エージェントは FILESTREAM データを読み取ることができません。  
  
## <a name="user-action"></a>ユーザーの操作  
パブリケーションの同期方法を *database snapshot* または *database_snapshot_character* 以外の方法に変更するか、パブリケーションから FILESTREAM 列を除外します。  
  
