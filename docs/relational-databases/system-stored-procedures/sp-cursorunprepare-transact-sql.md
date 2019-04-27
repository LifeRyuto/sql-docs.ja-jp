---
title: sp_cursorunprepare (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cursorunprepare_TSQL
- sp_cursorunprepare
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cursorunprepare
ms.assetid: b46d4813-c4a9-4f9d-9979-2b5082ecf06a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4427cb2db0169f5cb7a25937e230777318ab9201
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62507239"
---
# <a name="spcursorunprepare-transact-sql"></a>sp_cursorunprepare (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ストアド プロシージャを sp_cursorprepare で作成された実行プランを破棄します。 sp_cursorunprepare は、ID を指定して呼び出される、表形式データ ストリーム (TDS) パケットで 6 を = です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_cursorunprepare handle  
```  
  
## <a name="arguments"></a>引数  
 *handle*  
 *処理*ステートメントが準備されたときに sp_cursorprepare から返される値。  
  
## <a name="see-also"></a>参照  
 [sp_cursorprepare &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursorprepare-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
