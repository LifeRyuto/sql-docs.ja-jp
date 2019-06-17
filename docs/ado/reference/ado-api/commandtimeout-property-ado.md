---
title: CommandTimeout プロパティ (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command15::CommandTimeout
helpviewer_keywords:
- CommandTimeout property [ADO]
ms.assetid: c611f857-d6b0-4dca-8925-f4a02e769eb0
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 556474c3b038f40e21467a4bbc945fc8f29fd5a8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66695989"
---
# <a name="commandtimeout-property-ado"></a>CommandTimeout プロパティ (ADO)
試行を終了し、エラーが発生する前に、コマンドの実行中に待機する時間を示します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 設定または取得を**長い**を示す値を秒単位で期間コマンドの実行を待機します。 既定値は 30 です。  
  
## <a name="remarks"></a>コメント  
 使用して、 **CommandTimeout**プロパティを[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクトまたは[コマンド](../../../ado/reference/ado-api/command-object-ado.md)の取り消しを許可するオブジェクト、 [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md)メソッドネットワーク トラフィックや負荷の高いサーバーの使用から遅延によって、呼び出しをします。 この間隔で設定する場合、 **CommandTimeout**プロパティでは、コマンドが実行を完了、エラーが発生し、ADO コマンドをキャンセルする前に経過するとします。 プロパティを 0 に設定すると、ADO は、実行が完了するまで無期限に待機します。 コードのサポートを記述する、プロバイダーとデータ ソースの確認、 **CommandTimeout**機能します。  
  
 **CommandTimeout**の設定、**接続**オブジェクトも何も起こりません、 **CommandTimeout**の設定、**コマンド**上のオブジェクト、同じ**接続**つまり、**コマンド**オブジェクトの**CommandTimeout**プロパティの値を継承しません、 **の接続。** オブジェクトの**CommandTimeout**値。  
  
 **接続**オブジェクト、 **CommandTimeout**プロパティは読み取り/書き込み後に、**接続**が開かれます。  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[Command オブジェクト (ADO)](../../../ado/reference/ado-api/command-object-ado.md)|[Connection オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|  
  
## <a name="see-also"></a>参照  
 [ActiveConnection、CommandText、CommandTimeout、CommandType、サイズ、および方向プロパティの例 (VB)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [ActiveConnection、CommandText、CommandTimeout、CommandType、サイズ、および方向プロパティの例 (vc++)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [ActiveConnection、CommandText、CommandTimeout、CommandType、サイズ、および方向プロパティの例 (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)   
 [ConnectionTimeout プロパティ (ADO)](../../../ado/reference/ado-api/connectiontimeout-property-ado.md)
