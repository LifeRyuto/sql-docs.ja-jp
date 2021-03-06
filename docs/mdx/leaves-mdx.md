---
title: リーフ (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: d29c77250c23900d74d1969a6c37bc719c89cdd7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67905732"
---
# <a name="leaves-mdx"></a>リーフ (MDX)


  すべての属性で構成されるセットを返します (オプションで、特定のディメンションに属するものに限定されます)。 X が粒度属性であるか、直接または間接的に粒度属性に関連付けられている場合、戻りセット内の各属性 x について、粒度はスライスに影響を与えずに属性 x に設定されます。 **リーフ**関数は、SCOPE ステートメント内または代入の左側で使用するように設計されています。  
  
## <a name="syntax"></a>構文  
  
```  
  
Leaves( [ Dimension_expression ] )  
```  
  
## <a name="arguments"></a>引数  
 *Dimension_Expression*  
 ディメンションを返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 リーフメンバーは、すべての属性階層の最下位レベルのクロス結合によって形成される組です。 計算されるメンバーは除外されます。  
  
-   ディメンション名が指定されている場合、**リーフ関数は、指定**されたディメンションのキー属性のリーフメンバーを含むセットを返します。  
  
-   ディメンションが複数のメジャーグループに関連付けられている場合は、現在のスコープのメジャーのメジャーが使用されます。  
  
-   ディメンション名が指定されていない場合は、キューブ全体のリーフ メンバーで構成されるセットを返します。  
  
    > [!NOTE]  
    >  ディメンション式が階層に解決され、階層の一意の名前がディメンションの一意名 (キューブディメンションプロパティ HierarchyUniqueNameStyle = ExcludeDimensionName、階層名 = ディメンション名) と同じ場合、ディメンションは次のようになります。用い.  
  
    > [!IMPORTANT]  
    >  現在のスコープ内のメジャーグループに対して、すべての属性の粒度が同じでない場合は、エラーが生成されます。  
  
## <a name="see-also"></a>参照  
 [Mdx 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
