---
title: 配置されたキューブの表示 |Microsoft Docs
ms.date: 05/06/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 979a84b026b6d5399133ef9709e6908fdecb4aca
ms.sourcegitcommit: 54c8420b62269f6a9e648378b15127b5b5f979c1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65403714"
---
# <a name="lesson-3-5---browsing-the-deployed-cube"></a>レッスン 3-5-展開済みのキューブの表示
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]

この実習では、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Tutorial キューブを表示します。 分析で複数のディメンションにわたってメジャーを比較するため、データの参照には Excel のピボットテーブルを使用します。 ピボットテーブルを使用すると、顧客、日付、および製品情報を異なる軸に配置して、特定の期間、顧客の人口統計、および製品ラインにわたって見たときに、Internet Sales がどのように変化するかを確認できます。  
  
### <a name="to-browse-the-deployed-cube"></a>配置したキューブを表示するには  
  
1.  [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]のキューブ デザイナーに切り替えるには、ソリューション エクスプローラーの **[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] [キューブ]** フォルダーで **Tutorial** キューブをダブルクリックします。  
  
2.  **[ブラウザー]** タブを開き、キューブ デザイナーのツール バーにある **[再接続]** ボタンをクリックします。  
  
3.  Excel アイコンをクリックして Excel を起動し、データ ソースとしてワークスペース データベースを使用します。 接続を有効にするように求めるメッセージが表示されたら、 **[有効]** をクリックします。  
  
4.  ピボットテーブル フィールド リストで **[Internet Sales]** を展開し、 **Sales Amount** メジャーを **[値]** 領域にドラッグします。  
  
5.  ピボットテーブル フィールド リストで **Product**を展開します。  
  
6.  **Product Model Lines** ユーザー階層を **[列]** 領域にドラッグします。  
  
7.  ピボットテーブル フィールド リストで **[Customer]** を展開し、 **[Location]** を展開します。次に、Customer ディメンション内の [Location] 表示フォルダーにある **[Customer Geography]** 階層を **[行]** 領域にドラッグします。  
  
8.  ピボットテーブル フィールド リストで **[Order Date]** を展開し、 **[Order Date.Calendar Date]** 階層を **[レポート フィルター]** 領域にドラッグします。  
  
9. データ ペインで、 **Order Date.Calendar Date** フィルターの右側にある矢印をクリックし、 **[(すべて)]** レベルのチェック ボックスをオフにします。次に、 **[2006]**、 **[H1 CY 2006]**、 **[Q1 CY 2006]** の順に展開し、 **[February 2006]** チェック ボックスをオンにして、 **[OK]** をクリックします。  
  
    次の図のように、2006 年 2 月におけるインターネットでの売上が、地域別および製品ライン別に表示されます。  
  
    ![地域および製品ラインごとのインターネット販売](../media/l3-cube-browser-finish.gif "地域および製品ラインごとのインターネット販売")  
  
## <a name="next-lesson"></a>次のレッスン  
[レッスン 4:高度な属性およびディメンションのプロパティを定義します。](lesson-4-defining-advanced-attribute-and-dimension-properties.md)  
  
  
  
