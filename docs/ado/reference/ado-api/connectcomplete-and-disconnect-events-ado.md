---
title: ConnectComplete イベントと Disconnect イベント (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Disconnect
- Connection::ConnectComplete
- ConnectComplete
- Connection::Disconnect
helpviewer_keywords:
- Disconnect event [ADO]
- ConnectComplete event [ADO]
ms.assetid: 568f5252-d069-4d99-a01b-2ada87ad1304
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 448270ddf0e8cd7efb5ec39a93d4ff993360730e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67919579"
---
# <a name="connectcomplete-and-disconnect-events-ado"></a>ConnectComplete および Disconnect イベント (ADO)
**Connectcomplete**イベントは、接続の開始後に呼び出されます。 **切断**イベントは、接続が終了した後に呼び出されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
ConnectComplete pError, adStatus, pConnection  
Disconnect adStatus, pConnection  
```  
  
#### <a name="parameters"></a>パラメーター  
 *pError*  
 [エラー](../../../ado/reference/ado-api/error-object.md)オブジェクトです。 *Adstatus*の値が**adstatuserrorて**いる場合に発生したエラーについて説明します。それ以外の場合は設定されません。  
  
 *adStatus*  
 常に**Adstatusok**を返す[eventstatusenum](../../../ado/reference/ado-api/eventstatusenum.md)値。  
  
 **Connectcomplete**が呼び出されると、このパラメーターは、が保留中の接続のキャンセルを**要求した**場合に**adstatuscancel**に設定されます。  
  
 いずれかのイベントが返される前に、このパラメーターを**adStatusUnwantedEvent**に設定して、後続の通知を防止します。 ただし、[接続](../../../ado/reference/ado-api/connection-object-ado.md)を閉じて再度開くと、これらのイベントが再び発生します。  
  
 *pConnection*  
 このイベントが適用される**接続**オブジェクト。  
  
## <a name="see-also"></a>参照  
 [ADO Events モデルの例 (VC + +)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [ADO イベント ハンドラーの概要](../../../ado/guide/data/ado-event-handler-summary.md)
