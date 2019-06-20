---
title: メジャー グループ内のディメンションの粒度の定義 |Microsoft Docs
ms.date: 05/06/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e6dadcc53120ce112ad3e9044e38bf14a525fded
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "65404084"
---
# <a name="lesson-5-4---defining-dimension-granularity-within-a-measure-group"></a>レッスン 5-4-メジャー グループ内のディメンションの粒度の定義
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]

ファクト データは、利用目的ごとに異なる粒度でディメンションを作成しなければならない場合があります。 たとえば、販売店やインターネットでの売上データを日ごとに記録する一方で、販売量は月ごとまたは四半期ごとに記録することが考えられます。 このようなシナリオでは、ファクト テーブルごとに異なる詳細度を、時間のディメンションに設定します。 新しいデータベース ディメンションを定義する場合、このようにさまざまに異なる詳細度を設定して時間のディメンションを定義することもできますが、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]を使用すると、さらに容易にディメンションを定義できます。  
  
メジャー グループでディメンションを使用する場合、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]の既定では、ディメンションのキー属性に基づいてディメンションの詳細度が決定されます。 たとえば、あるメジャー グループに時間のディメンションが存在し、その時間ディメンションの既定の詳細度が日単位である場合は、メジャー グループ内のそのディメンションの既定の詳細度が日単位になります。 このチュートリアルで使用する **Internet Sales** (インターネット売上) や **Reseller Sales** (販売店売上) メジャー グループなどのように、既定の詳細度が適切である場合は数多くあります。 しかし、販売量や予算などのメジャー グループに存在するディメンションには、月単位、または四半期単位の詳細度がより適切です。  
  
キューブ ディメンションに既定値以外の詳細度を指定するには、具体的なメジャー グループ内で使用するキューブ ディメンションの "粒度" 属性を変更します。この操作は、キューブ デザイナーの **[ディメンションの使用法]** タブで行います。 指定のメジャー グループのディメンションの詳細度を、そのディメンションのキー属性以外の属性に変更する場合は、メジャー グループ内の他のすべての属性を、新しい "粒度" 属性に関連付ける必要があります (間接的な関連付けも有効です)。 関連付けを行うには、"粒度" 属性として指定した属性と、その他のすべての属性との間に、属性リレーションシップを指定します。 この場合、属性リレーションシップを移動するのではなく、追加の属性リレーションシップを定義します。 "粒度" 属性として指定した属性は、メジャー グループ内のディメンションの残りの属性のキー属性になります。 属性リレーションシップを適切に指定しないと、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は値を正しく集計できません。これについては、このトピックの実習で確認します。  
  
詳細については、「 [ディメンション リレーションシップ](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)」および「 [ファクト リレーションシップとファクト リレーションシップのプロパティの定義](../multidimensional-models/define-a-regular-relationship-and-regular-relationship-properties.md)」を参照してください。  
  
このトピックの実習では、Sales Quotas メジャー グループを追加し、このメジャー グループの Date ディメンションの粒度を月単位 (Month) に設定します。 次に、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] が値を適切に集計できるよう、Month 属性とその他の属性との間に属性リレーションシップを定義します。  
  
## <a name="adding-tables-and-defining-the-sales-quotas-measure-group"></a>テーブルの追加と Sales Quotas メジャー グループの定義  
  
1.  **Adventure Works DW 2012** データ ソース ビューに切り替えます。  
  
2.  **[ダイアグラム オーガナイザー]** ペイン内を右クリックし、 **[新しいダイアグラム]** をクリックして、ダイアグラムの名前として「 **Sales Quotas**」と入力します。  
  
3.  **[テーブル]** ペインの **Employee**、 **Sales Territory** 、および **Date** テーブルを、 **[ダイアグラム]** ペインにドラッグします。  
  
4.  **[ダイアグラム]** ペイン内を右クリックし、 **[テーブルの追加と削除]** をクリックして、 **FactSalesQuota** テーブルを **[ダイアグラム]** ペインに追加します。  
  
    **Employee** テーブルを介して、 **SalesTerritory** テーブルが **FactSalesQuota** テーブルに関連付けられます。  
  
5.  **FactSalesQuota** テーブルの列を確認し、このテーブル内のデータを調べます。  
  
    このテーブルのデータの詳細度が四半期単位になっていることがわかります。FactSalesQuota の最も低い詳細レベルが四半期単位ということになります。  
  
6.  データ ソース ビュー デザイナーで、 **FactSalesQuota** テーブルの **FriendlyName** プロパティを「 **SalesQuotas**」に変更します。  
  
7.  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Tutorial キューブに切り替え、 **[キューブ構造]** タブをクリックします。  
  
8.  **[メジャー]** ペイン内を右クリックし、 **[新しいメジャー グループ]** をクリックします。次に、 **[新しいメジャー グループ]** ダイアログ ボックスで **[SalesQuotas]** をクリックし、 **[OK]** をクリックします。  
  
    **[メジャー]** ペインに **Sales Quotas** メジャー グループが表示されます。 **[ディメンション]** ペインを見ると、 **Date** データベース ディメンションに基づく新しい **Date** キューブ ディメンションが定義されていることがわかります。 新しい時間キューブ ディメンションが定義されてしまうのは、Sales Quotas メジャー グループの基となる [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] FactSalesQuota **ファクト テーブルの** DateKey **列に関連付けられている時間キューブ ディメンションがどのディメンションなのかを、** に指定していないためです。 時間キューブ ディメンションの設定は、このトピックの別の実習で変更します。  
  
9. **Sales Quotas** メジャー グループを展開します。  
  
10. **[メジャー]** ペインで、 **Sales Amount Quota**をクリックします。次に、[プロパティ] ウィンドウで、 **FormatString** プロパティの値を **Currency** に設定します。  
  
11. **[Sales Quotas Count]** メジャーを選択します。次に、[プロパティ] ウィンドウで、 **FormatString** プロパティの値として「 **#,#** 」と入力します。  
  
12. **Sales Quotas** メジャー グループから **Calendar Quarter** メジャーを削除します。  
  
    [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によって、Calendar Quarter メジャーの基となる列 (この列には他のメジャーも含まれている) が自動的に検出されました。 しかし、このトピックの後の操作で Sales Quotas メジャー グループを Date ディメンションにリンクさせるときは、検出された列および CalendarYear 列の値を手動で割り当てます。  
  
13. **[メジャー]** ペインで **Sales Quotas** メジャー グループを右クリックし、 **[新しいメジャー]** をクリックします。  
  
    **[新しいメジャー]** ダイアログ ボックスが開き、メジャーの使用法が **[合計]** である場合に選択できる列が表示されます。  
  
14. **[新しいメジャー]** ダイアログ ボックスで、 **[使用法]** ボックスの一覧から **[個別のカウント]** をクリックします。 **[基になるテーブル]** ボックスの一覧で **SalesQuotas** が選択されていることを確認します。 **[基になる列]** ボックスの一覧で **EmployeeKey** をクリックし、 **[OK]** をクリックします。  
  
    **Sales Quotas 1**という名前の新しいメジャー グループに、メジャーが作成されます。 処理速度を最大限に向上させるため、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の "個別のカウント" メジャーは専用のメジャー グループに作成されます。  
  
15. **Employee Key Distinct Count** メジャーの **Name** プロパティの値を **Sales Person Count**に変更します。次に、 **FormatString** プロパティの値として「 **#,#** 」と入力します。  
  
## <a name="browsing-the-measures-in-the-sales-quota-measure-group-by-date"></a>Sales Quota メジャー グループのメジャーの日付順での表示  
  
1.  **[ビルド]** メニューの **[Analysis Services Tutorial の配置]** をクリックします。  
  
2.  配置が正常に完了したら、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Tutorial キューブのキューブ デザイナーで **[ブラウザー]** タブをクリックし、 **[再接続]** ボタンをクリックします。  
  
3.  Excel ショートカットをクリックし、 **[有効化]** をクリックします。  
  
4.  ピボットテーブル フィールド リストで **[Sales Quotas]** メジャー グループを展開し、 **Sales Amount Quota** メジャーを値領域にドラッグします。  
  
5.  **Sales Territory** ディメンションを展開し、 **Sales Territories** ユーザー定義階層を行ラベルにドラッグします。  
  
    次の図に示すように、Sales Territory キューブ ディメンションは、直接的にも間接的にも Fact Sales Quota テーブルには関連付けられていません。  
  
    ![Sales Territory キューブ ディメンション](../media/l5-granularity-2.gif "Sales Territory キューブ ディメンション")  
  
    このトピックの次の一連の手順では、Sales Territory キューブ ディメンションと Fact Sales Quota テーブルの間に参照ディメンションのリレーションシップを定義します。  
  
6.  **Sales Territories** ユーザー階層を行ラベル領域から列ラベル領域に移動します。  
  
7.  ピボットテーブル フィールド リストで **Sales Territories** ユーザー定義階層を選択し、右側の下矢印をクリックします。  
  
    ![フィールド リスト内の sales Territories 階層](../media/l5-granularity-1a.png "フィールド リスト内の Sales Territories 階層")  
  
8.  フィルターで [すべて選択] チェック ボックスをクリックしてすべての選択を解除してから、 **North America**だけを選択します。  
  
    ![North America を選択するためのフィルター ペイン](../media/l5-granularity-1b.png "North America を選択するためのフィルター ペイン")  
  
9. ピボットテーブル フィールド リストで **Date**を展開します。  
  
10. **Date.Fiscal Date** ユーザー階層を行ラベルにドラッグします。  
  
11. ピボットテーブルで、行ラベルの横にある下矢印をクリックします。 **FY 2008**以外のすべての年をオフにします。  
  
    **Month** レベルの **July, 2007** 、 **August, 2007**、 **September, 2007**メンバーの代わりに、 **Month** レベルの **July 2007** メンバーのみが表示されます。また、 **Date** レベルでは、31 日全部のメンバーではなく **July 1, 2007** メンバーのみが表示されます。 このように表示されるのは、ファクト テーブルの詳細度が四半期単位であり、 **Date** ディメンションの詳細レベルが日単位であるためです。 この変更は、このトピックの別の実習で行います。  
  
    また、月単位および日単位の **Sales Amount Quota** の値が四半期のそれと同じである $13,733,000.00 になっています。 これは、Sales Quotas メジャー グループのデータの最低詳細レベルが四半期単位になっているためです。 この変更は、レッスン 6 で行います。  
  
    次の図は、 **Sales Amount Quota**の値を示しています。  
  
    ![売上の値は Amount Quota](../media/l5-granularity-3.png "Amount Quota の売上の値")  
  
## <a name="defining-dimension-usage-properties-for-the-sales-quotas-measure-group"></a>Sales Quotas メジャー グループにおけるディメンションの使用法の定義  
  
1.  **Employee** ディメンションのディメンション デザイナーを開き、 **[データ ソース ビュー]** ペインで **[SalesTerritoryKey]** を右クリックし、 **[列から新しい属性を作成]** をクリックします。  
  
2.  **[属性]** ペインで、 **[SalesTerritoryKey]** をクリックします。次に、[プロパティ] ウィンドウで **AttributeHierarchyVisible** プロパティを **False** に設定します。さらに、 **AttributeHierarchyOptimizedState** プロパティを **NotOptimized**に設定し、 **AttributeHierarchyOrdered** プロパティを **False**に設定します。  
  
    この属性は、 **Sales Territory** ディメンションを参照元ディメンションとして **Sales Quotas** および **Sales Quotas 1** メジャー グループにリンクさせる際に使用します。  
  
3.  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Tutorial キューブのキューブ デザイナーで、 **[ディメンションの使用法]** タブをクリックします。次に、 **Sales Quotas** および **Sales Quotas 1** メジャー グループでのディメンションの使用法を確認します。  
  
    **Employee** および **Date** キューブ ディメンションは、通常のリレーションシップを介して **Sales Quotas** および Sales Quotas 1 メジャー グループにリンクしています。 また、 **Sales Territory** キューブ ディメンションはどちらのメジャー グループにもリンクしていません。  
  
4.  交差する位置のセルをクリックして、 **Sales Territory**ディメンションと**Sales Quotas**メジャー グループと、参照ボタンをクリックして ( **.** ). **[リレーションシップの定義]** ダイアログ ボックスが開きます。  
  
5.  **[リレーションシップの種類の選択]** ボックスの一覧から **[参照対象]** をクリックします。  
  
6.  **[中間ディメンション]** ボックスの一覧から **[Employee]** を選択します。  
  
7.  **[参照ディメンションの属性]** ボックスの一覧から **[Sales Territory Region]** を選択します。  
  
8.  **[中間ディメンションの属性]** ボックスの一覧から **[Sales Territory Key]** を選択します (Sales Territory Region 属性のキー列は、SalesTerritoryKey 列です)。  
  
9. **[具体化する]** チェック ボックスがオンになっていることを確認します。  
  
10. **[OK]** をクリックします。  
  
11. 交差する位置のセルをクリックして、 **Sales Territory**ディメンションと**Sales Quotas 1**メジャー グループと、参照ボタンをクリックして ( **.** ). **[リレーションシップの定義]** ダイアログ ボックスが開きます。  
  
12. **[リレーションシップの種類の選択]** ボックスの一覧から **[参照対象]** をクリックします。  
  
13. **[中間ディメンション]** ボックスの一覧から **[Employee]** を選択します。  
  
14. **[参照ディメンションの属性]** ボックスの一覧から **[Sales Territory Region]** を選択します。  
  
15. **[中間ディメンションの属性]** ボックスの一覧から **[Sales Territory Key]** を選択します (Sales Territory Region 属性のキー列は、SalesTerritoryKey 列です)。  
  
16. **[具体化する]** チェック ボックスがオンになっていることを確認します。  
  
17. **[OK]** をクリックします。  
  
18. **Date** キューブ ディメンションを削除します。  
  
    時間に関連する 4 つのキューブ ディメンションを用意する代わりに、 **Sales Quotas** メジャー グループの **Order Date** キューブ ディメンションを使用します。これが、販売量に対応する日付のディメンションになります。 また、このキューブ ディメンションはキューブ内のプライマリ日付ディメンションにもなります。  
  
19. **[ディメンション]** の一覧で、 **Order Date** キューブ ディメンションの名前を **Date**に変更します。  
  
    **Order Date** キューブ ディメンションの名前を **Date** に変更することにより、同キューブ ディメンションがこのキューブのプライマリ日付ディメンションとしての機能を持っていることを把握しやすくなります。  
  
20. [参照] ボタンをクリックします ( **.** ) の交差部分にあるセルで、 **Sales Quotas**メジャー グループと**日付**ディメンション。  
  
21. **[リレーションシップの定義]** ダイアログ ボックスで、 **[リレーションシップの種類の選択]** ボックスの一覧から **[標準]** を選択します。  
  
22. **[粒度属性]** ボックスの一覧から **[Calendar Quarter]** を選択します。  
  
    非キー属性を粒度属性として選択したため、警告が表示されます。他のすべての属性をメンバー プロパティとして指定し、直接または間接的に粒度属性に関連付ける必要があります。  
  
23. **[リレーションシップの定義]** ダイアログ ボックスの **[リレーションシップ]** 領域で、Date キューブ ディメンションの基となるテーブルから **CalendarYear** および **CalendarQuarter** ディメンション列を、Sales Quota メジャー グループの基となるテーブルの **CalendarYear** および **CalendarQuarter** 列にそれぞれリンクし、 **[OK]** をクリックします。  
  
    > [!NOTE]  
    > Calendar Quarter が、Sales Quotas メジャー グループの Date キューブ ディメンションの粒度属性として定義されます。しかし、Date 属性は依然として Internet Sales および Reseller Sales メジャー グループの粒度属性です。  
  
24. 前の 4 つの手順を **Sales Quotas 1** メジャー グループに対して繰り返します。  
  
## <a name="defining-attribute-relationships-between-the-calendar-quarter-attribute-and-the-other-dimension-attributes-in-the-date-dimension"></a>Calendar Quarter 属性およびその他の属性間の属性リレーションシップの Date ディメンションへの定義  
  
1.  **Date** ディメンションの **ディメンション デザイナー** に切り替えて、 **[属性リレーションシップ]** タブをクリックします。  
  
    **Calendar Year** は、 **Calendar Semester** 属性を介して **Calendar Quarter** にリンクされました。しかし、会計カレンダーの各属性は互いに一対一でリンクしているだけで、 **Calendar Quarter** 属性にはリンクしていません。したがって、このままでは **Sales Quotas** メジャー グループにおいて正しく集計されません。  
  
2.  ダイアグラムで、 **[Calendar Quarter]** 属性を右クリックし、 **[新しい属性リレーションシップ]** をクリックします。  
  
3.  **[属性リレーションシップの作成]** ダイアログ ボックスで、 **[基になる属性]** に **[Calendar Quarter]** を指定します。 **[関連属性]** を **[Fiscal Quarter]** に設定します。  
  
4.  **[OK]** をクリックします。  
  
    **Date** ディメンションに、1 つまたは複数の重複する属性リレーションシップが含まれており、このことが原因で、非キー属性が粒度属性として使用されている場合にデータの集計ができない可能性があることを警告するメッセージが表示されます。  
  
5.  **Month Name** 属性と **Fiscal Quarter** 属性との間の属性リレーションシップを削除します。  
  
6.  **[ファイル]** メニューの **[すべてを保存]** をクリックします。  
  
## <a name="browsing-the-measures-in-the-sales-quota-measure-group-by-date"></a>Sales Quota メジャー グループのメジャーの日付順での表示  
  
1.  **[ビルド]** メニューの **[Analysis Services Tutorial の配置]** をクリックします。  
  
2.  配置が正常に完了したら、 **Tutorial キューブのキューブ デザイナーで** [ブラウザー] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] タブをクリックし、 **[再接続]** をクリックします。  
  
3.  Excel ショートカットをクリックし、 **[有効化]** をクリックします。  
  
4.  **Sales Amount Quota** メジャーを値領域にドラッグします。  
  
5.  **Sales Territories** ユーザー階層を列ラベルにドラッグし、 **North America**でフィルター処理します。  
  
6.  **Date.FiscalDate** ユーザー階層を行ラベルにドラッグし、ピボットテーブルの **[行ラベル]** の横の下矢印をクリックします。次に、 **[FY 2008]** 以外のすべてのチェック ボックスをオフにして、2008 年度 (会計年度) だけを表示します。  
  
7.  [OK] をクリックします。  
  
8.  **FY 2008**、 **H1 FY 2008**、 **Q1 FY 2008**の順に展開します。  
  
    次の図は、Sales Quotas メジャー グループが適切に多次元化された、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Tutorial キューブのピボットテーブルです。  
  
    会計四半期レベルの各メンバーが、四半期レベルと同じ値になっています。 たとえば、 **Q1 FY 2008** では、 **Q1 FY 2008** の分の $9,180,000.00 が、その各メンバーの値にもなっています。 このように表示されるのは、ファクト テーブルの詳細度が四半期単位であり、同時に Date ディメンションの詳細レベルも四半期単位であるためです。 レッスン 6 では、四半期ごとの販売量を各月に均等に割り振る方法について学習します。  
  
    ![Sales Quota メジャー グループの次元は正しく](../media/l5-granularity-7.gif "正しくの次元は、Sales Quota メジャー グループ")  
  
## <a name="next-lesson"></a>次のレッスン  
[レッスン 6:計算の定義](lesson-6-defining-calculations.md)  
  
## <a name="see-also"></a>関連項目  
[ディメンション リレーションシップ](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)  
[ファクト リレーションシップとファクト リレーションシップのプロパティの定義](../multidimensional-models/define-a-regular-relationship-and-regular-relationship-properties.md)  
[データ ソース ビュー デザイナーでのダイアグラムの操作 &#40;Analysis Services&#41;](../multidimensional-models/work-with-diagrams-in-data-source-view-designer-analysis-services.md)  
  
  
  
