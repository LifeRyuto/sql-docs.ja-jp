---
title: 複数のhstmts(パラドックスドライバ) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- multiple hstmts [ODBC]
- Paradox driver [ODBC], multiple hstmts
ms.assetid: 66aecd94-092d-43d4-9583-74f5e2990eac
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ac381024a6b4b67719cb7c098367f63a6176bad0
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298192"
---
# <a name="multiple-hstmts-paradox-driver"></a>複数 hstmts (Paradox ドライバー)
ODBC Paradox ドライバを使用する場合、テーブルに対してクエリを実行するために複数*の hstmt*を使用する場合、テーブルには一意のインデックス (Paradox 主キー) が必要です。
