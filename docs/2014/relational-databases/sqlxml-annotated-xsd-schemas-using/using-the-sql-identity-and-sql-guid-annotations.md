---
title: Sql:identity 注釈と sql:guid 注釈の使用 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- sql:guid
- annotated XSD schemas, IDENTITY-type columns
- annotated XSD schemas, GUID values
- DiffGrams [SQLXML], annotations
- identity annotation
- XSD schemas [SQLXML], GUID values
- GUIDs [SQLXML]
- guid annotation
- sql:identity
- IDENTITY-type column
- XSD schemas [SQLXML], IDENTITY-type columns
- updategrams [SQLXML], GUID values
ms.assetid: 7661dfd0-6573-4692-a8f1-3597adcd33c4
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: bb953042707054a7dbfdee697b986e7e65f7059b
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52786184"
---
# <a name="using-the-sqlidentity-and-sqlguid-annotations"></a>sql:identity 注釈と sql:guid 注釈の使用
  指定することができます、`sql:identity`と`sql:guid`でデータベース列にマップされる任意のノードの XSD スキーマで注釈[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 アップデートグラムの形式では `updg:at-identity` 属性と `updg:guid` 属性がサポートされますが、DiffGram の形式ではこれらの属性はサポートされません。 `updg:at-identity` 属性では、IDENTITY 型の列を更新するときの動作を定義します。 `updg:guid` 属性では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] から GUID 値を取得でき、その値をアップデートグラムで使用できます。 詳細と実際のサンプルは、[を挿入するデータを使用して XML アップデート グラム&#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md)を参照してください。  
  
 `sql:identity` 注釈と `sql:guid` 注釈を使用すると、この機能が DiffGram にも拡張されます。  
  
 DiffGram を実行すると、DiffGram がアップデートグラムに変換された後、アップデートグラムが実行されます。 この場合、XSD スキーマで `sql:identity` 注釈と `sql:guid` 注釈を指定することで、アップデートグラムの動作を定義することになります。 したがって、すべての注釈はアップデートグラムのコンテキストで記述します。 これらの注釈は DiffGram とアップデートグラムの両方で使用できますが、アップデートグラムには ID 値と GUID 値をより効率的に処理する機能が既に用意されています。  
  
 `sql:identity` 注釈と `sql:guid` 注釈は、複合コンテンツを含む要素に定義できます。  
  
## <a name="sqlidentity-annotation"></a>sql:identity 注釈  
 `sql:identity` 注釈は、XSD スキーマで、IDENTITY 型のデータベース列にマップされる任意のノードに指定できます。 この注釈に指定された値は、IDENTITY 型の列を更新する方法を定義します (いずれかの列を変更するアップデート グラムで指定された値を使用するか、その場合、値を無視することによって、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-生成された値がこの列の使用)。  
  
 `sql:identity` 注釈には次の 2 つの値を割り当てることができます。  
  
 ignore  
 アップデートグラムで列に提供される値を無視し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で生成される ID 値を使用します。  
  
 useValue  
 アップデートグラムで提供される値を使用して、IDENTITY 型列を更新します。 アップデートグラムでは、列が ID 値かどうかは確認されません。  
  
 アップデートグラムで IDENTITY 型列に値を指定する場合は、スキーマで `sql:identity="useValue"` を指定する必要があります。  
  
## <a name="sqlguid-annotation"></a>sql:guid 注釈  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で GUID 値を生成し、その値をアップデートグラムで使用できます。 DiffGram のコンテキストでは `sql:guid` 注釈を使用して、列に対し SQL Server で生成される GUID 値を使用するか、アップデートグラムで提供される値を使用するかを指定できます。  
  
 `sql:guid` 注釈には次の 2 つの値を割り当てることができます。  
  
 generate  
 更新操作で、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で生成される GUID を列に使用することを指定します。  
  
 useValue  
 アップデートグラムで提供される値を列に使用することを指定します。 これが既定値です。  
  
  
