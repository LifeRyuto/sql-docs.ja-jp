---
title: MSSQLSERVER_7711 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 7711 (Database Engine error)
ms.assetid: a5c7cd6e-18d6-47ef-902b-db9dd64bba34
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1c1d9c5e02b4b761bba80f69306db51460b6ea43
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63025379"
---
# <a name="mssqlserver7711"></a>MSSQLSERVER_7711
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|7711|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|PRT_RANGE_OVERLAP|  
|メッセージ テキスト|テーブル、インデックス、またはパーティションの 1 つに DATA_COMPRESSION オプションが複数回指定されました。|  
  
## <a name="explanation"></a>説明  
次のステートメントのいずれかの DATA_COMPRESSION オプションでエラーが発生しました。  
  
-   CREATE TABLE  
  
-   ALTER TABLE  
  
-   CREATE INDEX  
  
-   ALTER INDEX  
  
引用されたテーブルまたはインデックスがパーティション分割されている場合、少なくとも 1 つのパーティションで DATA_COMPRESSION オプションが 2 回以上指定されました。 テーブルまたはインデックスがパーティション分割されていない場合、DATA_COMPRESSION オプションが 2 回以上引用されました。  
  
## <a name="user-action"></a>ユーザーの操作  
パーティション分割されたテーブルまたはインデックスの場合、各パーティションに DATA_COMPRESSION オプションを 1 回だけ指定するようにしてください。 パーティション分割されていないテーブルまたはインデックスの場合、ステートメントに DATA_COMPRESSION オプションを 1 回だけ使用してください。  
  
