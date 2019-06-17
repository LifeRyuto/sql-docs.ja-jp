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
manager: kfile
ms.openlocfilehash: 71235953f592572bd7ac0dcb2493d97dd509f8b7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63269943"
---
# <a name="linkmember-mdx"></a>LinkMember (MDX)


  指定された階層の指定されたメンバーと等価のメンバーを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
LinkMember(Member_Expression, Hierarchy_Expression)   
```  
  
## <a name="arguments"></a>引数  
 *メンバー式*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
 *Hierarchy_Expression*  
 階層を返す有効な多次元式 (MDX) 式。  
  
## <a name="remarks"></a>コメント  
 **LinkMember**関数は、関連する階層で指定されたメンバーの各レベルのキーの値に一致する指定された階層からメンバーを返します。 各レベルでの属性には、同じキーのカーディナリティおよびデータ型が必要です。 不自然階層では、属性のキー値が複数一致する場合、結果はエラーまたは不確定になります。  
  
## <a name="examples"></a>使用例  
 次の例では、 **LinkMember**関数を Calendar 階層にある Date.Date 属性階層の July 1, 2002年メンバーの先祖の Adventure Works キューブ内の既定のメジャーを返します。  
  
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
 [先祖&#40;MDX&#41;](../mdx/ascendants-mdx.md)   
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
