---
title: setAsciiStream メソッドの入力には、バイト数 - を時間の長いストリーム) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 6bc486cd-e432-4057-8789-9957ba23dd30
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 470ce0c14253229e096aec36ac9d0c019f27353c
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66765148"
---
# <a name="setasciistream-method-javalangstring-javaioinputstream-long"></a>setAsciiStream (java.lang.String, java.io.InputStream, long) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定されたパラメーターを、指定された入力ストリームに設定します。入力ストリームは、指定されたバイト数を持ちます。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final void setAsciiStream(java.lang.String parameterName,  
                                java.io.InputStream x,  
                                long length)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *parameterName*  
  
 パラメーターの名前を含む**文字列**です。  
  
 *x*  
  
 InputStream オブジェクト。  
  
 *length*  
  
 バイト数を示す **long** です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この setAsciiStream メソッドは、java.sql.PreparedStatement インターフェイスの setAsciiStream メソッドによって指定されます。  
  
 ストリームの長さが、*length* パラメーターで指定された長さと異なる場合は、行の更新または挿入時に JDBC ドライバーが例外をスローします。  
  
 ストリームの長さが不明である場合、*length* パラメーターを -1 に設定して、ドライバーが長さに関係なくストリームを受け入れるように指定できます。 sqljdbc4.jar を使用する場合、アプリケーションで長さが不明なストリームを使用して列を更新するときは、JDBC 4.0 メソッドの [setAsciiStream (java.lang.String, java.io.InputStream) メソッド](../../../connect/jdbc/reference/setasciistream-method-java-lang-string-java-io-inputstream.md)を使用することをお勧めします。  
  
## <a name="see-also"></a>参照  
 [setAsciiStream &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/setasciistream-sqlservercallablestatement.md)   
 [SQLServerCallableStatement のメンバー](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
