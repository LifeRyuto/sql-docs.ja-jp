---
title: 変数とパラメーター (MDX) の使用 |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: deb1f7b4e641dd2347e8629e1e13ad3f4da7788c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62989365"
---
# <a name="using-variables-and-parameters-mdx"></a>変数とパラメーターの使用 (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
   [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]では、多次元式 (MDX) ステートメントをパラメーター化できます。 ステートメントをパラメーター化すれば、実行時にカスタマイズ可能な汎用ステートメントを作成できます。  
  
 パラメーター化されたステートメントを作成するときには、パラメーター名の前に @ 記号を付けることによってパラメーター名を識別します。 たとえば、@Year有効なパラメーター名になります。  
  
 MDX は、リテラルまたはスカラー値用のパラメーターだけをサポートします。 メンバー、セット、または組を参照するパラメーターを作成するには、 [StrToMember](../../../mdx/strtomember-mdx.md) や [StrToSet](../../../mdx/strtoset-mdx.md)などの関数を使う必要があります。  
  
 次の XML for Analysis (XMLA) の例で、@CountryNameパラメーター データを取得する顧客の国が含まれます。  
  
```  
<Envelope xmlns="http://schemas.xmlsoap.org/soap/envelope/">  
  <Body>  
    <Execute xmlns="urn:schemas-microsoft-com:xml-analysis">  
      <Command>  
        <Statement>  
select [Measures].members on 0,   
       Filter(Customer.[Customer Geography].Country.members,   
              Customer.[Customer Geography].CurrentMember.Name =  
              @CountryName) on 1  
from [Adventure Works]  
</Statement>  
      </Command>  
      <Properties />  
      <Parameters>  
        <Parameter>  
          <Name>CountryName</Name>  
          <Value>'United Kingdom'</Value>  
        </Parameter>  
      </Parameters>  
    </Execute>  
  </Body>  
</Envelope>  
```  
  
 OLE DB でこの機能を使用するには、 **ICommandWithParameters** インターフェイスを使用します。 ADOMD.Net でこの機能を使用するには、 **AdomdCommand.Parameters** コレクションを使用します。  
  
## <a name="see-also"></a>参照  
 [MDX スクリプティングの基礎 &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md)  
  
  
