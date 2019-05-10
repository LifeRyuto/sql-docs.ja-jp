---
title: 名前付きセットの定義 |Microsoft Docs
ms.date: 05/06/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5f6d9ebe43d45ce16ca4889d08656029cad22dcf
ms.sourcegitcommit: 54c8420b62269f6a9e648378b15127b5b5f979c1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65404034"
---
# <a name="lesson-6-2---defining-named-sets"></a>レッスン 6-2 - 名前付きセットを定義します。
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]

名前付きセットとは、ディメンション メンバーのセットを返す多次元式 (MDX) です。 名前付きセットを定義し、キューブ定義の一部として保存できます。さらに、名前付きセットをクライアント アプリケーションで作成することもできます。 名前付きセットは、キューブ データ、算術演算子、数値、関数を組み合わせることによって作成します。 名前付きセットは、クライアント アプリケーションの MDX クエリの中で使用できます。また、サブキューブのセットを定義するときも使用できます。 サブキューブは、クロス結合によるセットのコレクションであり、後続のステートメントに対して、キューブ空間を定義されたサブスペースに制限します。 制限されたキューブ領域の定義は MDX スクリプティングの基本概念です。  
  
名前付きセットを使用すると、MDX クエリを単純化することができ、よく使用する複雑なセット式に対して便利な別名を使用できます。 たとえば、従業員が最も多い Reseller ディメンションのメンバーを含む Large Resellers 名前付きセットを定義できます。 エンド ユーザーはクエリの中でこの Large Resellers 名前付きセットを使用できます。また、サブキューブ内のセットを定義するために名前付きセットを使用することもできます。 名前付きセットの定義はキューブに格納されますが、その値はメモリにしか存在しません。 名前付きセットを作成するには、キューブ デザイナーの **[計算]** タブで **[新しい名前付きセット]** コマンドを使用します。 詳細については、「 [計算](../multidimensional-models-olap-logical-cube-objects/calculations.md)」、「 [名前付きセットの作成](../multidimensional-models/create-named-sets.md)」を参照してください。  
  
このトピックの作業では、Core Products と Large Resellers という 2 つの名前付きセットを定義します。  
  
## <a name="defining-a-core-products-named-set"></a>Core Products 名前付きセットの定義  
  
1.  **Tutorial キューブのキューブ デザイナーを開いて、** [計算] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] タブに切り替えます。次に、ツール バーの **[フォーム ビュー]** をクリックします。  
  
2.  **[スクリプト オーガナイザー]** ペインの **[Total Sales Ratio to All Products]** をクリックして、 **[計算]** タブのツール バーの **[新しい名前付きセット]** をクリックします。  
  
    **[計算]** タブで新しい計算を定義する場合、計算は **[スクリプト オーガナイザー]** ペインに表示されている順序で解決されることに注意してください。 新しい計算を作成するときにペイン内でフォーカスが置かれている位置によって、計算の実行順序が決まります。新しい計算は、フォーカスが置かれている計算の直後に定義されます。  
  
3.  **[名前]** ボックスに、新しい名前付きセットの名前として「 **[Core Products]**」と入力します。  
  
    **[スクリプト オーガナイザー]** ペインには、スクリプト コマンドまたは計算されるメンバーとは異なる、名前付きセットの固有のアイコンが表示されます。  
  
4.  **[計算ツール]** ペインの **[メタデータ]** タブで、 **[Product]**、 **[Category]**、 **[メンバー]**、 **[All Products]** の順に展開します。  
  
    > [!NOTE]  
    > **[計算ツール]** ペインにメタデータが表示されない場合、ツール バーの **[再接続]** をクリックします。 それでも表示されない場合は、キューブを処理するか、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスを開始する必要があります。  
  
5.  **[Bikes]** を **[式]** ボックスにドラッグします。  
  
    これで、Product ディメンションの Bike カテゴリに属するメンバーのセットを返すセット式を作成できました。  
  
## <a name="defining-a-large-resellers-named-set"></a>Large Resellers 名前付きセットの定義  
  
1.  **[スクリプト オーガナイザー]** ペインの **[Core Products]** を右クリックして、 **[新しい名前付きセット]** をクリックします。  
  
2.  **[名前]** ボックスに、この名前付きセットの名前として「 **[Large Resellers]**」と入力します。  
  
3.  **[式]** ボックスに「 **Exists()**」と入力します。  
  
    Exists 関数を使用して、Number of Employees 属性階層内の従業員数が多数であるメンバーのセットと交差する、Reseller Name 属性階層のメンバーのセットを返すようにします。  
  
4.  **[計算ツール]** ペインの **[メタデータ]** タブで、 **Reseller** ディメンション、 **Reseller Name** 属性階層の順に展開します。  
  
5.  **Reseller Name** レベルを Exists セット式のかっこ内にドラッグします。  
  
    このセットのすべてのメンバーを返すには、Members 関数を使用します。 詳細については、「[Members (Set) (MDX)](../../mdx/members-set-mdx.md)」を参照してください。  
  
6.  セット式の部分に続けて、ピリオドを入力して、Members 関数を追加します。 式は以下のようになります。  
  
    ```  
    Exists([Reseller].[Reseller Name].[Reseller Name].Members)  
    ```  
  
    定義したので、Exists の最初のセット式を設定する、従業員の最大数を含む Reseller ディメンションのメンバーのセットが 2 番目のセットを追加する準備が整いました。  
  
7.  **[計算ツール]** ペインの **[メタデータ]** タブで、Reseller ディメンションの **[Number of Employees]** を展開して、 **[メンバー]**、 **[All Resellers]** の順に展開します。  
  
    この属性階層のメンバーはグループ化されていません。  
  
8.  **Reseller** ディメンションのディメンション デザイナーを開いて、 **[属性]** ペインの **[Number of Employees]** をクリックします。  
  
9. プロパティ ウィンドウで、**DiscretizationMethod** プロパティを **Automatic** に変更して、**DiscretizationBucketCount** プロパティを「**5**」に変更します。 詳細については、[「属性メンバーのグループ化 (分離)](../multidimensional-models/attribute-properties-group-attribute-members.md)」を参照してください。  
  
10. **で、** [ビルド] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]メニューの **[Analysis Services Tutorial の配置]** をクリックします。  
  
11. 配置が正常に完了したら、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Tutorial キューブのキューブ デザイナーに切り替え、 **[計算]** タブのツール バーで **[再接続]** をクリックします。  
  
12. **[計算ツール]** ペインの **[メタデータ]** タブで、 **Reseller** ディメンションの **[Number of Employees]** を展開して、 **[メンバー]**、 **[All Resellers]** の順に展開します。  
  
    この属性階層のメンバーには、0 から 4 までの番号が付いた 5 つのグループが含まれるようになりました。 グループの番号は、グループ上にポインターを合わせると表示されるヒントで確認できます。 `2 -17`の範囲では、ヒントに `[Reseller].[Number of Employees].&[0]`が含まれている必要があります。  
  
    この属性階層のメンバーがこのようにグループ化されるのは、DiscretizationBucketCount プロパティが **5** に設定され、DiscretizationMethod プロパティが **Automatic**に設定されているためです。  
  
13. **[式]** ボックスで、Exists セット式内の Members 関数の後ろ、右かっこの直前にコンマを追加します。次に、 **[メタデータ]** ペインから **[83 - 100]** をドラッグしてコンマの後に置きます。  
  
    これで、Exists セット式は完成です。この式は、Large Resellers 名前付きセットが軸に設定された場合に、これらの指定された 2 つのセット、つまり全再販業者のセットと 83 から 100 人の従業員を持つ再販業者のセットで交差するメンバーのセットを返します。  
  
    次の図は、 **Large Resellers** 名前付きセットの **計算式** ペインを示しています。  
  
    ![[Large Resellers] の計算式ペイン](../media/l6-named-set-02.gif "[Large Resellers] の計算式ペイン")  
  
14. **[計算]** タブのツール バーで **[スクリプト ビュー]** をクリックし、計算スクリプトに追加した 2 つの名前付きセットを確認します。  
  
15. 計算スクリプトの最初の CREATE SET コマンドの直前に新しい行を追加して、その行に以下のテキストを独自の行として追加します。  
  
    ```  
    /* named sets */  
    ```  
  
    これで 2 つの名前付きセットが定義され、それらは **[スクリプト オーガナイザー]** ペインに表示されます。 これらの名前付きセットを配置して、これらのメジャーを [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Tutorial キューブで表示する準備が整いました。  
  
## <a name="browsing-the-cube-by-using-the-new-named-sets"></a>新しい名前付きセットを使用したキューブの表示  
  
1.  **で、** [ビルド] [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]メニューの **[Analysis Services Tutorial の配置]** をクリックします。  
  
2.  配置が正常に完了したら、 **[ブラウザー]** タブをクリックして、 **[再接続]** をクリックします。  
  
3.  データ ペインのグリッドをクリアします。  
  
4.  **Reseller Sales-Sales Amount** メジャーをデータ領域に追加します。  
  
5.  次の図のように、Product ディメンションを展開し、Category と Subcategory を行領域に追加します。  
  
    ![Subcategory 属性のメンバー](../media/l6-named-set-03.gif "Subcategory 属性のメンバー")  
  
6.  **[メタデータ]** ペインの **Product** ディメンションで、 **Core Products** をフィルター領域にドラッグします。  
  
    キューブで表示されるのは **Category** 属性の **Bike** メンバーと、 **Bike** サブカテゴリのメンバーだけになります。 これは、サブキューブを定義するために **Core Products** 名前付きセットが使用されているためです。 次の図のように、このサブキューブは、サブキューブ内の **Product** ディメンション内の **Category** 属性のメンバーを、 **Core Product** 名前付きセットのメンバーに限定します。  
  
    ![名前付きセットのメンバーはコア製品](../media/l6-named-set-04.gif "コア製品のメンバーの名前付きセット")  
  
7.  **[メタデータ]** ペインで **Reseller**を展開し、フィルター領域に **Large Resellers** を追加します。  
  
    データ ペインの Reseller Sales Amount メジャーには、自転車の大規模な再販業者の売上高だけが表示されるようになります。 また、次の図のように、フィルター ペインには、この特定のサブキューブを定義するために使用される 2 つの名前付きセットが表示されています。  
  
    ![フィルター ペインの 2 つの名前を格納している設定](../media/l6-named-set-05.gif "という名前の 2 つを含むフィルター ウィンドウの設定")  
  
## <a name="next-lesson"></a>次のレッスン  
[レッスン 7: 主要業績評価指標を定義する&#40;Kpi&#41;](lesson-7-defining-key-performance-indicators-kpis.md)  
  
## <a name="see-also"></a>参照  
[[新しい名前付きセット]](../multidimensional-models-olap-logical-cube-objects/calculations.md)  
[名前付きセットの作成](../multidimensional-models/create-named-sets.md)  
  
  
  
