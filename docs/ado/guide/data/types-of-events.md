---
title: イベントの種類 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- EventComplete event [ADO]
- events [ADO], types
- Will events [ADO]
- complete events [ADO]
- WillEvent event [ADO]
ms.assetid: f3327ea0-635a-43d4-bd78-c1674f62f1a2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 78505f010706a39e5278d50219dd4504e33dd67c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63142941"
---
# <a name="types-of-events"></a>イベントの種類
2 つのイベントの種類があります。 「イベントは」操作を開始する前に呼び出されなどの名前に「は」は、通常**WillChangeRecordset**または**WillConnect**します。 イベントが通常は完了した後に呼び出されるイベントを含める"Complete"の名前になど**RecordChangeComplete**または**ConnectComplete**します。 例外の存在 - など**InfoMessage** - が関連付けられている操作が完了した後にこれらが発生します。  
  
## <a name="will-events"></a>イベントには  
 操作の開始が調査または操作のパラメーターを変更し、操作をキャンセルするかを完了することを許可する機会を提供する前に、イベント ハンドラーが呼び出されます。 これらのイベント ハンドラー ルーチンが、通常は、フォームの名前を持つ<strong>は*イベント*</strong>します。  
  
## <a name="complete-events"></a>完了イベント  
 操作の完了後に呼び出されるイベント ハンドラーは、操作の完了をアプリケーションに通知できます。 イベント ハンドラーが保留中の操作をキャンセルしたときにも、このようなイベント ハンドラーが通知されます。 これらのイベント ハンドラー ルーチンが、通常は、フォームの名前を持つ<strong>*イベント*完了</strong>します。  
  
 完了イベントがペアで通常使用されます。  
  
## <a name="other-events"></a>その他のイベント  
 他のイベント ハンドラーの名前は、フォームのないイベントは、<strong>は*イベント*</strong>または<strong>*イベント*完了</strong>の後にのみと呼ばれます操作を完了します。 これらのイベントは**切断**、 **EndOfRecordset**、および**InfoMessage**します。  
  
## <a name="see-also"></a>参照  
 [ADO イベント ハンドラーの概要](../../../ado/guide/data/ado-event-handler-summary.md)   
 [言語で ADO イベントのインスタンス化](../../../ado/guide/data/ado-event-instantiation-by-language.md)   
 [イベント パラメーター](../../../ado/guide/data/event-parameters.md)   
 [複数のイベント ハンドラーの連携方法](../../../ado/guide/data/how-event-handlers-work-together.md)
