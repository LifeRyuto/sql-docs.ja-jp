---
title: setPacketSize メソッド (SQLServerDataSource) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setPacketSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5d490edc-a223-4870-a838-784952497e5f
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: d102885fc235a66f5d42b7ae5100bc8905d895d2
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66788117"
---
# <a name="setpacketsize-method-sqlserverdatasource"></a>setPacketSize メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] との通信に使用される現在のネットワーク パケット サイズが設定されます (バイトで指定します)。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void setPacketSize(int packetSize)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *packetSize*  
  
 ネットワーク パケット サイズを含む **int** 値です。  
  
## <a name="remarks"></a>Remarks  
 このプロパティの値の許容範囲は、[-1 | 0 | 512..32767] です。 このプロパティが許容範囲外の値に設定されている場合は、例外が発生します。  
  
 SSL (Secure Sockets Layer) 暗号化を使用して接続しているときに、アプリケーションで packetSize プロパティを設定する場合があります。 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] では、パケット サイズがサーバーとの間でネゴシエートされます。 encrypt プロパティが "**true**" に設定されている場合に、ネゴシエートされたパケット サイズが Java 仮想マシン (JVM) における既定のセキュリティ プロバイダーの SSL レコード サイズを超えるときは、ドライバーでエラーが発生して接続が終了します。  
  
 また、SSL 暗号化を要求せずにアプリケーションで packetSize プロパティを設定する場合もあります。 この場合、クライアントによる SSL 暗号化のサポートをサーバーで必要としているときは、JVM における既定のセキュリティ プロバイダーの SSL レコード サイズが、ドライバーによってチェックされます。 packetSize プロパティが JVM における既定のセキュリティ プロバイダーの SSL レコード サイズを超えるときは、ドライバーでエラーが発生して接続が終了します。  
  
 SSL の使用方法の詳細については、次を参照してください。 [Using SSL Encryption](../../../connect/jdbc/using-ssl-encryption.md)します。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
