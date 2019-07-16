---
title: パースペクティブで Analysis Services 多次元モデル |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ae14c0e76564ebcaffecb7591d14c283fffd2906
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68208563"
---
# <a name="perspectives-in-multidimensional-models"></a>多次元モデルのパースペクティブ
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  パースペクティブは、特定のアプリケーションまたはユーザーのグループに対して作成されるキューブのサブセットです。 キューブ自体は既定のパースペクティブになります。 パースペクティブは、キューブとしてクライアントに表示されます。 ユーザーがパースペクティブを表示すると、キューブと同じように表示されます。 パースペクティブで書き戻しによりキューブ データに行われる変更は、元のキューブに対して行われます。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のビューの詳細については、「 [パースペクティブ](../../analysis-services/multidimensional-models-olap-logical-cube-objects/perspectives.md)」を参照してください。  
  
 キューブのパースペクティブを作成または変更するには、キューブ デザイナーの **[パースペクティブ]** タブを使用します。 **[パースペクティブ]** タブの最初の列は **[キューブ オブジェクト]** 列で、この列にはキューブ内のオブジェクトがすべて一覧表示されます。 これは、キューブ自体である、キューブの既定のパースペクティブに対応しています。  
  
## <a name="creating-or-deleting-perspectives"></a>パースペクティブの作成または削除  
 パースペクティブを **[パースペクティブ]** タブに追加するには、 **[キューブ]** メニューの **[新しいパースペクティブ]** をクリックします。 ツール バーの **[新しいパースペクティブ]** ボタンをクリックするか、ペイン内を右クリックしてショートカット メニューの **[新しいパースペクティブ]** をクリックすることもできます。 キューブに追加できるパースペクティブの数に制限はありません。  
  
 パースペクティブを削除するには、削除するパースペクティブの列内の任意のセルをクリックします。 次に、 **[キューブ]** メニューで、 **[パースペクティブの削除]** をクリックします。 ツール バーの **[パースペクティブの削除]** ボタンをクリックするか、削除するパースペクティブ内の任意のセルを右クリックし、ショートカット メニューの **[パースペクティブの削除]** をクリックすることもできます。  
  
## <a name="renaming-perspectives"></a>パースペクティブ名の変更  
 各パースペクティブの最初の行には、パースペクティブの名前が表示されます。 パースペクティブを作成したときの初期の名前は「パースペクティブ」になります (「パースペクティブ」という名前が既に存在する場合は、1 から始まる序数が名前の後に付けられます)。 この名前をクリックすると、名前を編集できます。  
  
## <a name="hiding-objects-from-a-perspective"></a>パースペクティブのオブジェクトの非表示  
 パースペクティブのオブジェクトを非表示にするには、パースペクティブの列にあるオブジェクトに対応する行のチェック ボックスをオフにします。 パースペクティブで非表示にできるキューブ オブジェクトは次のとおりです。  
  
-   メジャー グループ  
  
-   メジャー  
  
-   ディメンション  
  
-   階層  
  
-   名前付きセット  
  
-   KPI  
  
-   Actions  
  
-   計算されるメンバー  
  
 オブジェクトを表示するには、 **[キューブ オブジェクト]** の下にあるオブジェクトの種類のカテゴリ ( **[メジャー グループ]** 、 **[ディメンション]** 、 **[KPI]** 、 **[計算]** 、または **[アクション]** ) を展開します。 ディメンション内の階層または属性を表示するには、まず、ディメンションを展開してから、 **[階層]** または **[属性]** 行を展開します。 メジャー グループ内のメジャーを表示するには、メジャー グループを展開します。  
  
## <a name="see-also"></a>関連項目  
 [多次元モデルのキューブ](../../analysis-services/multidimensional-models/cubes-in-multidimensional-models.md)  
  
  
