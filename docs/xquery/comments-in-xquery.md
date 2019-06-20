---
title: XQuery のコメント |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- comments [XQuery]
- XQuery, comments
ms.assetid: 4d977268-de9d-4bf0-b310-b63f6a0fb0db
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 32047da9a95190f0099d1a84bceef13540143223
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63047606"
---
# <a name="comments-in-xquery"></a>XQuery のコメント
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  XQuery にコメントを追加することができます。 使用して、コメントの文字列が追加されて、"`(:`「と」`:)`"区切り記号。 例 :  
  
```  
declare @x xml  
set @x=''  
SELECT @x.query('  
(: simple query to construct an element :)  
<ProductModel ProductModelID="10" />  
')  
```  
  
 次に、別の例の Instruction 列に対してクエリが指定されて、 **xml**型。  
  
```  
SELECT Instructions.query('  
(: declare prefix and namespace binding in the prolog. :)  
     declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
  (: Following expression retrieves the <Location> element children of the <root> element. :)  
  /AWMI:root/AWMI:Location  
') as Result  
FROM Production.ProductModel  
where ProductModelID=7  
```  
  
  
