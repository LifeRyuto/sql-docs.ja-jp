---
title: 変更データ キャプチャを有効にする場合は、cdc スキーマを削除する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- cdc schema
- change data capture
ms.assetid: 6a84aa25-0f31-4be3-b2dd-4f249b8254ae
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a5d162635a9162871e51fe0664198302804aa487
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62855751"
---
# <a name="remove-the-cdc-schema-if-you-plan-to-enable-change-data-capture"></a>変更データ キャプチャを有効にする場合に cdc スキーマを削除する
  データベースには、既に cdc スキーマが含まれています。 アップグレード後に変更データ キャプチャを有効にする場合は、まずこの cdc スキーマを削除する必要があります。 データベースで変更データ キャプチャを有効にすると、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]によって、cdc という名前の新しいスキーマが作成されます。  
  
  
