---
title: CREATE MEASURE ステートメント (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 37a8b8ef757184e7467c3551148c8c149bb45097
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63309095"
---
# <a name="mdx-data-definition---create-measure"></a>MDX データ操作 - CREATE MEASURE


  テーブル モデルでメジャーを作成します。  
  
## <a name="syntax"></a>構文  
  
```  
  
CREATE MEASURE Table_Name[Measure_Name] = DAX_Expression  
[; CREATE MEASURE ...n]  
  
```  
  
## <a name="arguments"></a>引数  
 *Table_Name*  
 メジャーを作成するテーブルの名前を指定する有効な文字列リテラルです。  
  
 *Measure_Name*  
 メジャー名を指定する有効な文字列リテラルです。  
  
 *DAX_Expression*  
 1 つのスカラー値を返す有効な DAX 式を入力します。  
  
## <a name="remarks"></a>コメント  
 *Measure_Name*角かっこで囲む必要があります。  
  
 CREATE MEASURE ステートメントは、MDX スクリプト定義; の内部でのみ使用できます。参照してください[MdxScript 要素&#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/objects/mdxscript-element-assl)します。  
  
 1 つのクエリだけで使用する計算されるメンバーを定義することも可能です。 1 つのクエリに限定される計算されるメンバーを定義するには、SELECT ステートメントで WITH 句を使用します。 詳細については、次を参照してください。 [MDX でのメジャーの作成](../analysis-services/multidimensional-models/mdx/mdx-building-measures.md)です。  
  
## <a name="see-also"></a>参照  
 [MDX データ定義ステートメント&#40;MDX&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
