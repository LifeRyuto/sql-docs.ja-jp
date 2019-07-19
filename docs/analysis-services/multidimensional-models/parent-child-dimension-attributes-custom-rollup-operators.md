---
title: 親子ディメンションのカスタム ロールアップ演算子 |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 000d6355aee1fc38aa4fdcb97cf02df2a4ef09da
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68165428"
---
# <a name="parent-child-dimension-attributes---custom-rollup-operators"></a>親子ディメンションの属性 - カスタム ロールアップ演算子
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  カスタム ロールアップ演算子を使用すると、親子階層でメンバーの値を親の値にロール アップする方法を簡単に制御できます。 親子リレーションシップを含んでいるディメンションでは、親属性のすべての計算されないメンバーのロールアップを指定する単項演算子を含んでいる列を指定します。 単項演算子は、親メンバーの値が評価されるたびにメンバーに適用されます。  
  
 単項演算子は、親属性の **UnaryOperatorColumn** プロパティで定義した列に保存され、属性の各メンバーに適用されます。 このプロパティで指定する列は、ディメンション テーブルに存在するか、ディメンション テーブル内の外部キーによってそのディメンション テーブルに関連付けられているテーブルに存在する可能性があります。  
  
 カスタム ロールアップ演算子の機能は、カスタム メンバー式に似ていますが、それよりも簡単です。 カスタム メンバー式では、多次元式 (MDX) を使用して、メンバーのロール アップ方法を決定します。 これに対し、カスタム ロールアップ演算子では、単純な単項演算子を使用して、メンバーの値が親に与える影響を決定します。 ディメンション内の前のレベルのカスタム メンバー式は、レベルのカスタム ロールアップ演算子をオーバーライドします。  
  
## <a name="custom-rollup-precedence"></a>カスタム ロールアップの優先順位  
 優先順位の面では、階層内のレベルのソース属性のカスタム ロールアップ演算子は、前のレベルのカスタム メンバー式をオーバーライドします。 ただし、前のレベルのカスタムメンバー式は、レベルのカスタム ロールアップ演算子をオーバーライドします。  
  
## <a name="see-also"></a>関連項目  
 [カスタム メンバー式の定義](../../analysis-services/multidimensional-models/attribute-properties-define-custom-member-formulas.md)   
 [親子ディメンションの単項演算子](../../analysis-services/multidimensional-models/parent-child-dimension-attributes-unary-operators.md)  
  
  
