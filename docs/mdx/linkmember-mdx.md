---
title: LinkMember (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 8a00388e067878d9c2165cbae6844f8020b7c63e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67905603"
---
# <a name="linkmember-mdx"></a>LinkMember (MDX)


  指定された階層の指定されたメンバーと等価のメンバーを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
LinkMember(Member_Expression, Hierarchy_Expression)   
```  
  
## <a name="arguments"></a>引数  
 *Member_Expression*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
 *Hierarchy_Expression*  
 階層を返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 **Linkmember**関数は、指定された階層から、関連する階層内の指定されたメンバーの各レベルのキー値と一致するメンバーを返します。 各レベルの属性は、キーのカーディナリティとデータ型が同じである必要があります。 不自然階層では、属性のキー値が複数一致する場合、結果はエラーまたは不確定になります。  
  
## <a name="examples"></a>例  
 次の例では、 **Linkmember**関数を使用して、Calendar 階層の Date. date 属性階層にある2002年7月1日のメンバーの先祖の Adventure works キューブの既定のメジャーを返します。  
  
```  
SELECT  Hierarchize  
   (Ascendants   
      (LinkMember   
         ([Date].[Date].[July 1, 2002], [Date].[Calendar]  
         )  
       )  
    ) ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [Hierarchize &#40;MDX&#41;](../mdx/hierarchize-mdx.md)   
 [先祖 &#40;MDX&#41;](../mdx/ascendants-mdx.md)   
 [Mdx 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
