---
title: キューブの表示 |Microsoft Docs
ms.date: 05/06/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: da01dbb0f8e67d885382a3fa125a0fb37596d553
ms.sourcegitcommit: 54c8420b62269f6a9e648378b15127b5b5f979c1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65403974"
---
# <a name="lesson-2-6---browsing-the-cube"></a>レッスン 2-6-キューブの表示
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]

キューブを配置すると、キューブ デザイナーの **[ブラウザー]** タブにキューブ データが表示され、ディメンション デザイナーの **[ブラウザー]** タブにディメンション データが表示されます。 キューブ データとディメンション データを参照すると、作業を段階的に確認できます。 プロパティ、リレーションシップ、およびその他のオブジェクトに対する細かい変更が、それらのオブジェクトの処理後に期待どおりの効果をもたらしていることを検証できます。 [ブラウザー] タブはキューブ データとディメンション データの両方を表示するために使用されますが、参照するオブジェクトに応じて異なる機能を提供します。  
  
ディメンションの場合は、メンバーを表示したり、階層内をリーフ ノードまで移動したりすることができます。 モデルに翻訳を追加すると、ディメンション データを別の言語で参照できます。  
  
キューブの場合は、データを探索するための 2 つの方法が [ブラウザー] タブに用意されています。 組み込みの MDX クエリ デザイナーを使用して、多次元データベースからフラット化行セットを返すクエリを作成できます。 または、Excel のショートカットを使用してもかまいません。 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]内から Excel を起動する場合、既にピボットテーブルがあるワークシートと、モデル ワークスペース データベースへの定義済みの接続が含まれている状態で Excel が開かれます。  
  
横軸と縦軸を使用して対話的にキューブ データを探索し、データのリレーションシップを分析できるため、通常は Excel での参照の方が便利です。 一方、MDX クエリ デザイナーは、1 つの軸に制限されます。 また、行セットがフラット化されるため、Excel のピボットテーブルでは可能なドリルダウンができません。 この後のレッスンで行うように、キューブにディメンションや階層を追加する場合は、データを参照するためのソリューションとしては Excel の方が適しています。  
  
### <a name="to-browse-the-deployed-cube"></a>配置したキューブを表示するには  
  
1.  **で、Product ディメンションの** ディメンション デザイナー [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]に切り替えます。 これを行うには、ソリューション エクスプローラーの **[ディメンション]** ノードで **[Product]** ディメンションをダブルクリックします。  
  
2.  **[ブラウザー]** タブをクリックして、 **Product Key** 属性階層の **All** メンバーを表示します。 レッスン 3 では、Product ディメンションのユーザー階層を定義し、ディメンションを参照できるようにします。  
  
3.  **で** キューブ デザイナー [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]に切り替えます。 これを行うには、ソリューション エクスプローラーの **[キューブ]** ノードで **[Analysis Services Tutorial]** キューブをダブルクリックします。  
  
4.  **[ブラウザー]** タブをクリックし、キューブ デザイナーのツール バーにある **[再接続]** アイコンをクリックします。  
  
    キューブ デザイナーの左側のペインには、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Tutorial キューブのオブジェクトが表示されます。 **[ブラウザー]** タブの右側には、2 つのペインが表示されます。上は **フィルター** ペイン、下は **データ** ペインです。 次のレッスンでは、キューブ ブラウザーを使用して分析を行います。  
  
## <a name="next-lesson"></a>次のレッスン  
[レッスン 3:メジャー、属性および階層の変更](lesson-3-modifying-measures-attributes-and-hierarchies.md)  
  
## <a name="see-also"></a>参照  
[MDX クエリ エディター &#40;Analysis Services - 多次元データ&#41;](http://msdn.microsoft.com/library/777f2c23-1c1c-4b72-9d19-48a4866551f8)  
  
  
  
