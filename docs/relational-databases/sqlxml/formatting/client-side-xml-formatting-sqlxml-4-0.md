---
title: クライアント側の XML の書式設定 (SQLXML 4.0) |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- FOR XML clause, formatting
- middle tier XML formatting [SQLXML]
- client-side XML formatting
- client-side-xml attribute
ms.assetid: 9630a21d-a93b-4d3b-8a25-c4b32399f993
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 95ed0b26f885474b87b45addd08dfcdb67b4bff9
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56016933"
---
# <a name="client-side-xml-formatting-sqlxml-40"></a>クライアント側の XML 書式設定 (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  ここでは、クライアント側の XML 書式設定に関する情報を提供します。 クライアント側の書式設定とは、中間層での XML の書式設定を指します。  
  
> [!NOTE]  
>  ここでは、クライアント側での FOR XML 句の使用に関する追加情報を提供します。ここでは、FOR XML 句について理解していることを前提としています。 FOR XML の詳細についてを参照してください[を構築する XML を使用しての XML](../../../relational-databases/xml/for-xml-sql-server.md)。  
  
 **重要な**新しいクライアント側の XML 機能を使用する**xml**データ型では、クライアントを使用する必要があります常に、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] SQLOLEDB プロバイダーではなくデータ プロバイダーのネイティブ クライアント (SQLNCLI11)。 SQLNCLI11 は、最新バージョンの SQL Server プロバイダーであり、[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] で導入されたデータ型を完全に認識します。 SQLOLEDB プロバイダーでは、FOR XML を処理するクライアント側の動作**xml**の文字列としてのデータ型です。  
  
## <a name="formatting-xml-documents-on-the-client-side"></a>クライアント側での XML ドキュメントの書式設定  
 クライアント アプリケーションで次のクエリを実行するとします。  
  
```  
SELECT FirstName, LastName  
FROM   Person.Contact  
FOR XML RAW  
```  
  
 この場合、クエリの次の部分だけがサーバーに送信されます。  
  
```  
SELECT FirstName, LastName  
FROM   Person.Contact  
```  
  
 サーバーはクエリを実行し、クライアントに行セットを含む] フィールドと [LastNamecolumns) を返します。 次に、中間層で、行セットに FOR XML 変換が適用され、XML の書式設定がクライアントに返されます。  
  
 同様に、XPath クエリを実行すると、サーバーからクライアントに行セットが返され、クライアント側で行セットに FOR XML EXPLICIT 変換が適用されて、目的の XML の書式設定が生成されます。  
  
 次の表は、クライアント側の FOR XML で指定できるモードです。  
  
|クライアント側の FOR XML のモード|解説|  
|-------------------------------|-------------|  
|RAW|クライアント側とサーバー側のどちらの FOR XML で指定しても、同じ結果が生成されます。|  
|NESTED|サーバー側で FOR XML AUTO モードを指定した場合と同様です。|  
|EXPLICIT|サーバー側で FOR XML EXPLICIT モードを指定した場合と同様です。|  
  
> [!NOTE]  
>  AUTO モードを指定してクライアント側の XML 書式設定を要求すると、クエリ全体がサーバーに送信され、XML 書式設定はサーバー側で実行されます。 このモードは便利ですが、NESTED モードを指定した場合は、生成される XML ドキュメント内の要素名としてベース テーブル名が返される点に注意してください。 使用するアプリケーションによっては、ベース テーブル名が必要です。 たとえば、ストアド プロシージャを実行し、結果のデータを [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework のデータセットに読み込んだ後で、テーブルのデータを更新する DiffGram を生成するとします。 この場合、ベース テーブル情報が必要となるため、NESTED モードを使用する必要があります。  
  
## <a name="benefits-of-client-side-xml-formatting"></a>クライアント側の XML 書式設定の利点  
 次に、クライアント側の XML 書式設定の利点をいくつか紹介します。  
  
### <a name="if-you-have-stored-procedures-on-the-server-that-return-a-single-rowset-you-can-request-client-side-for-xml-transformation-to-generate-an-xml"></a>サーバーに単一の行セットを返すストアド プロシージャがある場合、クライアント側の FOR XML 変換を要求して XML を生成できる。  
 たとえば、次のストアド プロシージャを考えてみます。 このプロシージャでは、従業員の姓と名前が AdventureWorks データベースの Person.Contact テーブルから返されます。  
  
```  
IF EXISTS (SELECT name FROM sysobjects  
   WHERE name = 'GetContacts' AND type = 'P')  
   DROP PROCEDURE GetContacts  
GO  
CREATE PROCEDURE GetContacts  
AS  
    SELECT   FirstName, LastName  
    FROM     Person.Contact  
```  
  
 このストアド プロシージャを、次のサンプル XML テンプレートで実行します。 このとき、FOR XML 句をストアド プロシージャ名の後に指定します。  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query client-side-xml="1">  
    EXEC GetContacts FOR XML NESTED  
  </sql:query>  
</ROOT>  
```  
  
 **クライアント側の xml**属性が 1 (true) に、テンプレートの設定、サーバー上でストアド プロシージャを実行し、サーバーによって返される 2 つの列の行セットが中間層で XML に変換してに返されるクライアントです。 次に示すのは結果の一部です。  
  
```  
 <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Person.Contact FirstName="Gustavo" LastName="Achong" />   
  <Person.Contact FirstName="Catherine" LastName="Abel" />  
</ROOT>  
```  
  
> [!NOTE]  
>  SQLXMLOLEDB プロバイダーまたは SQLXML マネージ クラスを使用しているときに使用できます、 **ClientSideXml**プロパティをクライアント側の XML 書式設定を要求します。  
  
### <a name="the-workload-is-more-balanced"></a>ワークロードをより適切に分散できる。  
 クライアントで XML 書式設定を行うため、サーバーとクライアント間でワークロードがより適切に分散され、サーバーで他の処理を実行できるようになります。  
  
## <a name="supporting-client-side-xml-formatting"></a>クライアント側の XML 書式設定のサポート  
 クライアント側の XML 書式設定機能をサポートするため、SQLXML では次のコンポーネントが提供されます。  
  
-   SQLXMLOLEDB プロバイダー  
  
-   SQLXML マネージド クラス  
  
-   拡張 XML テンプレートのサポート  
  
-   SqlXmlCommand.ClientSideXml プロパティ  
  
     SQLXML マネージド クラスのこのプロパティを true に設定すると、クライアント側の書式設定を指定できます。  
  
## <a name="enhanced-xml-template-support"></a>強化された XML テンプレートのサポート  
 始まる[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]、XML テンプレートに[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]の追加により強化されています、**クライアント側の xml**属性です。 この属性を true に設定すると、XML がクライアント側で書式設定されます。 SQLXMLOLEDB プロバイダーに固有の ClientSideXML プロパティと同じ機能でこのテンプレートの属性であるに注意してください。  
  
> [!NOTE]  
>  SQLXMLOLEDB プロバイダーを使用している ADO アプリケーションでの XML テンプレートを実行して、両方を指定する場合、**クライアント側の xml**テンプレートと ClientSideXML プロパティで指定された値プロバイダー内の属性、テンプレートが優先されます。  
  
## <a name="see-also"></a>参照  
 [クライアント側とサーバー側の XML 書式設定のアーキテクチャ&#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml/formatting/architecture-of-client-side-and-server-side-xml-formatting-sqlxml-4-0.md)   
 [FOR XML &#40;SQL Server&#41;](../../../relational-databases/xml/for-xml-sql-server.md)   
 [XML のセキュリティに関する考慮事項の&#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/security/for-xml-security-considerations-sqlxml-4-0.md)   
 [xml SQLXML 4.0 でのデータ型のサポート](../../../relational-databases/sqlxml/xml-data-type-support-in-sqlxml-4-0.md)   
 [SQLXML マネージ クラス](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/sqlxml-4-0-net-framework-support-managed-classes.md)   
 [クライアント側とサーバー側の XML 書式設定&#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml/formatting/client-side-vs-server-side-xml-formatting-sqlxml-4-0.md)   
 [SqlXmlCommand オブジェクト&#40;SQLXML マネージ クラス&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/sqlxml-managed-classes-sqlxmlcommand-object.md)   
 [XML データ &#40;SQL Server&#41;](../../../relational-databases/xml/xml-data-sql-server.md)  
  
  
