---
title: 名前空間を使用した XPath クエリの実行 (SQLXML マネージクラス) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- namespaces property
- XPath queries [SQLXML], SQLXML Managed Classes
- queries [SQLXML], SQLXML Managed Classes
- XPath queries [SQLXML], namespaces
- Managed Classes [SQLXML], executing XPath queries
- SQLXML Managed Classes, executing XPath queries
- namespaces [SQLXML], XPath queries
ms.assetid: c6fc46d8-6b42-4992-a8f1-a8d4b8886e6e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 793107e91425e4fa0df23211a6d4ea42afef8c54
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66010803"
---
# <a name="executing-xpath-queries-with-namespaces-sqlxml-managed-classes"></a>名前空間を使用した XPath クエリの実行 (SQLXML マネージド クラス)
  XPath クエリには名前空間を使用できます。 スキーマ要素に対象名前空間の修飾子が付けられている場合、そのスキーマに対する XPath クエリでは、名前空間を指定する必要があります。  
  
 
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 ではワイルドカード文字 (*) がサポートされないため、XPath クエリは、名前空間プレフィックスを使用して指定する必要があります。 プレフィックスを解決するには、名前空間プロパティを使用して名前空間のバインドを指定します。  
  
 次の例では、XPath クエリは、ワイルドカード文字 (\*) およびローカル名 () および名前空間 uri () の xpath 関数を使用して名前空間を指定します。 この XPath クエリでは、ローカル名が `Employee`、名前空間 URI が `urn:myschema:Contacts` のすべての要素が返されます。  
  
```  
/*[local-name() = 'Contact' and namespace-uri() = 'urn:myschema:Contacts']  
```  
  
 SQLXML 4.0 では、この XPath クエリを名前空間プレフィックスと共に指定します。 たとえば、`x:Contact` と指定します。ここで、`x` は名前空間プレフィックスです。 次の XSD スキーマについて考えてみます。  
  
```  
<schema xmlns="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema"  
            xmlns:con="urn:myschema:Contacts"  
            targetNamespace="urn:myschema:Contacts">  
<complexType name="ContactType">  
  <attribute name="CID" sql:field="ContactID" type="ID"/>  
  <attribute name="FName" sql:field="FirstName" type="string"/>  
  <attribute name="LName" sql:field="LastName"/>   
</complexType>  
<element name="Contact" type="con:ContactType" sql:relation="Person.Contact"/>  
</schema>  
```  
  
 このスキーマでは対象の名前空間が定義されているため、このスキーマに対する XPath クエリ ("Employee" など) には名前空間を含める必要があります。  
  
 次の C# サンプル アプリケーションでは、前の XSD スキーマ (MySchema.xml) に対する XPath クエリが実行されます。 プレフィックスを解決するには、SqlXmlCommand オブジェクトの namespace プロパティを使用して名前空間のバインドを指定します。  
  
> [!NOTE]  
>  コードでは、接続文字列に [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンス名を含める必要があります。  
  
```  
using System;  
using Microsoft.Data.SqlXml;  
using System.IO;  
class Test  
{  
      static string ConnString = "Provider=SQLOLEDB;Server=(local);database=AdventureWorks;Integrated Security=SSPI";  
      public static int testXPath()  
      {  
         //Stream strm;  
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
         cmd.CommandText = "x:Contact[@CID='1']";  
         cmd.CommandType = SqlXmlCommandType.XPath;  
         cmd.RootTag = "ROOT";  
         cmd.Namespaces = "xmlns:x='urn:myschema:Contacts'";  
         cmd.SchemaPath = "MySchema.xml";  
         using (Stream strm = cmd.ExecuteStream()){  
            using (StreamReader sr = new StreamReader(strm)){  
               Console.WriteLine(sr.ReadToEnd());  
            }  
         }  
         return 0;  
      }  
      public static int Main(String[] args)  
      {  
         testXPath();  
         return 0;  
      }  
   }  
```  
  
 この例をテストするには、コンピューターに [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework がインストールされている必要があります。  
  
### <a name="to-test-the-application"></a>アプリケーションをテストするには  
  
1.  この例で提供される XSD スキーマ (MySchema.xml) をフォルダーに保存します。  
  
2.  この例で提供されている C# コード (DocSample.cs) を、スキーマが格納されているのと同じフォルダーに保存します。 ファイルを別のフォルダーに保存する場合は、コードを編集して、マッピング スキーマに対する適切なディレクトリ パスを指定する必要があります。  
  
3.  コードをコンパイルします。 コマンド プロンプトでコードをコンパイルするには、次を使用します。  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     これにより、実行可能ファイル (DocSample.exe) が作成されます。  
  
4.  コマンド プロンプトで、DocSample.exe を実行します。  
  
  
