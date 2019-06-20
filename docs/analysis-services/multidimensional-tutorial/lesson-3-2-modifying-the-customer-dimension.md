---
title: Customer ディメンションの変更 |Microsoft Docs
ms.date: 05/06/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bbe4fbfc2cad2df41a1d9bd14fcb2620e2dec5c1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "65403644"
---
# <a name="lesson-3-2---modifying-the-customer-dimension"></a>レッスン 3-2-Customer ディメンションの変更
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]

キューブのディメンションの使いやすさと機能性を向上させる方法は数多くあります。 このトピックの実習では、Customer ディメンションを変更します。  
  
## <a name="renaming-attributes"></a>属性名の変更  
属性名は、ディメンション デザイナーの **[ディメンション構造]** タブで変更できます。  
  
#### <a name="to-rename-an-attribute"></a>属性名を変更するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] で Customer ディメンションの**ディメンション デザイナー**に切り替えます。 これを行うには、ソリューション エクスプローラーの **[ディメンション]** ノードで **[Customer]** ディメンションをダブルクリックします。  
  
2.  **[属性]** ペインで **[English Country Region Name]** を右クリックし、 **[名前の変更]** をクリックします。 この属性の名前を「 **Country-Region**」に変更します。  
  
3.  同様に、次の属性の名前も変更します。  
  
    -   **English Education**属性 - 変更**教育**  
  
    -   **English Occupation**属性 - 変更**職業**  
  
    -   **State Province Name**属性 - 変更**State-province**  
  
4.  **[ファイル]** メニューの **[すべてを保存]** をクリックします。  
  
## <a name="creating-a-hierarchy"></a>階層の作成  
新しい階層は、属性を **[属性]** ペインから **[階層]** ペインにドラッグすることで作成できます。  
  
#### <a name="to-create-a-hierarchy"></a>階層を作成するには  
  
1.  **[属性]** ペインの **[Country-Region]** 属性を **[階層]** ペインにドラッグします。  
  
2.  **[属性]** ペインの **[State-Province]** 属性を、 **[階層]** ペインの **[<new level>]** セル ( **[Country-Region]** レベルの下) にドラッグします。  
  
3.  **[属性]** ペインの **[City]** 属性を、 **[階層]** ペインの **[<new level>]** セル ( **[State-Province]** レベルの下) にドラッグします。  
  
4.  **[ディメンション構造]** タブの **[階層]** ペインで、 **[Hierarchy]** 階層のタイトル バーを右クリックし、 **[名前の変更]** を選択して「**Customer Geography**」と入力します。  
  
    この階層の名前が **Customer Geography**になりました。  
  
5.  **[ファイル]** メニューの **[すべてを保存]** をクリックします。  
  
## <a name="adding-a-named-calculation"></a>名前付き計算の追加  
名前付き計算 (計算列として表される SQL 式) をデータ ソース ビューに追加できます。 この式は、テーブルの列として表示され、動作します。 名前付き計算により、基になるデータ ソースのテーブルを変更せずに、データ ソース ビューの既存のテーブルのリレーショナル スキーマを拡張できます。 詳細については、「[データ ソース ビューでの名前付き計算の定義 (Analysis Services)](../multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md)」を参照してください。  
  
#### <a name="to-add-a-named-calculation"></a>名前付き計算を追加するには  
  
1.  **[!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] DW 2012** データ ソース ビューを開きます。これには、ソリューション エクスプローラーの **[データ ソース ビュー]** フォルダーでこのデータ ソース ビューをダブルクリックします。  
  
2.  左側の **[テーブル]** ペインで **Customer**を右クリックし、 **[新しい名前付き計算]** をクリックします。  
  
3.  **[名前付き計算の作成]** ダイアログ ボックスの **[列名]** ボックスに「 **FullName** 」と入力します。次に、 **[式]** ボックスに次の **CASE** ステートメントを入力するか、またはコピーして貼り付けます。  
  
    ```  
    CASE  
       WHEN MiddleName IS NULL THEN  
       FirstName + ' ' + LastName  
       ELSE  
       FirstName + ' ' + MiddleName + ' ' + LastName  
    END  
    ```  
  
    この **CASE** ステートメントは、 **FirstName**列、 **MiddleName**列、および **LastName** 列を連結して 1 つの列に表示します。この列に表示される名前が **Customer** 属性の表示名となります。  
  
4.  **[OK]** をクリックします。次に、 **[テーブル]** ペインで **Customer** を展開します。  
  
    **FullName** 名前付き計算が Customer テーブルの列の一覧に表示されます。そのアイコンは、FullName が名前付き計算であることを示しています。  
  
5.  **[ファイル]** メニューの **[すべてを保存]** をクリックします。  
  
6.  **[テーブル]** ペインで **[Customer]** を右クリックし、 **[データの探索]** をクリックします。  
  
7.  **[Customer テーブルの探索]** ビューで、最後の列を確認します。  
  
    データ ソース ビューに **[FullName]** 列が表示されています。元のデータ ソースは変更されずに、データ ソースから取得された複数の列のデータが適切に連結されています。  
  
8.  **[Customer テーブルの探索]** タブを閉じます。  
  
## <a name="using-the-named-calculation-for-member-names"></a>メンバー名に対応する名前付き計算の使用  
データ ソース ビューで名前付き計算を作成したら、その名前付き計算を属性のプロパティとして使用できます。  
  
#### <a name="to-use-the-named-calculation-for-member-names"></a>メンバー名に対応する名前付き計算を使用するには  
  
1.  Customer ディメンションのディメンション デザイナーに切り替えます。  
  
2.  **[ディメンション構造]** タブの **[属性]** ペインで、 **[Customer Key]** 属性をクリックします。  
  
3.  [プロパティ] ウィンドウを開いて、タイトル バーにある **[自動的に隠す]** ボタンをクリックします。これにより、[プロパティ] ウィンドウが開いたままになります。  
  
4.  **[Name]** プロパティ フィールドに「 **Full Name**」と入力します。  
  
5.  をクリックして、 **NameColumn**プロパティは、下部にあるフィールドし、クリックし、参照 ( **.** ) ボタンをクリックする、**名前列** ダイアログ ボックス。  
  
6.  **[基になる列]** ボックスの一覧の下部にある **[FullName]** を選択し、 **[OK]** をクリックします。  
  
7.  [ディメンション構造] タブで、 **[属性]** ペインの **[Full Name]** 属性を、 **[階層]** ペインの **[<new level>]** セル ( **[City]** レベルの下) にドラッグします。  
  
8.  **[ファイル]** メニューの **[すべてを保存]** をクリックします。  
  
## <a name="defining-display-folders"></a>表示フォルダーの定義  
表示フォルダーを使用してユーザー階層と属性階層をフォルダー構造内にグループ化することで、使いやすさを向上させることができます。  
  
#### <a name="to-define-display-folders"></a>表示フォルダーを定義するには  
  
1.  Customer ディメンションの **[ディメンション構造]** タブを開きます。  
  
2.  **[属性]** ペインで、Ctrl キーを押しながら次の各属性をクリックして選択します。  
  
    -   **City**  
  
    -   **Country-Region**  
  
    -   **Postal Code**  
  
    -   **State-Province**  
  
3.  [プロパティ] ウィンドウで、上部の **[AttributeHierarchyDisplayFolder]** プロパティ フィールド (ポイントしないと名前全体が表示されない場合があります) をクリックし、「 **Location**」と入力します。  
  
4.  **[階層]** ペインで、 **[Customer Geography]** をクリックします。次に、右側の [プロパティ] ウィンドウで、 **DisplayFolder** プロパティの値として **[Location]** をクリックします。  
  
5.  **[属性]** ペインで、Ctrl キーを押しながら次の各属性をクリックして選択します。  
  
    -   **Commute Distance**  
  
    -   **Education**  
  
    -   **Gender**  
  
    -   **House Owner Flag**  
  
    -   **Marital Status**  
  
    -   **Number Cars Owned**  
  
    -   **Number Children At Home**  
  
    -   **Occupation**  
  
    -   **Total Children**  
  
    -   **Yearly Income**  
  
6.  [プロパティ] ウィンドウで、上部の **[AttributeHierarchyDisplayFolder]** プロパティ フィールドをクリックして「 **Demographic**」と入力します。  
  
7.  **[属性]** ペインで、Ctrl キーを押しながら次の各属性をクリックして選択します。  
  
    -   **Email Address**  
  
    -   **Phone**  
  
8.  [プロパティ] ウィンドウで、 **[AttributeHierarchyDisplayFolder]** プロパティ フィールドをクリックして「 **Contacts**」と入力します。  
  
9. **[ファイル]** メニューの **[すべてを保存]** をクリックします。  
  
## <a name="defining-composite-keycolumns"></a>複合 KeyColumns の定義  
**KeyColumns** プロパティは、属性のキーを表す 1 つ以上の列を示します。 このレッスンでは、 **City** 属性と **State-Province** 属性の複合キーを作成します。 複合キーは、属性を一意に識別する必要がある場合に役立ちます。 たとえば、このチュートリアルで後ほど属性リレーションシップを定義する際に、 **City** 属性は **State-Province** 属性を一意に識別する必要があります。 ただし、異なる州に同じ名前の都市が存在する可能性もあります。 そのため、 **City** 属性に対しては **StateProvinceName** 列と **City** 列で構成される複合キーを作成します。 詳細については、「[属性の KeyColumn プロパティの変更](../multidimensional-models/attribute-properties-modify-the-keycolumn-property.md)」を参照してください。  
  
#### <a name="to-define-composite-keycolumns-for-the-city-attribute"></a>City 属性の複合 KeyColumns を定義するには  
  
1.  Customer ディメンションの **[ディメンション構造]** タブを開きます。  
  
2.  **[属性]** ペインで、 **[City]** 属性をクリックします。  
  
3.  **[プロパティ]** ウィンドウで、下部付近の **[KeyColumns]** フィールドをクリックし、参照ボタン ( **[...]** ) をクリックします。  
  
4.  **[キー列]** ダイアログ ボックスの **[使用できる列]** ボックスの一覧で **[StateProvinceName]** 列を選択し、 **[>]** をクリックします。  
  
    **[City]** 列と **[StateProvinceName]** 列が **[キー列]** ボックスの一覧に表示されるようになりました。  
  
5.  **[OK]** をクリックします。  
  
6.  **City** 属性の **NameColumn** プロパティを設定するには、[プロパティ] ウィンドウで **[NameColumn]** フィールドをクリックし、参照ボタン ( **[...]** ) をクリックします。  
  
7.  **[名前列]** ダイアログ ボックスの **[基になる列]** ボックスの一覧で **[City]** を選択し、 **[OK]** をクリックします。  
  
8.  **[ファイル]** メニューの **[すべてを保存]** をクリックします。  
  
#### <a name="to-define-composite-keycolumns-for-the-state-province-attribute"></a>State-Province 属性の複合 KeyColumns を定義するには  
  
1.  Customer ディメンションの **[ディメンション構造]** タブが開いていることを確認します。  
  
2.  **[属性]** ペインで、 **[State-Province]** 属性をクリックします。  
  
3.  **[プロパティ]** ウィンドウで **[KeyColumns]** フィールドをクリックし、参照ボタン ( **[...]** ) をクリックします。  
  
4.  **[キー列]** ダイアログ ボックスの **[使用できる列]** ボックスの一覧で **[EnglishCountryRegionName]** 列を選択し、 **[>]** をクリックします。  
  
    **[EnglishCountryRegionName]** 列と **[StateProvinceName]** 列が **[キー列]** ボックスの一覧に表示されるようになりました。  
  
5.  **[OK]** をクリックします。  
  
6.  **State-Province** 属性の **NameColumn** プロパティを設定するには、[プロパティ] ウィンドウで **[NameColumn]** フィールドをクリックし、参照ボタン ( **[...]** ) をクリックします。  
  
7.  **[名前列]** ダイアログ ボックスの **[基になる列]** ボックスの一覧で **[StateProvinceName]** を選択し、 **[OK]** をクリックします。  
  
8.  **[ファイル]** メニューの **[すべてを保存]** をクリックします。  
  
## <a name="defining-attribute-relationships"></a>属性リレーションシップの定義  
基になるデータで属性リレーションシップがサポートされる場合、属性間の属性リレーションシップを定義する必要があります。 属性リレーションシップを定義すると、ディメンション、パーティション、およびクエリの処理速度が上がります。 詳細については、「 [属性リレーションシップの定義](../multidimensional-models/attribute-relationships-define.md) 」および「 [属性リレーションシップ](../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)」を参照してください。  
  
#### <a name="to-define-attribute-relationships"></a>属性リレーションシップを定義するには  
  
1.  Customer ディメンションの **ディメンション デザイナー** で、 **[属性リレーションシップ]** タブをクリックします。場合によっては、しばらく待つ必要があります。  
  
2.  ダイアグラムで、 **[City]** 属性を右クリックし、 **[新しい属性リレーションシップ]** をクリックします。  
  
3.  **[属性リレーションシップの作成]** ダイアログ ボックスで、 **[基になる属性]** に **[City]** を指定します。 **[関連属性]** を **[State-Province]** に設定します。  
  
4.  **[リレーションシップの種類]** ボックスの一覧で、リレーションシップの種類を **[固定]** に設定します。  
  
    リレーションシップの種類を **[固定]** に設定するのは、時間が経過してもメンバー間のリレーションシップが変化しないためです。 たとえば、ある都市が別の都道府県の一部となることは通常ありません。  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
6.  ダイアグラムで、 **[State-Province]** 属性を右クリックし、 **[新しい属性リレーションシップ]** をクリックします。  
  
7.  **[属性リレーションシップの作成]** ダイアログ ボックスで、 **[基になる属性]** に **[State-Province]** を指定します。 **[関連属性]** を **[Country-Region]** に設定します。  
  
8.  **[リレーションシップの種類]** ボックスの一覧で、リレーションシップの種類を **[固定]** に設定します。  
  
9. **[OK]** をクリックします。  
  
10. **[ファイル]** メニューの **[すべてを保存]** をクリックします。  
  
## <a name="deploying-changes-processing-the-objects-and-viewing-the-changes"></a>オブジェクトの配置、変更、処理、および変更内容の表示  
属性と階層を変更したら、変更を表示する前に変更を配置し、関連するオブジェクトを再処理する必要があります。  
  
#### <a name="to-deploy-the-changes-process-the-objects-and-view-the-changes"></a>変更の配置、オブジェクトの処理、および変更の表示を行うには  
  
1.  **で、** [ビルド] [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]メニューの **[Analysis Services Tutorial の配置]** をクリックします。  
  
2.  " **配置が正常に完了しました** " というメッセージが表示されたら、Customer ディメンションのディメンション デザイナーの **[ブラウザー]** タブをクリックし、ディメンション デザイナーのツール バーの左側にある [再接続] ボタンをクリックします。  
  
3.  **[階層]** ボックスで、 **[Customer Geography]** が選択されていることを確認します。次に、ブラウザー ペインで、 **[All]** 、 **[Australia]** 、 **[New South Wales]** 、 **[Coffs Harbour]** の順に展開します。  
  
    この都市の顧客がブラウザーに表示されます。  
  
4.  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Tutorial キューブの**キューブ デザイナー**に切り替えます。 これを行うには、 **ソリューション エクスプローラー** の **[キューブ]** ノードで **[Analysis Services Tutorial]** キューブをダブルクリックします。  
  
5.  **[ブラウザー]** タブをクリックし、キューブ デザイナーのツール バーにある [再接続] ボタンをクリックします。  
  
6.  **[メジャー グループ]** ペインで **[Customer]** を展開します。  
  
    [Customer] の下には、属性が展開されて表示される代わりに、表示フォルダーが表示されています。表示フォルダー値が割り当てられていない属性はそのまま表示されます。  
  
7.  **[ファイル]** メニューの **[すべてを保存]** をクリックします。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
[Product ディメンションの変更](lesson-3-3-modifying-the-product-dimension.md)  
  
## <a name="see-also"></a>参照  
[ディメンションの属性のプロパティの参照](../multidimensional-models/dimension-attribute-properties-reference.md)  
[ディメンションからの属性の削除](../multidimensional-models/attribute-properties-remove-an-attribute-from-a-dimension.md)  
[属性名を変更する](../multidimensional-models/attribute-properties-rename-an-attribute.md)  
[データ ソース ビューでの名前付き計算の定義 (Analysis Services)](../multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md)  
  
