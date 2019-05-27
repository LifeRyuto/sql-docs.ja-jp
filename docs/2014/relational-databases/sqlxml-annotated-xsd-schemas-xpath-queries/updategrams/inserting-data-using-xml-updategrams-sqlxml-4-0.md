---
title: XML アップデート グラム (SQLXML 4.0) を使用してデータを挿入する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- xsi:nil attribute
- unique values
- <after> block
- id attribute
- data insertions [SQLXML]
- nil attribute
- <before> block
- updg:guid attribute
- multiple record insertions
- returnid attribute
- updategrams [SQLXML], inserting data
- updg:at-identity attribute
- invalid characters [SQLXML]
- updg:returnid attribute
- updg:id attribute
- namespaces [SQLXML], updategrams
- IDENTITY-type column
- guid attribute
- record insertion [SQLXML]
- null values [SQLXML]
- at-identity attribute
- xml data type [SQL Server], SQLXML
ms.assetid: 4dc48762-bc12-43fb-b356-ea1b9c1e287e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fb8058eacc2958327f1aa5649ed2dcfefe173b37
ms.sourcegitcommit: 45a9d7ffc99502c73f08cb937cbe9e89d9412397
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/22/2019
ms.locfileid: "66014807"
---
# <a name="inserting-data-using-xml-updategrams-sqlxml-40"></a>XML アップデートグラムを使用した、データの挿入 (SQLXML 4.0)
  レコード インスタンスが表示されたら、アップデート グラムは挿入操作を示します、 **\<後 >** ブロックが、対応する**\<する前に >** ブロックします。 アップデート グラムがでレコードを挿入するこの例では、 **\<後 >** をデータベースにブロックします。  
  
 挿入操作のアップデートグラムの形式は次のとおりです。  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync [mapping-schema="SampleSchema.xml"]  >  
   [<updg:before>  
   </updg:before>]  
    <updg:after [updg:returnid="x y ...] >  
       <ElementName [updg:id="value"]   
                   [updg:at-identity="x"]   
                   [updg:guid="y"]  
                   attribute="value"   
                   attribute="value"  
                   ...  
       />  
      [<ElementName .../>... ]  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
## <a name="before-block"></a>\<前に > ブロック  
 **\<する前に >** 挿入操作のブロックを省略できます。 場合、省略可能な`mapping-schema`属性が指定されていない、  **\<ElementName >** をデータベース テーブルと子要素には、アップデート グラム マップで指定されたまたはテーブル内の列に属性をマップします。  
  
## <a name="after-block"></a>\<後 > ブロック  
 内の 1 つまたは複数のレコードを指定することができます、 **\<後 >** ブロックします。  
  
 場合、 **\<後 >** ブロックが特定の列の値を提供せず、アップデート グラムでは、(スキーマが指定されている) 場合は、注釈付きスキーマで指定されている既定値を使用します。 スキーマが列の既定値を指定していない場合、アップデート グラムでこの列に明示的な値を指定しないと、代わりに、割り当て、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]既定この列に値 (指定した) 場合。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の既定値がなく、列で NULL 値が許容される場合、アップデートグラムでは列値に NULL が設定されます。 列に既定値がなく NULL 値が許容されない場合、コマンドは失敗し、アップデートグラムではエラーが返されます。 `updg:returnid` 属性は省略可能です。この属性は、IDENTITY 型の列があるテーブルにレコードを追加するときに、システムによって生成される ID 値を返す場合に使用します。  
  
## <a name="updgid-attribute"></a>updg:id 属性  
 アップデートグラムでレコードのみを挿入する場合、アップデートグラムに `updg:id` 属性を指定する必要はありません。 詳細については`updg:id`を参照してください[更新データを使用して XML アップデート グラム&#40;SQLXML 4.0&#41;](updating-data-using-xml-updategrams-sqlxml-4-0.md)します。  
  
## <a name="updgat-identity-attribute"></a>updg:at-identity 属性  
 アップデートグラムで、IDENTITY 型列があるテーブルにレコードを挿入するときには、省略可能な `updg:at-identity` 属性を使用して、システムにより割り当てられた値をキャプチャできます。 キャプチャした値は、後続のアップデートグラム操作で使用できます。 `updg:returnid` 属性を指定してアップデートグラムを実行すると、生成される ID 値を返すことができます。  
  
## <a name="updgguid-attribute"></a>updg:guid 属性  
 `updg:guid` 属性は省略可能です。この属性では、グローバル一意識別子が生成されます。 この値が全体のスコープ内に残ります**\<同期 >** ブロックが指定されています。 この値はで任意の場所を使用することができます、 **\<同期 >** ブロックします。 属性の呼び出し、 `NEWGUID()` [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]一意識別子を生成する関数。  
  
## <a name="examples"></a>使用例  
 次の例を使用して実際のサンプルを作成するで指定された要件を満たす必要があります[SQLXML の例を実行するための要件](../../sqlxml/requirements-for-running-sqlxml-examples.md)します。  
  
 アップデート グラムの例を使用する前に、次のことを確認してください。  
  
-   ほとんどの例では、アップデートグラムでマッピング スキーマを指定せず、既定のマッピングを使用します。 マッピング スキーマを使用するアップデート グラムの例については、次を参照してください。[アップデート グラムで注釈が付けられたマッピング スキーマの指定&#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)します。  
  
-   ほとんどの例では、[!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] サンプル データベースを使用します。 すべての更新内容は、このデータベースのテーブルに適用されます。  
  
### <a name="a-inserting-a-record-by-using-an-updategram"></a>A. アップデートグラムを使用してレコードを挿入する  
 この属性中心のアップデートグラムでは、[!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] データベース内の HumanResources.Employee テーブルにレコードを挿入します。  
  
 この例で、アップデート グラムでは、マッピング スキーマを指定しません。 したがって、アップデートグラムでは既定のマッピングが使用されます。このマッピングでは、要素名はテーブル名にマップされ、属性または子要素はそのテーブル内の列にマップされます。  
  
 HumanResources.Department テーブルに対する [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] スキーマでは、すべての列に 'not null' 制限が設定されます。 したがって、アップデートグラムには、すべての列に指定する値を含める必要があります。 DepartmentID は IDENTITY 型の列であり、 値は指定しません。  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
    </updg:before>  
    <updg:after>  
       <HumanResources.Department   
            Name="New Product Research"   
            GroupName="Research and Development"   
            ModifiedDate="2010-08-31"/>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>スキーマに対してサンプル XPath クエリをテストするには  
  
1.  上のアップデートグラムをコピーして、テキスト ファイルに貼り付け、 MyUpdategram.xml として保存します。  
  
2.  SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。  
  
     詳細については、次を参照してください。 [SQLXML 4.0 クエリの実行に ADO を使用する](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)します。  
  
 要素中心のマッピングの場合、アップデートグラムは次のようになります。  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
    </updg:before>  
    <updg:after>  
       <HumanResources.Department>  
            <Name> New Product Research </Name>  
            <GroupName> Research and Development </GroupName>  
            <ModifiedDate>2010-08-31</ModifiedDate>  
       </HumanResources.Department>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 要素中心と属性中心の混合モードのアップデートグラムでは、次のアップデートグラムのように、要素に属性と副要素の両方を含めることができます。  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
    </updg:before>  
    <updg:after>  
       <HumanResources.Department   
            Name=" New Product Research "   
            <GroupName>Research and Development</GroupName>  
            <ModifiedDate>2010-08-31</ModifiedDate>  
       </HumanResources.Department>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
### <a name="b-inserting-multiple-records-by-using-an-updategram"></a>B. アップデートグラムを使用して複数のレコードを挿入する  
 このアップデートグラムでは、HumanResources.Shift テーブルに 2 つの新しい勤務時間レコードを追加します。 アップデート グラムでは、オプションで指定されていない**\<する前に >** ブロックします。  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync>  
    <updg:after >  
       <HumanResources.Shift Name="Day-Evening"  
                        StartTime="1900-01-01 11:00:00.000"  
                        EndTime="1900-01-01 19:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
       <HumanResources.Shift Name="Evening-Night"  
                        StartTime="1900-01-01 19:00:00.000"  
                        EndTime="1900-01-01 03:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>スキーマに対してサンプル XPath クエリをテストするには  
  
1.  上のアップデートグラムをコピーして、テキスト ファイルに貼り付け、 Updategram-AddShifts.xml として保存します。  
  
2.  SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。  
  
     詳細については、次を参照してください。 [SQLXML 4.0 クエリの実行に ADO を使用する](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)します。  
  
 この例の別のバージョンは 2 つの個別を使用するアップデート グラム**\<後 >** 2 人の従業員を挿入する 1 つのブロックではなくブロックします。 これは有効であり、次のようにエンコードできます。  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync>  
    <updg:after >  
       <HumanResources.Shift Name="Day-Evening"  
                        StartTime="1900-01-01 11:00:00.000"  
                        EndTime="1900-01-01 19:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
    </updg:after>  
    <updg:before>  
    </updg:before>  
    <updg:after >  
       <HumanResources.Shift Name="Evening-Night"  
                        StartTime="1900-01-01 19:00:00.000"  
                        EndTime="1900-01-01 03:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
### <a name="c-working-with-valid-sql-server-characters-that-are-not-valid-in-xml"></a>C. SQL Server で有効で、XML では有効でない文字を処理する  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、テーブル名は、Northwind データベースの Order Details テーブルのようにスペースを含めて指定できます。 ただし、これは有効な XML 文字では有効ではありません[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]を使用して、識別子には有効でない XML 識別子をエンコードできます '__xHHHH\_\_' HHHH は 4 桁の 16 進数 ucs-2 コードのエンコードの値として最上位ビット順の文字。  
  
> [!NOTE]  
>  この例では Northwind データベースを使用します。 これからダウンロードして使用可能な SQL スクリプトを使用して、Northwind データベースをインストールする[Microsoft Web サイト](https://go.microsoft.com/fwlink/?LinkId=30196)します。  
  
 また、要素名を角かっこ () 内で囲む必要があります。 _X005B としてエンコードする必要がありますの文字 [と] は XML で有効ではありません、ため\_と _x005D\_、それぞれします。 マッピング スキーマを使用して、空白文字など有効でない文字を含まない要素名を指定することもできます。 この場合、マッピング スキーマで必要なマッピングが行われるので、これらの文字をエンコードする必要はありません。  
  
 次のアップデートグラムでは、Northwind データベースの Order Details テーブルにレコードを追加します。  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
    </updg:before>  
    <updg:after>  
      <_x005B_Order_x0020_Details_x005D_ OrderID="1"  
            ProductID="11"  
            UnitPrice="$1.0"  
            Quantity="1"  
            Discount="0.0" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 Order Details テーブル内の UnitPrice 列は `money` 型です。 `string` 型から `money` 型へ、適切な型変換を行うには、ドル記号 ($) を値の一部に追加する必要があります。 アップデートグラムでマッピング スキーマが指定されていない場合は、`string` 値の最初の文字が評価されます。 最初の文字がドル記号 ($) の場合、適切な変換が行われます。  
  
 アップデートグラムで指定したマッピング スキーマで、列が `dt:type="fixed.14.4"` または `sql:datatype="money"` として適切にマークされている場合は、ドル記号 ($) は必要なく、マッピングによって変換が処理されます。 適切な型変換が行われるようにするには、この方法が推奨されます。  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>スキーマに対してサンプル XPath クエリをテストするには  
  
1.  上のアップデートグラムをコピーして、テキスト ファイルに貼り付け、 UpdategramSpacesInTableName.xml として保存します。  
  
2.  SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。  
  
     詳細については、次を参照してください。 [SQLXML 4.0 クエリの実行に ADO を使用する](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)します。  
  
### <a name="d-using-the-at-identity-attribute-to-retrieve-the-value-that-has-been-inserted-in-the-identity-type-column"></a>D. at-identity 属性を使用して、IDENTITY 型の列に挿入されている値を取得する  
 次のアップデートグラムでは、Sales.SalesOrderHeader テーブルと Sales.SalesOrderDetail テーブルに 1 つずつ、合計 2 つのレコードを挿入します。  
  
 このアップデートグラムでは、最初にレコードを Sales.SalesOrderHeader テーブルに追加します。 このテーブルで、SalesOrderID 列は IDENTITY 型の列です。 したがって、このレコードをテーブルに追加するとき、アップデートグラムでは割り当てられている SalesOrderID 値を `at-identity` 属性に "x" (プレースホルダー値) としてキャプチャし、 この指定`at-identity`SalesOrderID 属性の値として変数、 \<Sales.SalesOrderDetail > 要素。  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
 <updg:sync >  
  <updg:before>  
  </updg:before>  
  <updg:after>  
   <Sales.SalesOrderHeader updg:at-identity="x"   
             RevisionNumber="1"  
             OrderDate="2001-07-01 00:00:00.000"  
             DueDate="2001-07-13 00:00:00.000"  
             OnlineOrderFlag="0"  
             CustomerID="676"  
             ContactID="378"  
             BillToAddressID="985"  
             ShipToAddressID="985"  
             ShipMethodID="5"  
             SubTotal="24643.9362"  
             TaxAmt="1971.5149"  
             Freight="616.0984"  
             rowguid="00001111-2222-3333-4444-556677889900"  
             ModifiedDate="2001-07-08 00:00:00.000" />  
      <Sales.SalesOrderDetail SalesOrderID="x"  
                LineNumber="1"  
                OrderQty="1"  
                ProductID="776"  
                SpecialOfferID="1"  
                UnitPrice="2429.9928"  
                UnitPriceDiscount="0.00"  
                rowguid="aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee"  
                ModifiedDate="2001-07-01 00:00:00.000" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 `updg:at-identity` 属性により生成される ID 値を返す場合は、`updg:returnid` 属性を使用できます。 次のアップデートグラムは、この ID 値を返すように変更されたものです。 例を少し複雑にするため、ここでは 2 つの注文レコードと 2 つの注文詳細レコードを追加します。  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
 <updg:sync>  
  <updg:before>  
  </updg:before>  
  <updg:after updg:returnid="x y" >  
       <HumanResources.Shift updg:at-identity="x" Name="Day-Evening"  
                        StartTime="1900-01-01 11:00:00.000"  
                        EndTime="1900-01-01 19:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
       <HumanResources.Shift updg:at-identity="y" Name="Evening-Night"  
                        StartTime="1900-01-01 19:00:00.000"  
                        EndTime="1900-01-01 03:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
  </updg:after>  
 </updg:sync>  
</ROOT>  
```  
  
 アップデートグラムを実行すると、次のような結果が返されます。この結果には、生成された ID 値 (テーブル ID に使用される ShiftID 列の生成値) が含まれます。  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">   
  <returnid>   
    <x>4</x>   
    <y>5</y>   
  </returnid>   
</ROOT>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>スキーマに対してサンプル XPath クエリをテストするには  
  
1.  上のアップデートグラムをコピーして、テキスト ファイルに貼り付け、 Updategram-returnId.xml として保存します。  
  
2.  SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。  
  
     詳細については、次を参照してください。 [SQLXML 4.0 クエリの実行に ADO を使用する](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)します。  
  
### <a name="e-using-the-updgguid-attribute-to-generate-a-unique-value"></a>E. updg:guid 属性を使用して一意な値を生成する  
 この例のアップデートグラムでは、Cust および CustOrder テーブルにレコードを挿入します。 また、`updg:guid` 属性を使用して、CustomerID 属性に一意な値を生成します。  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
    </updg:before>  
    <updg:after updg:returnid="x" >  
      <Cust updg:guid="x" >  
         <CustID>x</CustID>  
         <LastName>Fuller</LastName>  
      </Cust>  
      <CustOrder>  
         <CustID>x</CustID>  
         <OrderID>1</OrderID>  
      </CustOrder>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 このアップデートグラムでは、`returnid` 属性を指定しています。 結果として、生成された GUID が返されます。  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <returnid>  
    <x>7111BD1A-7F0B-4CEE-B411-260DADFEFA2A</x>   
  </returnid>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a>アップデートグラムをテストするには  
  
1.  上のアップデートグラムをコピーして、テキスト ファイルに貼り付け、 Updategram-GenerateGuid.xml として保存します。  
  
2.  これらのテーブルを作成します。  
  
    ```  
    USE tempdb  
    CREATE TABLE Cust (CustID uniqueidentifier, LastName varchar(20))  
    CREATE TABLE CustOrder (CustID uniqueidentifier, OrderID int)  
    ```  
  
3.  SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。  
  
     詳細については、次を参照してください。 [SQLXML 4.0 クエリの実行に ADO を使用する](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)します。  
  
### <a name="f-specifying-a-schema-in-an-updategram"></a>F. アップデートグラムでスキーマを指定する  
 この例のアップデートグラムでは、レコードを次のテーブルに挿入します。  
  
```  
CustOrder(OrderID, EmployeeID, OrderType)  
```  
  
 このアップデートグラムでは XSD スキーマを指定しています。アップデートグラム要素と属性に既定のマッピングはありません。 このスキーマでは、要素および属性からデータベース テーブルおよび列への必要なマッピングが提供されます。  
  
 次のスキーマ (CustOrderSchema.xml) について説明します、  **\<CustOrder >** 要素で構成される、 **OrderID**と**EmployeeID**属性。 スキーマをさらに興味深いにするために、既定値が割り当てられている、 **EmployeeID**属性。 アップデートグラムでは、属性の既定値は、アップデートグラムでその属性が指定されていない挿入操作のみに使用されます。  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="CustOrder" >  
   <xsd:complexType>  
        <xsd:attribute name="OrderID"     type="xsd:integer" />   
        <xsd:attribute name="EmployeeID"  type="xsd:integer" />  
        <xsd:attribute name="OrderType  " type="xsd:integer" default="1"/>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 このアップデートグラムでは、CustOrder テーブルにレコードを挿入します。 このアップデートグラムでは OrderID および EmployeeID 属性の値のみを指定し、 OrderType 属性の値は指定しません。 したがって、アップデートグラムでは、前のスキーマで指定されている EmployeeID 属性の既定値が使用されます。  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql"  
             xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync mapping-schema='CustOrderSchema.xml'>  
<updg:after>  
       <CustOrder OrderID="98000" EmployeeID="1" />  
</updg:after>  
</updg:sync>  
</ROOT>  
```  
  
 マッピング スキーマを指定するアップデート グラムの例については、次を参照してください。[アップデート グラムで注釈が付けられたマッピング スキーマの指定&#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)します。  
  
##### <a name="to-test-the-updategram"></a>アップデートグラムをテストするには  
  
1.  このテーブルを作成、 **tempdb**データベース。  
  
    ```  
    USE tempdb  
    CREATE TABLE CustOrder(  
                     OrderID int,   
                     EmployeeID int,   
                     OrderType int)  
    ```  
  
2.  上のスキーマをコピーして、テキスト ファイルに貼り付け、 CustOrderSchema.xml として保存します。  
  
3.  上のアップデートグラムをコピーして、テキスト ファイルに貼り付け、 上の手順と同じフォルダーに CustOrderUpdategram.xml として保存します。  
  
4.  SQLXML 4.0 テスト スクリプト (Sqlxml4test.vbs) を作成し、それを使用してアップデートグラムを実行します。  
  
     詳細については、次を参照してください。 [SQLXML 4.0 クエリの実行に ADO を使用する](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)します。  
  
 これは、同等の XDR スキーマです。  
  
```  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"  
        xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
 <ElementType name="CustOrder" >  
    <AttributeType name="OrderID" />  
    <AttributeType name="EmployeeID" />  
    <AttributeType name="OrderType" default="1" />  
    <attribute type="OrderID"  />  
    <attribute type="EmployeeID" />  
    <attribute type="OrderType" />  
  </ElementType>  
</Schema>  
```  
  
### <a name="g-using-the-xsinil-attribute-to-insert-null-values-in-a-column"></a>G. xsi:nil 属性を使用して列に null 値を挿入する  
 テーブル内の列に null 値を挿入する場合は、アップデートグラム内の対応する要素に `xsi:nil` 属性を指定します。 また、対応する XSD スキーマで、XSD `nillable` 属性も指定する必要があります。  
  
 たとえば、次の XSD スキーマを考えてみます。  
  
```  
<?xml version="1.0"?>  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:element name="Student" sql:relation="Students">  
  <xsd:complexType>  
    <xsd:all>  
      <xsd:element name="fname" sql:field="first_name"   
                                type="xsd:string"   
                                 nillable="true"/>  
    </xsd:all>  
    <xsd:attribute name="SID"   
                        sql:field="StudentID"  
                        type="xsd:ID"/>      
    <xsd:attribute name="lname"       
                        sql:field="last_name"  
                        type="xsd:string"/>  
    <xsd:attribute name="minitial"    
                        sql:field="middle_initial"   
                        type="xsd:string"/>  
    <xsd:attribute name="years"       
                         sql:field="no_of_years"  
                         type="xsd:integer"/>  
  </xsd:complexType>  
 </xsd:element>  
</xsd:schema>  
```  
  
 XSD スキーマを指定します**nillable ="true"** の **\<fname >** 要素。 このスキーマを使用するアップデートグラムは次のとおりです。  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql"  
      xmlns:updg="urn:schemas-microsoft-com:xml-updategram"  
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  
<updg:sync mapping-schema='StudentSchema.xml'>  
  <updg:before/>  
  <updg:after>  
    <Student SID="S00004" lname="Elmaci" minitial="" years="2">  
      <fname xsi:nil="true">  
    </fname>  
    </Student>  
  </updg:after>  
</updg:sync>  
  
</ROOT>  
```  
  
 アップデート グラムで指定`xsi:nil`の **\<fname >** 内の要素、 **\<後 >** ブロックします。 したがって、このアップデートグラムを実行すると、テーブルの first_name 列に NULL 値が挿入されます。  
  
##### <a name="to-test-the-updategram"></a>アップデートグラムをテストするには  
  
1.  次の表を作成、 **tempdb**データベース。  
  
    ```  
    USE tempdb  
    CREATE TABLE Students (  
       StudentID char(6)NOT NULL ,  
       first_name varchar(50),  
       last_name varchar(50),  
       middle_initial char(1),  
       no_of_years int NULL)  
    GO  
    ```  
  
2.  上のスキーマをコピーして、テキスト ファイルに貼り付け、 StudentSchema.xml として保存します。  
  
3.  上のアップデートグラムをコピーして、テキスト ファイルに貼り付け、 上の手順の StudentSchema.xml と同じフォルダーに StudentUpdategram.xml として保存します。  
  
4.  SQLXML 4.0 テスト スクリプト (Sqlxml4test.vbs) を作成し、それを使用してアップデートグラムを実行します。  
  
     詳細については、次を参照してください。 [SQLXML 4.0 クエリの実行に ADO を使用する](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)します。  
  
### <a name="h-specifying-namespaces-in-an-updategram"></a>H. アップデートグラムで名前空間を指定する  
 アップデートグラム内の要素で名前空間を宣言し、その名前空間に属する要素として、同じ要素を保持することができます。 この場合、対応するスキーマで同じ名前空間を宣言する必要があり、対象の名前空間に要素が属している必要があります。  
  
 たとえば、次のアップデート グラム (Updategram-elementhavingnamespace.xml) で、 **\<順序 >** 要素は、要素で宣言された名前空間に属します。  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync mapping-schema='XSD-ElementHavingNameSpace.xml'>  
    <updg:after>  
       <x:Order  xmlns:x="http://server/xyz/schemas/"  
             updg:at-identity="SalesOrderID"   
             RevisionNumber="1"  
             OrderDate="2001-07-01 00:00:00.000"  
             DueDate="2001-07-13 00:00:00.000"  
             OnlineOrderFlag="0"  
             CustomerID="676"  
             ContactID="378"  
             BillToAddressID="985"  
             ShipToAddressID="985"  
             ShipMethodID="5"  
             SubTotal="24643.9362"  
             TaxAmt="1971.5149"  
             Freight="616.0984"  
             rowguid="00009999-8888-7777-6666-554433221100"  
             ModifiedDate="2001-07-08 00:00:00.000" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 この場合、このスキーマに示すように、スキーマでも名前空間を宣言する必要があります。  
  
 次のスキーマ (XSD-ElementHavingNamespace.xml) では、対応する要素と属性の宣言方法を示しています。  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
     xmlns:dt="urn:schemas-microsoft-com:datatypes"   
     xmlns:sql="urn:schemas-microsoft-com:mapping-schema"    
     xmlns:x="http://server/xyz/schemas/"   
     targetNamespace="http://server/xyz/schemas/" >  
  <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader" type="x:Order_type"/>  
  <xsd:complexType name="Order_type">  
    <xsd:attribute name="SalesOrderID"  type="xsd:ID"/>  
    <xsd:attribute name="RevisionNumber" type="xsd:unsignedByte"/>  
    <xsd:attribute name="OrderDate" type="xsd:dateTime"/>  
    <xsd:attribute name="DueDate" type="xsd:dateTime"/>  
    <xsd:attribute name="ShipDate" type="xsd:dateTime"/>  
    <xsd:attribute name="Status" type="xsd:unsignedByte"/>  
    <xsd:attribute name="OnlineOrderFlag" type="xsd:boolean"/>  
    <xsd:attribute name="SalesOrderNumber" type="xsd:string"/>  
    <xsd:attribute name="PurchaseOrderNumber" type="xsd:string"/>  
    <xsd:attribute name="AccountNumber" type="xsd:string"/>  
    <xsd:attribute name="CustomerID" type="xsd:int"/>  
    <xsd:attribute name="ContactID" type="xsd:int"/>  
    <xsd:attribute name="SalesPersonID" type="xsd:int"/>  
    <xsd:attribute name="TerritoryID" type="xsd:int"/>  
    <xsd:attribute name="BillToAddressID" type="xsd:int"/>  
    <xsd:attribute name="ShipToAddressID" type="xsd:int"/>  
    <xsd:attribute name="ShipMethodID" type="xsd:int"/>  
    <xsd:attribute name="CreditCardID" type="xsd:int"/>  
    <xsd:attribute name="CreditCardApprovalCode" type="xsd:string"/>  
    <xsd:attribute name="CurrencyRateID" type="xsd:int"/>  
    <xsd:attribute name="SubTotal" type="xsd:decimal"/>  
    <xsd:attribute name="TaxAmt" type="xsd:decimal"/>  
    <xsd:attribute name="Freight" type="xsd:decimal"/>  
    <xsd:attribute name="TotalDue" type="xsd:decimal"/>  
    <xsd:attribute name="Comment" type="xsd:string"/>  
    <xsd:attribute name="rowguid" type="xsd:string"/>  
    <xsd:attribute name="ModifiedDate" type="xsd:dateTime"/>  
  </xsd:complexType>  
</xsd:schema>  
```  
  
##### <a name="to-test-the-updategram"></a>アップデートグラムをテストするには  
  
1.  上のスキーマをコピーして、テキスト ファイルに貼り付け、 XSD-ElementHavingNamespace.xml として保存します。  
  
2.  上のアップデートグラムをコピーして、テキスト ファイルに貼り付け、 XSD-ElementHavingnamespace.xml と同じフォルダーに Updategram-ElementHavingNamespace.xml として保存します。  
  
3.  SQLXML 4.0 テスト スクリプト (Sqlxml4test.vbs) を作成し、それを使用してアップデートグラムを実行します。  
  
     詳細については、次を参照してください。 [SQLXML 4.0 クエリの実行に ADO を使用する](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)します。  
  
### <a name="i-inserting-data-into-an-xml-data-type-column"></a>I. XML データ型列にデータを挿入する  
 `xml` データ型は、[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] で導入されました。 アップデートグラムを使用して、`xml` データ型の列にデータを挿入したり、この列に格納されているデータを更新することができます。これには次の条件があります。  
  
-   `xml` 列は、既存の行の識別に使用できません。 したがって、アップデートグラムの `updg:before` セクションに含めることはできません。  
  
-   `xml` 列に挿入される XML フラグメントのスコープにある名前空間は保持されます。挿入されたフラグメントの最上位要素には、その名前空間宣言が追加されます。  
  
 たとえば、次のアップデート グラム (SampleUpdateGram.xml) で、  **\<Desc >** 要素で、運用環境で ProductDescription 列が更新 > productModel テーブルの[!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)]サンプル データベース。 このアップデート グラムの結果は、ProductDescription 列の XML の内容が更新プログラムの XML の内容を **\<Desc >** 要素。  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
    <updg:sync mapping-schema="SampleSchema.xml" >  
       <updg:before>  
<ProductModel ProductModelID="19">  
   <Name>Mountain-100</Name>  
</ProductModel>  
    </updg:before>  
    <updg:after>  
 <ProductModel>  
    <Name>Mountain-100</Name>  
    <Desc><?xml-stylesheet href="ProductDescription.xsl" type="text/xsl"?>  
        <p1:ProductDescription xmlns:p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription"   
              xmlns:wm="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain"   
              xmlns:wf="http://www.adventure-works.com/schemas/OtherFeatures"   
              xmlns:html="http://www.w3.org/1999/xhtml"   
              xmlns="">  
  <p1:Summary>  
     <html:p>Insert Example</html:p>  
  </p1:Summary>  
  <p1:Manufacturer>  
    <p1:Name>AdventureWorks</p1:Name>  
    <p1:Copyright>2002</p1:Copyright>  
    <p1:ProductURL>HTTP://www.Adventure-works.com</p1:ProductURL>  
  </p1:Manufacturer>  
  <p1:Features>These are the product highlights.   
    <wm:Warranty>  
       <wm:WarrantyPeriod>3 years</wm:WarrantyPeriod>  
       <wm:Description>parts and labor</wm:Description>  
    </wm:Warranty>  
    <wm:Maintenance>  
       <wm:NoOfYears>10 years</wm:NoOfYears>  
       <wm:Description>maintenance contract available through your dealer or any AdventureWorks retail store.</wm:Description>  
    </wm:Maintenance>  
    <wf:wheel>High performance wheels.</wf:wheel>  
    <wf:saddle>  
      <html:i>Anatomic design</html:i> and made from durable leather for a full-day of riding in comfort.</wf:saddle>  
    <wf:pedal>  
       <html:b>Top-of-the-line</html:b> clipless pedals with adjustable tension.</wf:pedal>  
    <wf:BikeFrame>Each frame is hand-crafted in our Bothell facility to the optimum diameter and wall-thickness required of a premium mountain frame. The heat-treated welded aluminum frame has a larger diameter tube that absorbs the bumps.</wf:BikeFrame>  
    <wf:crankset> Triple crankset; alumunim crank arm; flawless shifting. </wf:crankset>  
   </p1:Features>  
   <p1:Picture>  
      <p1:Angle>front</p1:Angle>  
      <p1:Size>small</p1:Size>  
      <p1:ProductPhotoID>118</p1:ProductPhotoID>  
   </p1:Picture>  
   <p1:Specifications> These are the product specifications.  
     <Material>Almuminum Alloy</Material>  
     <Color>Available in most colors</Color>  
     <ProductLine>Mountain bike</ProductLine>  
     <Style>Unisex</Style>  
     <RiderExperience>Advanced to Professional riders</RiderExperience>  
   </p1:Specifications>  
  </p1:ProductDescription>  
 </Desc>  
      </ProductModel>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 このアップデートグラムでは、次の注釈付き XSD スキーマ (SampleSchema.xml) を参照しています。  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
           xmlns:sql="urn:schemas-microsoft-com:mapping-schema"  
           xmlns="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription">   
  <xsd:element name="ProductModel"  sql:relation="Production.ProductModel" >  
     <xsd:complexType>  
       <xsd:sequence>  
          <xsd:element name="Name" type="xsd:string"></xsd:element>  
          <xsd:element name="Desc" sql:field="CatalogDescription" sql:datatype="xml">  
           <xsd:complexType>  
            <xsd:sequence>  
              <xsd:element name="ProductDescription">  
                 <xsd:complexType>  
                   <xsd:sequence>  
                     <xsd:element name="Summary" type="xsd:anyType">  
                     </xsd:element>  
                   </xsd:sequence>  
                 </xsd:complexType>  
              </xsd:element>  
            </xsd:sequence>  
           </xsd:complexType>  
          </xsd:element>   
       </xsd:sequence>  
       <xsd:attribute name="ProductModelID" sql:field="ProductModelID"/>  
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-the-updategram"></a>アップデートグラムをテストするには  
  
1.  上のスキーマをコピーして、テキスト ファイルに貼り付け、 XSD-SampleSchema.xml として保存します。  
  
    > [!NOTE]  
    >  アップデートグラムでは既定のマッピングがサポートされるので、`xml` データ型の開始位置と終了位置を識別する方法はありません。 つまり、`xml` データ型の列を含むテーブルを挿入または更新するときには、マッピング スキーマが必要です。 スキーマを指定しない場合、SQLXML では、テーブル内の列の 1 つが見つからないというエラーが返されます。  
  
2.  上のアップデートグラムをコピーして、テキスト ファイルに貼り付け、 SampleSchema.xml と同じフォルダーに SampleUpdategram.xml として保存します。  
  
3.  SQLXML 4.0 テスト スクリプト (Sqlxml4test.vbs) を作成し、それを使用してアップデートグラムを実行します。  
  
     詳細については、次を参照してください。 [SQLXML 4.0 クエリの実行に ADO を使用する](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)します。  
  
## <a name="see-also"></a>参照  
 [アップデート グラムのセキュリティに関する考慮事項&#40;SQLXML 4.0&#41;](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
