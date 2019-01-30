---
title: sql:column() 関数 (XQuery) |Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- sql:column function
- sql:column() function
ms.assetid: e8f67bdf-b489-49a9-9d0f-2069c1750467
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: c5b7babb3f34f906a241669bbde753e3beaace92
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2018
ms.locfileid: "51662271"
---
# <a name="xquery-extension-functions---sqlcolumn"></a>XQuery Extension Functions - sql:column()
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  」の説明に従って[XML 内リレーショナル データのバインド](../t-sql/xml/binding-relational-data-inside-xml-data.md)、使用することができます、 **sql:column()** 関数を使用するときに[XML データ型メソッド](../t-sql/xml/xml-data-type-methods.md)リレーショナル値を公開するにはXQuery 内部。  
  
 たとえば、 [query() メソッド (XML データ型)](../t-sql/xml/query-method-xml-data-type.md)変数またはの列に格納されている XML インスタンスに対してクエリを指定するために使用**xml**型。 場合によっては、クエリで XML 型ではない別の列の値を使用して、リレーショナル データと XML データを結合することもできます。 これを行うには、使用する、 **sql:column()** 関数。  
  
 SQL 値は、対応する XQuery 値にマップされ、その型は対応する SQL 型に相当する XQuery 基本データ型になります。  
  
## <a name="syntax"></a>構文  
  
```  
  
sql:column("columnName")  
```  
  
## <a name="remarks"></a>コメント  
 指定された列への参照をことに注意してください、 **sql:column()** XQuery 内の関数が処理されている行の列を参照します。  
  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]、のみを参照することができます、 **xml**インスタンス コンテキスト、ソースの式の XML DML 挿入ステートメントで、それ以外の場合、型の列を参照することはできません**xml**または CLRユーザー定義型です。  
  
 **Sql:column()** 結合操作では、関数はサポートされていません。 代わりに、APPLY 操作を使用できます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-sqlcolumn-to-retrieve-the-relational-value-inside-xml"></a>A. sql:column() を使用して XML 内部のリレーショナル値を取得する  
 XML の構築にあたり、次の例では、XML 以外のリレーショナル列の値を取得し、XML とリレーショナル データをバインドしています。  
  
 クエリにより、次の形式で XML が構築されます。  
  
```xml
<Product ProductID="771" ProductName="Mountain-100 Silver, 38" ProductPrice="3399.99" ProductModelID="19"   
  ProductModelName="Mountain 100" />  
```  
  
 構築された XML に関して、次の点に注意してください。  
  
-   **ProductID**、 **ProductName**、および**ProductPrice**属性値がから取得した、**製品**テーブル。  
  
-   **ProductModelID**から属性値を取得、 **ProductModel**テーブル。  
  
-   さらに興味深いクエリを作成する、 **ProductModelName**属性値がから取得した、 **CatalogDescription**の列**xml 型**します。 XML 製品モデル カタログ情報が保存されていない製品モデルもあるため、`if` ステートメントを使用して、カタログ情報がある場合にのみその値を取得するようにしています。  
  
    ```sql
    SELECT P.ProductID, CatalogDescription.query('  
    declare namespace pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
           <Product   
               ProductID=       "{ sql:column("P.ProductID") }"  
               ProductName=     "{ sql:column("P.Name") }"  
               ProductPrice=    "{ sql:column("P.ListPrice") }"  
               ProductModelID= "{ sql:column("PM.ProductModelID") }" >  
               { if (not(empty(/pd:ProductDescription))) then  
                 attribute ProductModelName { /pd:ProductDescription[1]/@ProductModelName }  
                else   
                   ()  
    }  
            </Product>  
    ') as Result  
    FROM Production.ProductModel PM, Production.Product P  
    WHERE PM.ProductModelID = P.ProductModelID  
    AND   CatalogDescription is not NULL  
    ORDER By PM.ProductModelID  
    ```  
  
 上のクエリに関して、次の点に注意してください。  
  
-   値を 2 つの異なるテーブルから取得するため、FROM 句で 2 つのテーブルを指定しています。 WHERE 句に定義された条件により結果をフィルター選択し、カタログの説明のある製品モデルの製品のみを取得しています。  
  
-   **名前空間**キーワード、 [XQuery プロローグ](../xquery/modules-and-prologs-xquery-prolog.md)XML 名前空間プレフィックス"pd"、クエリ本文で使用されるを定義します。 テーブルの別名 "P" および "PM" は、クエリ自体の FROM 句に定義されていることに注意してください。  
  
-   **Sql:column()** 関数を使用して、XML 内部の XML 以外の値を表示します。  
  
 結果の一部を次に示します。  
  
```  
ProductID               Result  
-----------------------------------------------------------------  
771         <Product ProductID="771"                   ProductName="Mountain-100 Silver, 38"   
                  ProductPrice="3399.99" ProductModelID="19"   
                  ProductModelName="Mountain 100" />  
...  
```  
  
 次のクエリは、製品固有の情報を保持する XML を構築します。 この情報には、ある特定の製品モデル (ProductModelID=19) に属するすべての製品について、ProductID、ProductName、ProductPrice、および取得可能な場合は ProductModelName が含まれます。 XML が割り当てられているし、@xの変数 **xml** 型。  
  
```sql
declare @x xml  
SELECT @x = CatalogDescription.query('  
declare namespace pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
       <Product   
           ProductID=       "{ sql:column("P.ProductID") }"  
           ProductName=     "{ sql:column("P.Name") }"  
           ProductPrice=    "{ sql:column("P.ListPrice") }"  
           ProductModelID= "{ sql:column("PM.ProductModelID") }" >  
           { if (not(empty(/pd:ProductDescription))) then  
             attribute ProductModelName { /pd:ProductDescription[1]/@ProductModelName }  
            else   
               ()  
}  
        </Product>  
')   
FROM Production.ProductModel PM, Production.Product P  
WHERE PM.ProductModelID = P.ProductModelID  
And P.ProductModelID = 19  
select @x  
```  
  
## <a name="see-also"></a>参照  
 [SQL Server XQuery 拡張関数します。](https://msdn.microsoft.com/library/4bc5d499-5fec-4c3f-b11e-5ab5ef9d8f97)   
 [型指定された XML と型指定されていない XML の比較](../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [XML データ &#40;SQL Server&#41;](../relational-databases/xml/xml-data-sql-server.md)   
 [XML データのインスタンスの作成](../relational-databases/xml/create-instances-of-xml-data.md)   
 [xml データ型メソッド](../t-sql/xml/xml-data-type-methods.md)   
 [XML データ変更言語 &#40;XML DML&#41;](../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  
