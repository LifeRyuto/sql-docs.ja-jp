---
title: SQLXML インターフェイス |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 7c67be98-efb5-446c-a0e3-ee67c43cb170
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 29d135cffceca65ea81ac6752963732bc2f7b056
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66798332"
---
# <a name="sqlxml-interface"></a>SQLXML インターフェイス

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

この JDBC ドライバーがサポートする JDBC 4.0 API には、java.sql.SQLXML インターフェイスが導入されています。 SQLXML インターフェイスには、XML データを操作するための各種のメソッドが定義されています。 **SQLXML**データ型にマップされます、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **xml**データ型。  
  
SQLXML インターフェイスとして XML 値にアクセスするためのメソッドを提供、**文字列**、**リーダー**または**ライター**、または、 **Stream**します。 XML 値は **Source** を介してアクセスしたり、**Result** として設定したりすることもでき、これらを XSLT 変換や XPath のほか、Document Object Model (DOM)、Simple API for XML (SAX)、Streaming API for XML (StAX) などの XML パーサー API と組み合わせて利用することが可能です。  
  
## <a name="remarks"></a>Remarks  

次の表で、SQLXML インターフェイスに定義されている各メソッドについて説明します。  
  
|メソッドの構文|メソッドの説明|  
|-------------------|------------------------|  
|[void free()](https://go.microsoft.com/fwlink/?LinkId=131685)|このメソッドは、SQLXML オブジェクトと、それが占有していたリソースを解放します。|  
|[InputStream getBinaryStream()](https://go.microsoft.com/fwlink/?LinkId=131754)|SQLXML からデータを読み取る入力ストリームを返します。|  
|[Reader getCharacterStream()](https://go.microsoft.com/fwlink/?LinkId=131755)|**XML** データを、java.io.Reader オブジェクトまたは文字のストリームとして返します。|  
|[T extends Source T getSource(Class\<T> sourceClass)](https://go.microsoft.com/fwlink/?LinkId=131756)|返します、**ソース**読み取り用、 **XML**これによって指定された値**SQLXML**オブジェクト。<br /><br /> **注:** getSource メソッドは、javax.xml.transform.dom.DOMSource、javax.xml.transform.sax.SAXSource、javax.xml.transform.stax.StAXSource、java.io.InputStream の各ソースをサポートします。|  
|[String getString()](https://go.microsoft.com/fwlink/?LinkId=131757)|この SQLXML オブジェクトによって指定された **XML** 値の文字列表現を返します。|  
|[OutputStream setBinaryStream()](https://go.microsoft.com/fwlink/?LinkId=131758)|この SQLXML オブジェクトが表す **XML** 値の書き込みに使用できるストリームを取得します。|  
|[Writer setCharacterStream()](https://go.microsoft.com/fwlink/?LinkId=131759)|この SQLXML オブジェクトが表す **XML** 値の書き込みに使用されるストリームを返します。|  
|[T extends Result T setResult(Class\<T> resultClass)](https://go.microsoft.com/fwlink/?LinkId=131760)|返します、**結果**設定、 **XML**これによって指定された値**SQLXML**オブジェクト。<br /><br /> **注:** setResult メソッドは、javax.xml.transform.dom.DOMResult、javax.xml.transform.sax.SAXResult、javax.xml.transform.stax.StaxResult、java.io.OutputStream の各ソースをサポートします。|  
|[void setString(String value)](https://go.microsoft.com/fwlink/?LinkId=131762)|この SQLXML オブジェクトによって指定された XML 値を、指定された **String** 表現に設定します。|  
  
アプリケーションから SQLXML オブジェクトを介して XML 値の読み取りと書き込みを行うことができるのは 1 回だけです。  
  
SQLXML オブジェクトは free() メソッドが呼び出された時点で無効になり、読み取りも書き込みもできなくなります。 同じ SQLXML オブジェクトの (free() 以外の) メソッドを呼び出そうとすると、例外がスローされます。  
  
アプリケーションは、次の getter メソッドのいずれかを呼び出すときに、SQLXML オブジェクトは読み取りも書き込みも: getSource、getCharacterStream、getBinaryStream と getString します。  
  
アプリケーションでは、次の setter メソッドのいずれかを呼び出すとき、SQLXML オブジェクトはどちらも書き込みも読み取り: setResult、setCharacterStream、setBinaryStream、setString とします。  
  
## <a name="see-also"></a>参照  

[XML データのサポート](../../connect/jdbc/supporting-xml-data.md)  
