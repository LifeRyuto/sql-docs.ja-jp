---
title: データ領域内のデータの並べ替え (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.date: 08/17/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 2fcb9be2-1daa-4c92-ad00-5f63cdf39f70
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 6ad5600def990457834d858b61ba3bad4a241158
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "65570744"
---
# <a name="sort-data-in-a-data-region-report-builder-and-ssrs"></a>データ領域内のデータの並べ替え (レポート ビルダーおよび SSRS)
  レポートを初めて実行したときのデータ領域内のデータの並べ替え順序を変更するには、データ領域またはグループに対して並べ替え式を設定する必要があります。 既定で、グループの並べ替え式は、グループ式と同じ値に自動的に設定されます。  
  
-   Tablix データ領域では、詳細グループも含め、各グループのデータ領域に対して並べ替え式を設定します。 tablix データ領域に詳細グループが 1 つしかない場合は、データ領域または詳細グループでクエリの並べ替え式の効果が同じになるように定義できます。  
  
-   グラフ データ領域では、カテゴリおよび系列グループの並べ替え式を設定して、各グループの並べ替え順序を制御します。 グラフの凡例に表示される色の順序は、カテゴリ グループ内のデータ ポイントに対して設定されている並べ替え式によって決まります。  
  
-   ゲージには範囲を基準とした単一の値が表示されます。そのため、ゲージ データ領域では、データの並べ替えが必要とならないのが一般的です。 ゲージのデータを並べ替える必要がある場合は、最初にグループを定義し、次にグループの並べ替え式を設定します。  
  
 詳細については、「 [データのフィルター、グループ化、および並べ替え (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)」を参照してください。  
  
 tablix データ領域の場合は、対話的な並べ替えボタンを列見出しの上に追加して、ユーザーがグループまたは詳細行の並べ替え順序を変更できるようにすることもできます。 詳細については、「[対話的な並べ替え (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/interactive-sort-report-builder-and-ssrs.md)」を参照してください。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-sort-data-in-a-tablix-data-region"></a>Tablix データ領域内のデータを並べ替えるには  
  
1.  デザイン画面で、行ハンドルを右クリックし、 **[Tablix のプロパティ]** をクリックします。  
  
2.  **[並べ替え]** をクリックします。  
  
3.  各並べ替え式について、次の手順を実行します。  
  
    1.  **[追加]** をクリックします。  
  
    2.  データの並べ替えに使用する式を入力または選択します。  
  
    3.  **[順序]** 列のドロップダウン リストから、各式の並べ替え方向を選択します。 **[昇順で並べ替え]** を選択すると、式が昇順で並べ替えられます。 **[降順で並べ替え]** を選択すると、式が降順で並べ替えられます。  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-sort-values-in-a-group-including-the-details-group-for-a-tablix"></a>Tablix で詳細グループを含むグループ内の値を並べ替えるには  
  
1.  デザイン画面で、Tablix データ領域内をクリックして選択します。 グループ化ペインに、この Tablix データ領域の行グループと列グループが表示されます。  
  
2.  行グループ ペインで、グループ名を右クリックし、 **[グループの編集]** をクリックします。  
  
3.  **[Tablix のグループ]** ダイアログ ボックスで **[並べ替え]** をクリックします。  
  
4.  各並べ替え式について、次の手順を実行します。  
  
    1.  **[追加]** をクリックします。  
  
    2.  データの並べ替えに使用する式を入力または選択します。  
  
    3.  **[順序]** 列のドロップダウン リストから、各式の並べ替え方向を選択します。 **[昇順で並べ替え]** を選択すると、式が昇順で並べ替えられます。 **[降順で並べ替え]** を選択すると、式が降順で並べ替えられます。  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-sort-x-axis-labels-in-alphabetical-order-on-a-chart"></a>グラフで X 軸ラベルをアルファベット順に並べ替えるには  
  
1.  [カテゴリ フィールド] ドロップ ゾーンでフィールドを右クリックして、 **[カテゴリ グループのプロパティ]** をクリックします。  
  
2.  **[カテゴリ グループのプロパティ]** ダイアログ ボックスの **[並べ替え]** をクリックします。  
  
3.  各並べ替え式について、次の手順を実行します。  
  
    1.  **[追加]** をクリックします。  
  
    2.  グループ化フィールドと一致する式を選択します。 **[グループ化]** をクリックすると、グループ化フィールドの式を確認できます。  
  
    3.  **[順序]** 列のドロップダウン リストから、各式の並べ替え方向を選択します。 **[昇順で並べ替え]** を選択すると、式がアルファベットの昇順で並べ替えられます。 **[降順で並べ替え]** を選択すると、式がアルファベットの降順で並べ替えられます。  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-sort-the-data-points-in-ascending-or-descending-order-on-a-chart"></a>グラフ上のデータ ポイントを昇順または降順で並べ替えるには  
  
1.  [カテゴリ フィールド] ドロップ ゾーンでフィールドを右クリックして、 **[カテゴリ グループのプロパティ]** をクリックします。  
  
2.  **[カテゴリ グループのプロパティ]** ダイアログ ボックスの **[並べ替え]** をクリックします。  
  
3.  各並べ替え式について、次の手順を実行します。  
  
    1.  **[追加]** をクリックします。  
  
    2.  データ フィールドと一致する式を選択します。 ほとんどの場合、これは、 `=Sum(Fields!Quantity.Value)`などの集計値です。  
  
    3.  **[順序]** 列のドロップダウン リストから、各式の並べ替え方向を選択します。 **[昇順で並べ替え]** を選択すると、式が昇順で並べ替えられます。 **[降順で並べ替え]** を選択すると、式が降順で並べ替えられます。  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-sort-data-in-ascending-or-descending-order-for-display-on-a-gauge"></a>ゲージ上に表示するデータを昇順または降順で並べ替えるには  
  
1.  ゲージを右クリックして、 **[データ グループの追加]** をクリックします。  
  
2.  **[ゲージ パネル グループのプロパティ]** ダイアログ ボックスで、必要に応じて **[全般]** をクリックします。  
  
3.  **[グループ式]** の **[追加]** をクリックします。  
  
4.  **[グループ化の条件]** で、データのグループ化に使用する式を入力または選択します。  
  
5.  手順 3. と 4. を繰り返して、使用するグループ式をすべて追加します。  
  
6.  **[並べ替え]** をクリックします。  
  
7.  各並べ替え式について、次の手順を実行します。  
  
    1.  **[追加]** をクリックします。  
  
    2.  グループ化フィールドと一致する式を選択します。 **[グループ化]** をクリックすると、グループ化フィールドの式を確認できます。  
  
    3.  **[順序]** 列のドロップダウン リストから、各式の並べ替え方向を選択します。 **[昇順で並べ替え]** を選択すると、式が昇順で並べ替えられます。 **[降順で並べ替え]** を選択すると、式が降順で並べ替えられます。  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 ゲージ内のデータをグループ化する方法の詳細については、「[ゲージ &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/gauges-report-builder-and-ssrs.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [グラフ &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
 [グラフの軸ラベルの書式設定 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)   
 [複数の図形グラフでの色の統一 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/specify-consistent-colors-across-multiple-shape-charts-report-builder-and-ssrs.md)  
  
  
