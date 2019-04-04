---
title: Power View レポートのレポート プロパティの構成 |Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e9122ab6f783e6b845c1a961c133d66e58e933e7
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2018
ms.locfileid: "52544279"
---
# <a name="supplemental-lesson---configure-reporting-properties-for-power-view-reports"></a>補助レッスン - Power View レポートのレポートのプロパティを構成します。
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

この補足のレッスンでは、レポート、AW Internet Sales プロジェクトのプロパティを設定します。 レポートのプロパティを使用すると、Power View 内のモデル データの選択や表示をエンド ユーザーが簡単にできるようになります。 また、プロパティを設定して、特定の列やテーブルの非表示や、グラフで使う新しいデータの作成を行います。   
  
このレッスンを完了するまでに時間を推定するには。**30 分**  
  
## <a name="prerequisites"></a>前提条件  
この補足のレッスンは表形式モデルの作成チュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。 この補足のレッスンの作業を実行する前に、前のレッスンをすべて完了している必要があります。  
この補足のレッスンを完了するには、次の準備も必要です。  
  
-   (このチュートリアルを完了します)、AW Internet Sales プロジェクトを展開または Analysis Services サーバーに既に配置の準備。  
  
  
## <a name="model-properties-that-affect-reporting"></a>レポートに影響するモデルのプロパティ  
表形式モデルを作成するとき、個々の列やテーブルに特定のプロパティを設定して、エンド ユーザーが Power View のレポートをより使いやすくすることができます。 また、データの視覚エフェクトをサポートする追加のモデル データや、レポート クライアントに固有の他の機能を作成することもできます。 ここでは、Adventure Works Internet Sales Model のサンプルにいくつかの変更を加えます。  
  
-   **新しいデータを追加**-にグラフを表示しやすい形式で日付の情報を作成する計算列で DAX 数式を使用して新しいデータを追加します。  
  
-   **エンド ユーザーには不要なテーブルと列の非表示** - **[非表示]** プロパティは、テーブルやテーブルの列をレポート クライアントに表示するかどうかを制御します。 項目は非表示になってもモデルの一部であり、引き続きクエリや計算に使用できます。  
  
-   **クリック 1 回でテーブルを有効にする**-既定も何も起こりません、エンドユーザーが、フィールド リストでテーブルをクリックします。 この動作を変更して、テーブルをクリックするとそのテーブルがレポートに追加されるようにするには、テーブルに含める各列に既定のフィールド セットを設定します。 このプロパティは、エンド ユーザーの使用頻度の高いテーブルの列に設定されます。  
  
-   **必要に応じたグループの設定** - **[一意の行の保持]** プロパティは、列内の値を別のフィールド (識別子フィールドなど) の値によってグループ化するかどうかを決定します。 Customer Name のように重複した値が含まれる列 (たとえば、"John Smith" という顧客が複数存在する可能性があります) では、エンド ユーザーに正しい結果を提供するために、 **[行識別子 (ROWID)]** フィールドでグループ化 (一意の行を保持) することが重要です。  
  
-   **データ型とデータ形式の設定** - 既定では、フィールドをメジャーとして使用できるかどうかを判断するために、Power View は列のデータ型に基づいたルールを適用します。 Power View におけるデータの視覚エフェクトにはそれぞれ、メジャーと非メジャーをどこに配置するかについてのルールもあるので、エンド ユーザーが適切な操作を実行するように、モデル内のデータ型を設定したり、既定値をオーバーライドしたりすることが重要です。  
  
-   **列で並べ替えを設定**プロパティ -、**列による並べ替え**プロパティは、列の値を別のフィールドの値によって並べ替えするかどうを指定します。 たとえば、月の名前を含む Month Calendar 列を Month Number 列によって並べ替えます。  
  
## <a name="hide-tables-from-client-tools"></a>クライアント ツールでのテーブルの非表示  
Product テーブルには既に Product Category 計算列と Product Subcategory 計算列があるので、クライアント アプリケーションに Product Category テーブルと Product Subcategory テーブルを表示する必要はありません。  
  
#### <a name="to-hide-the-product-category-and-product-subcategory-tables"></a>Product Category テーブルと Product Subcategory テーブルを非表示にするには  
  
1.  モデル デザイナーで、 **Product Category** テーブル (タブ) を右クリックし、 **[クライアント ツールに非表示]** をクリックします。  
  
2.  **Product Subcategory** テーブル (タブ) を右クリックし、 **[クライアント ツールに非表示]** をクリックします。  
  
## <a name="create-new-data-for-charts"></a>グラフ用の新しいデータの作成  
DAX 式を使用して、モデル内で新しいデータを作成することが必要な場合があります。 ここでは、Date テーブルに 2 つの新しい計算列を追加します。 これらの新しい列は、グラフで使うのに便利な形式の日付フィールドを提供します。  
  
#### <a name="to-create-new-data-for-charts"></a>グラフ用の新しいデータを作成するには  
  
1.  **Date** テーブルを右端までスクロールして、 **[列の追加]** をクリックします。  
  
2.  数式バーで次の式を使用して、2 つの新しい計算列を追加します。  
  
    |列名|[数式]|  
    |---------------|-----------|  
    |Year Quarter|=[Calendar Year] & " Q" & [Calendar Quarter]|  
    |年月|=[Calendar Year] & FORMAT([Month],"#00")|  
  
## <a name="default-field-set"></a>既定のフィールド セット  
既定のフィールド セットは、列とテーブルは、レポート フィールド リスト内でクリックしたときに自動的にレポート キャンバスに追加されるテーブルのメジャーの定義済み一覧です。 基本的に、このテーブルが Power View レポート内で視覚化されたときにユーザーに表示される既定の列、メジャー、フィールドの順序を指定できます。  Internet Sales モデルでは、Customer、Geography、Product の各テーブルの既定のフィールド セットと順序を定義します。 含まれるのは、Power View レポートを使用して Adventure Works Internet Sales データを分析するときにユーザーが表示する必要がある、使用頻度の高いこれらの列のみです。  
  
既定のフィールド セットの詳細については、[を構成する既定のフィールド セット Power View レポートの](../analysis-services/tabular-models/power-view-configure-default-field-set-for-reports.md)SQL Server オンライン ブックの「を参照してください。  
  
#### <a name="to-set-default-field-set-for-tables"></a>テーブルの既定のフィールド セットを設定するには  
  
1.  モデル デザイナーで、 **Customer** テーブル (タブ) をクリックします。  
  
2.  **[プロパティ]** ウィンドウの **[レポートのプロパティ]** の **[既定のフィールド セット]** プロパティで、 **[クリックして編集]** をクリックして **[既定のフィールド セット]** ダイアログ ボックスを開きます。  
  
3.  **[既定のフィールド セット]** ダイアログ ボックスの **[テーブル内のフィールド]** ボックスの一覧で、Ctrl キーを押しながら次のフィールドをクリックし、 **[追加]** をクリックします。  
  
    **[Birth Date]**、 **[Customer Alternate Id]**、 **[First Name]**、 **[Last Name]**。  
  
4.  **[既定のフィールド (並べ替え順)]** ウィンドウで、[上へ移動] と [下へ移動] を使用して次の順序に並べます。  
  
    **[Customer Alternate Id]**  
  
    **[First Name]**  
  
    **[Last Name]**  
  
    **Birth Date**  
  
5.  **[OK]** をクリックして、 **Customer** テーブルの **[既定のフィールド セット]** ダイアログ ボックスを閉じます。  
  
6.  **Geography** テーブルでも同じ手順を実行し、次のフィールドをこの順序に並べます。  
  
    **City**、 **State Province Code**、 **Country Region Code**。  
  
7.  最後に、 **Product** テーブルについても同じ手順を実行し、次のフィールドをこの順序に並べます。  
  
    **Product Alternate Id**、 **Product Name**。  
  
## <a name="table-behavior"></a>テーブルの動作  
[テーブルの動作] プロパティを使用すると、Power View レポートで使用するテーブルについて、さまざまな視覚エフェクトの種類の既定の動作およびグループ化動作を変更できます。 これにより、名前やイメージ、またはタイル、カード、グラフ レイアウトのタイトルなど、識別情報の適切な既定位置を設定できます。  
  
テーブル動作プロパティの詳細については、[Power View レポート用のテーブル動作プロパティの構成](../analysis-services/tabular-models/power-view-configure-table-behavior-properties-for-reports.md)SQL Server オンライン ブックの「を参照してください。  
  
#### <a name="to-set-table-behavior"></a>テーブルの動作を設定するには 
  
1.  モデル デザイナーで、 **Customer** テーブル (タブ) をクリックします。  
  
2.  **[プロパティ]** ウィンドウの **[テーブルの動作]** プロパティで、 **[クリックして編集]** をクリックして **[テーブルの動作]** ダイアログ ボックスを開きます。  
  
3.  **[テーブルの動作]** ダイアログ ボックスの **[行識別子 (ROWID)]** ボックスの一覧から、 **[Customer Id]** 列を選択します。  
  
4.  **[一意の行の保持]** ボックスの一覧の、 **[First Name]** と **[Last Name]** を選択します。  
  
    このプロパティを設定することで、重複している場合でも一意として扱う必要のある値をこれらの列が提供することを指定します (たとえば、同姓または同名の従業員が複数いる場合など)。  
  
5.  **[既定のラベル]** ボックスの一覧から、 **[Last Name]** 列を選択します。  
  
    このプロパティを設定することで、この列が行データを表す表示名を提供することを指定します。  
  
6.  **Geography** テーブルについても同じ手順を繰り返します。行識別子 (ROWID) として **[Geography Id]** 列を選択し、 **[一意の行の保持]** ボックスの一覧の **[City]** 列を選択します。 このテーブルには、既定のラベルを設定する必要はありません。  
  
7.  **Product** テーブルについても同じ手順を繰り返します。行識別子 (ROWID) として **[Product Id]** 列を選択し、 **[一意の行の保持]** ボックスの一覧の **[Product Name]** 行を選択します。 **[既定のラベル]** には、 **[Product Alternate Id]** を選択します。  
  
## <a name="reporting-properties-for-columns"></a>列の [レポートのプロパティ]  
列にはいくつかの基本のプロパティと列に固有のレポート プロパティがあり、このプロパティを設定することにより、モデルのレポートをより使いやすくすることができます。 たとえば、ユーザーが必ずしもすべてのテーブルのすべての列を見る必要がない場合もあります。 列の Hidden プロパティを使用して、Product Category と Product Subcategory テーブルの前に、例は、それ以外の場合に表示されているテーブルから特定の列を非表示にすることができます。 [データ形式] や [列で並べ替え] などの他のプロパティも、レポート内の列データの表示に影響を及ぼします。 ここでは、特定の列にいくつかのプロパティを設定します。 操作の必要がない他の列は、以下には表示していません。  
  
ここでは、さまざまな列のプロパティのうちの一部のみを設定しますが、他にも多くのプロパティがあります。 詳細レポートのプロパティの列に関する情報を参照してください。[列プロパティ](../analysis-services/tabular-models/column-properties-ssas-tabular.md)SQL Server オンライン ブックの「します。  
  
#### <a name="to-set-properties-for-columns"></a>列のプロパティを設定するには  
  
1.  モデル デザイナーで、 **Customer** テーブル (タブ) をクリックします。  
  
2.  **[Customer Id]** 列をクリックして、 **[プロパティ]** ウィンドウに列のプロパティを表示します。  
  
3.  **[プロパティ]** ウィンドウで、 **[非表示]** プロパティを True に設定します。 **[Customer Id]** 列は、モデル デザイナーではグレーで表示されるようになります。  
  
4.  この手順を繰り返して、以下の各表に指定するように列のレポート プロパティを設定します。 他のプロパティはすべて、既定の設定のままにしておきます。  
  
    注:すべての日付列のことを確認します**データ型**は**日付**します。  
  
    **Customer**  
  
    |[列]|プロパティ|値|  
    |----------|------------|---------|  
    |[Geography Id]|[非表示]|True|  
    |[Birth Date]|データ形式|短い日付|  
  
    **Date**  
  
    > [!NOTE]  
    > 日付テーブルが日付テーブルの設定として、マークを使用して、モデルの日付テーブルとして選択された、ためにレッスン 7 に。一意の識別子では、日付列の行識別子プロパティとして使用するには、日付テーブルとしてマークと、列と日付のテーブルに日付列は自動的に True に設定して、変更できません。 DAX 式でタイム インテリジェンス関数を使用するときは、日付テーブルを指定する必要があります。 このモデルでは、タイム インテリジェンス関数を使用していくつかのメジャーを作成して、さまざまな期間 (前四半期と現四半期など) の売上データを計算しました。これは KPI にも使用できます。 日付テーブルの指定に関する詳細については、[タイム インテリジェンスで使用するための日付テーブルとしてマーク の指定](../analysis-services/tabular-models/specify-mark-as-date-table-for-use-with-time-intelligence-ssas-tabular.md)SQL Server オンライン ブックの「を参照してください。  
  
    |[列]|プロパティ|値|  
    |----------|------------|---------|  
    |date|データ形式|短い日付|  
    |Day Number of Week|[非表示]|True|  
    |Day Name|[列で並べ替え]|Day Number of Week|  
    |Day of Week|[非表示]|True|  
    |Day of Month|[非表示]|True|  
    |Day of Year|[非表示]|True|  
    |Month Name|[列で並べ替え]|Month|  
    |Month|[非表示]|True|  
    |Month Calendar|[非表示]|True|  
    |Fiscal Quarter|[非表示]|True|  
    |Fiscal Year|[非表示]|True|  
    |Fiscal Semester|[非表示]|True|  
  
    **Geography**  
  
    |[列]|プロパティ|値|  
    |----------|------------|---------|  
    |[Geography Id]|[非表示]|True|  
    |Sales Territory Id|[非表示]|True|  
  
    **Product**  
  
    |[列]|プロパティ|値|  
    |----------|------------|---------|  
    |[Product Id]|[非表示]|True|  
    |Product Alternate Id|[既定のラベル]|True|  
    |Product Subcategory Id|[非表示]|True|  
    |Product Start Date|データ形式|短い日付|  
    |Product End Date|データ形式|短い日付|  
  
    **Internet Sales**  
  
    |[列]|プロパティ|値|  
    |----------|------------|---------|  
    |[Product Id]|[非表示]|True|  
    |[Customer Id]|[非表示]|True|  
    |Promotion Id|[非表示]|True|  
    |Currency Id|[非表示]|True|  
    |Sales Territory Id|[非表示]|True|  
    |Order Quantity|データ型<br /><br />データ形式<br /><br />小数点以下表示桁数|10 進数<br /><br />10 進数<br /><br />0|  
    |Order Date|データ形式|短い日付|  
    |Due Date|データ形式|短い日付|  
    |Ship Date|データ形式|短い日付|  
  
## <a name="redeploy-the-adventure-works-internet-sales-tabular-model"></a>Adventure Works Internet Sales 表形式モデルの再配置  
モデルを変更したので、再配置する必要があります。  
  
#### <a name="to-redeploy-the-adventure-works-internet-sales-tabular-model"></a>Adventure Works Internet Sales 表形式モデルを再配置するには  
  
-   SSDT で、**ビルド** メニューをクリック**Adventure Works の Internet Sales Model を導入**します。  
  
    **[配置]** ダイアログ ボックスが表示され、メタデータの配置状況と、モデルに含まれる各テーブルが表示されます。  
  
## <a name="next-steps"></a>次の手順  
これで、Power View を使用してモデルのデータを表示できるようになりました。 SharePoint サイトの Analysis Services と Reporting Services のアカウントが、モデルを配置した Analysis Services インスタンスに対する読み取り権限を持っていることを確認します。  
  
モデルを参照する Reporting Services のレポート データ ソースを作成するには、「 [データ モデルの共有データ ソースの作成 (SSRS)](http://msdn.microsoft.com/library/hh270317%28v=SQL.110%29.aspx)」を参照してください。  
  
  
  
