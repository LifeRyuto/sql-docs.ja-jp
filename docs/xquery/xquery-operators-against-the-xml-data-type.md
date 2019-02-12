---
title: Xml データ型に対しての XQuery 演算子 |Microsoft Docs
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
- XQuery, operators
- operators [XQuery]
- xml data type [SQL Server], XQuery
ms.assetid: 39ca3d2e-e928-4333-872b-75c4ccde8e79
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 2786295b344cfc2df6ae613e42a39f71aee4d3d8
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56038893"
---
# <a name="xquery-operators-against-the-xml-data-type"></a>xml データ型に対する XQuery の演算子
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  XQuery では、次の演算子がサポートされています。  
  
-   数値演算子 (+、-、*、div、mod)  
  
-   値の比較演算子 (eq、ne、lt、gt、le、ge)  
  
-   一般的な比較演算子 (=、! =、 \<、>、 \<=、> =)  
  
 これらの演算子の詳細については、次を参照してください[比較式&#40;XQuery。&#41;](../xquery/comparison-expressions-xquery.md)  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-general-operators"></a>A. 一般的な演算子の使用  
 次のクエリでは、シーケンスおよびシーケンスの比較に適用される一般的な演算子の用途について説明します。 クエリは、各顧客からの電話番号のシーケンスを取得する、 **AdditionalContactInfo**の列、**連絡先**テーブル。 取得されたシーケンスは、2 つの電話番号 ("111-111-1111"、"222-2222") のシーケンスと比較されます。  
  
 クエリを使用して、 **=** 比較演算子。 右側にあるシーケンス内の各ノード、 **=** 演算子が左側にあるシーケンス内の各ノードと比較されます。 ノードの比較では、ノードが一致している場合**TRUE**します。 次に、シーケンスは int 型に変換されて 1 と比較され、クエリが顧客 ID を返します。  
  
```sql
WITH XMLNAMESPACES (  
'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo' AS ACI,  
'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes' AS ACT)  
SELECT ContactID   
FROM   Person.Contact  
WHERE  AdditionalContactInfo.value('  
      //ACI:AdditionalContactInfo//ACT:telephoneNumber/ACT:number =   
          ("111-111-1111", "222-2222")',  
      'bit')= cast(1 as bit)  
```  
  
 前のクエリの動作を観察する別の方法があります。各電話番号の値から取得した、 **AdditionalContactInfo**列が 2 つの電話番号のセットと比較されます。 値がセット内にある場合、その顧客が結果に返されます。  
  
### <a name="b-using-a-numeric-operator"></a>B. 数値演算子の使用  
 このクエリの + 演算子は 1 つのアイテムに適用されるので、値の演算子です。 たとえば、クエリによって返されたロット サイズに値 1 が加算されます。  
  
```sql
SELECT ProductModelID, Instructions.query('  
     declare namespace   
 AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
     for $i in (/AWMI:root/AWMI:Location)[1]  
     return   
       <Location LocationID="{ ($i/@LocationID) }"  
                   LotSize  = "{  number($i/@LotSize) }"  
                   LotSize2 = "{ number($i/@LotSize) + 1 }"  
                   LotSize3 = "{ number($i/@LotSize) + 2 }" >  
  
       </Location>  
') as Result  
FROM Production.ProductModel  
where ProductModelID=7  
```  
  
### <a name="c-using-a-value-operator"></a>C. 値の演算子の使用  
 次のクエリでは、写真のサイズが "small" である製品モデルの <`Picture`> 要素が取得されます。  
  
```sql
SELECT CatalogDescription.query('  
     declare namespace PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
     for $P in /PD:ProductDescription/PD:Picture[PD:Size eq "small"]  
     return  
           $P  
    ') as Result  
FROM Production.ProductModel  
where ProductModelID=19  
```  
  
 に、両方のオペランド、 **eq**演算子はアトミック値、値の演算子は、クエリで使用します。 一般的な比較演算子を使用して、同じクエリを記述することができます ( **=** )。  
  
## <a name="see-also"></a>参照  
 [Xml データ型に対する XQuery 関数](../xquery/xquery-functions-against-the-xml-data-type.md)   
 [XML データ &#40;SQL Server&#41;](../relational-databases/xml/xml-data-sql-server.md)   
 [XQuery 言語リファレンス &#40;SQL Server&#41;](../xquery/xquery-language-reference-sql-server.md)  
  
  
