---
title: 双方向クロス フィルターを Analysis Services 表形式モデルで |Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: eee2e859abf5b7924cb072c4653ac3e83e7b7824
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68163172"
---
# <a name="bi-directional-cross-filters-in-tabular-models"></a>表形式モデルの双方向クロス フィルターします。
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  SQL Server 2016 では、表形式モデルで *双方向のクロス フィルター* を有効にするための組み込みアプローチが新たに導入されています。これにより、テーブル リレーションシップ間でフィルター コンテキストを伝達するために DAX 式を手動で作成する必要がなくなります。  
  
 この概念を構成要素に分解して説明します。 *クロス フィルタリング* は、関連テーブルの値に基づいてテーブルのフィルター コンテキストを設定する機能です。 *双方向* は、テーブル リレーションシップのもう一方の側の 2 つ目の関連テーブルにフィルター コンテキストを伝達することを意味します。 名前が示すように、一方向ではなく、双方向のリレーションシップでスライスすることができます。  内部的には、双方向のフィルタリングではフィルター コンテキストが展開され、データのスーパーセットが照会されます。  
  
 ![SSAS BIDI 1 Filteroption](../../analysis-services/tabular-models/media/ssas-bidi-1-filteroption.PNG "SSAS BIDI 1 Filteroption")  
  
 クロス フィルターの 2 種類あります。一方向と双方向のフィルター処理します。 一方向は、そのリレーションシップにおけるファクト テーブルとディメンション テーブル間の従来の多対一のフィルターです。 双方向は、両方のリレーションシップに共通する 1 つのテーブルを使用して、一方のリレーションシップのフィルター コンテキストをもう一方のテーブル リレーションシップのフィルター コンテキストとして使用できるようにするクロス フィルターです。  
  
 **FactOnlineSales** との外部キー リレーションシップを持つ **DimDate** と **DimProduct**がある場合、双方向のクロス フィルターは、 **FactOnlineSales-to-DimDate** と **FactOnlineSales-to-DimProduct** を同時に使用することに相当します。  
  
 双方向のクロス フィルターにより、表形式や Power Pivot の開発者をこれまで悩ませてきた多対多のクエリの設計に関する問題を簡単に解決できます。 表形式での多対多リレーションシップの DAX の回避策または Power Pivot のモデルを使用した場合は、期待どおりの結果が生成されるかどうかに双方向のフィルターの適用を試行できます。  
  
 双方向のクロス フィルターを作成するときには、次の点に注意してください。  
  
-   双方向のフィルターを有効にする前によく考えます。  
  
     双方向のフィルターをすべての場所で有効にすると、予想外の方法でデータが過剰にフィルター処理される可能性があります。  考えられる複数のクエリ パスを作成することで、あいまいさが生じる可能性もあります。 この両方の問題を回避するには、一方向のフィルターと双方向のフィルターの組み合わせを使用することを計画します。  
  
-   増分テストを実行して、各フィルターの変更がモデルに及ぼす影響を確認します。 増分テストには、[[Excel で分析]](../../analysis-services/tabular-models/analyze-a-tabular-model-in-excel-ssas-tabular.md) が適しています。 ベスト プラクティスとして、後で予想外のことが起こらないように、他のレポート作成クライアントを使用したテストで定期的に追跡します。  
  
> [!NOTE]  
>  CTP 3.2 以降では、SSDT に双方向のクロス フィルターを自動的に試行するかどうかを指定する既定値があります。 双方向のフィルターを既定で有効にすると、モデルでテーブル リレーションシップの連鎖を通じて 1 つのクエリ パスが明確に示される場合にのみ、双方向のフィルタリングが有効になります。  
  
## <a name="set-the-default"></a>既定値の設定  
 一方向のフィルターが既定値です。 デザイナーで作成されるすべての新しいプロジェクトの既定値を変更できます。また、プロジェクトが既に存在する場合は、モデル自体で既定値を変更できます。  
  
 設定は、プロジェクトの作成時にプロジェクト レベルで評価されるので、既定値を双方向に変更した場合、次のプロジェクトの作成時にその効果を確認できます。  
  
1.  SSDT で、 **[ツール]**  >  **[オプション]**  >  **[Analysis Services Tabular Designers]**  >  **[新しいプロジェクトの設定]** の順に選択します。  
  
2.  **[既定のフィルターの方向]** を **[一方向]** または **[双方向]** に設定します。  
  
 既定値はモデルで変更することもできます。  
  
1.  ソリューション エクスプローラーで、 **[Model.bim]**  >  **[プロパティ]** の順に選択します。  
  
2.  **[既定のフィルターの方向]** を **[一方向]** または **[双方向]** に設定します。  
  
## <a name="walkthrough-an-example"></a>サンプルの使用  
 双方向のクロス フィルタリングの価値を評価する最良の方法は、サンプルを使ってみることです。 既定で作成されたカーディナリティとクロス フィルターが反映された、 [ContosoRetailDW](http://www.microsoft.com/en-us/download/details.aspx?id=18279)の次のデータセットについて考えてみましょう。  
  
 ![SSAS BIDI 2 モデル](../../analysis-services/tabular-models/media/ssas-bidi-2-model.PNG "SSAS BIDI 2 モデル")  
  
> [!NOTE]  
>  既定では、データのインポート中に、ファクト テーブルと関連するディメンション テーブル間の外部キー リレーションシップと主キー リレーションシップから派生した多対一構成のテーブル リレーションシップが自動的に作成されます。  
  
 フィルターの方向は、ディメンション テーブルからファクト テーブルです。プロモーション、製品、日付、顧客、顧客の所在地は、いずれもメジャーの集計が正常に生成される有効なフィルターです。実際の値は、使用するディメンションによって異なります。  
  
 ![ssas bidi 3 defaultrelationships](../../analysis-services/tabular-models/media/ssas-bidi-3-defaultrelationships.PNG "ssas bidi 3 defaultrelationships")  
  
 この単純なスター スキーマでは、フィルタリングがディメンション テーブルの行と列から中央の **FactOnlineSales** テーブルにある **Sum of Sales** メジャーで提供される集計データに流れる場合に、データが適切にスライスされることが Excel でのテストで確認されています。  
  
 ![ssas bidi 4 excelSumSales](../../analysis-services/tabular-models/media/ssas-bidi-4-excelsumsales.PNG "ssas bidi 4 excelSumSales")  
  
 メジャーがファクト テーブルから取得され、フィルター コンテキストがファクト テーブルで終了していれば、このモデルの集計は正しくフィルター処理されます。 しかし、製品テーブルまたは顧客テーブルの個別カウントやプロモーション テーブルの平均割引率など、他の場所でメジャーを作成し、既存のフィルター コンテキストをそのメジャーにも適用する場合はどうなるのでしょうか。  
  
 試してみましょうから個別のカウントを追加することで**DimProducts**ピボット テーブルにします。 **Count Products**の繰り返し値に注目してください。 一見したところ、テーブル リレーションシップがないように見えますが、モデルでは、すべてのリレーションシップが完全に定義され、アクティブであることがわかっています。 この場合、繰り返し値が発生するのは、製品テーブルの行に日付フィルターがないためです。  
  
 ![ssas-bidi-5-prodcount-nofilter](../../analysis-services/tabular-models/media/ssas-bidi-5-prodcount-nofilter.png "ssas-bidi-5-prodcount-nofilter")  
  
 **FactOnlineSales** と **DimProduct**の間に双方向のクロス フィルターを追加すると、製品テーブルの行が製造元と日付で正しくフィルター処理されるようになりました。  
  
 ![ssas-bidi-6-prodcount-withfilter](../../analysis-services/tabular-models/media/ssas-bidi-6-prodcount-withfilter.png "ssas-bidi-6-prodcount-withfilter")  
  
## <a name="learn-step-by-step"></a>ステップ バイ ステップについて説明します  
 このチュートリアルの手順に従うことで、双方向のクロス フィルターを試すことができます。 先に進む必要があります。  
  
-   SQL Server 2016 Analysis Services インスタンス、表形式モード、最新リリースの CTP  
  
-   最新の CTP と共にリリースされた[SQL Server Data Tools for Visual Studio 2015 (SSDT)](http://go.microsoft.com/fwlink/p/?LinkID=627574)  
  
-   [ContosoRetailDW](http://www.microsoft.com/en-us/download/details.aspx?id=18279)  
  
-   このデータに対する読み取りアクセス許可  
  
-   Excel ("Excel で分析" で使用)  
  
### <a name="create-a-project"></a>プロジェクトを作成する  
  
1.  SQL Server Data Tools for Visual Studio 2015 を起動します。  
  
2.  **[ファイル]**  >  **[新規作成]**  >  **[プロジェクト]**  >  **[Analysis Services 表形式モデル]** の順にクリックします。  
  
3.  Tabular Model Designer で、ワークスペース データベースを、表形式のサーバー モードの SQL Server 2016 Preview Analysis Services インスタンスに設定します。  
  
4.  モデルの互換性レベルに設定することを確認**SQL Server 2016 RTM (1200)** またはそれ以降。  
  
     **[OK]** をクリックして、プロジェクトを作成します。  
  
### <a name="add-data"></a>データを追加する  
  
1.  **[モデル]**  >  **[データ ソースからのインポート]**  >  **[Microsoft SQL Server]** の順にクリックします。  
  
2.  サーバー、データベース、認証方法を指定します。  
  
3.  ContosoRetailDW データベースを選択します。  
  
4.  **[次へ]** をクリックします。  
  
5.  テーブルの選択では、Ctrl キーを押しながら次のテーブルを選択します。  
  
    -   DimProduct  
  
    -   DimCustomer  
  
    -   FactOnlineSales  
  
    -   DimGeography  
  
    -   DimPromotion  
  
     モデルでテーブル名をわかりやすくする場合は、この時点で名前を編集できます。  
  
     ![ssas-bidi-7-ImportData](../../analysis-services/tabular-models/media/ssas-bidi-7-importdata.PNG "ssas-bidi-7-ImportData")  
  
6.  データをインポートします。  
  
 エラーが発生した場合は、データベースへの接続に使用しているアカウントが、Contoso データ ウェアハウスに対する読み取りアクセス許可を持つ SQL Server ログインを持っていることを確認します。 リモート接続で、SQL Server に対するファイアウォールのポート構成を確認することもできます。  
  
### <a name="review-default-table-relationships"></a>既定のテーブル リレーションシップの確認  
 ダイアグラム ビューに切り替えます。**モデル** > **モデル ビュー** > **ダイアグラム ビュー**します。 カーディナリティとアクティブなリレーションシップが視覚的に示されます。 リレーションシップは、いずれも 2 つの関連テーブル間の一対多のリレーションシップです。  
  
 ![SSAS BIDI 2 モデル](../../analysis-services/tabular-models/media/ssas-bidi-2-model.PNG "SSAS BIDI 2 モデル")  
  
 **[テーブル]**  >  **[リレーションシップの管理]** の順にクリックすると、同じ情報をテーブル レイアウトで表示することもできます。  
  
 ![ssas bidi 3 defaultrelationships](../../analysis-services/tabular-models/media/ssas-bidi-3-defaultrelationships.PNG "ssas bidi 3 defaultrelationships")  
  
### <a name="create-measures"></a>メジャーを作成する  
 ディメンション データのさまざまな側面を売り上げ高の合計を集計する必要があります。 **DimProduct** で、製品数をカウントするメジャーを作成し、特定の年、特定の地域、または顧客タイプの売上に関与する製品の数を示す、製品販売促進の分析に使用できます。  
  
1.  **[モデル]**  >  **[モデル ビュー]**  >  **[ダイアグラム ビュー]** をクリックします。  
  
2.  **[FactOnlineSales]** をクリックします。  
  
3.  **[SalesAmount]** 列を選択します。  
  
4.  **[列]**  >  **[オート SUM]**  >  **[合計]** の順にクリックして、売上のメジャーを作成します。  
  
5.  **[DimProduct]** をクリックします。  
  
6.  **[ProductKeycolumn]** を選択します。  
  
7.  **[列]**  >  **[オート SUM]**  >  **[DistinctCount]** の順にクリックして、一意の製品のメジャーを作成します。  
  
### <a name="analyze-in-excel"></a>[Excel で分析]  
  
1.  **[モデル]**  >  **[Excel で分析]** の順にクリックして、すべてのデータをピボットテーブルにまとめます。  
  
2.  フィールドの一覧から先ほど作成した 2 つのメジャーを選択します。  
  
3.  **[製品]**  >  **[製造元]** を選択します。  
  
4.  **[Date]**  >  **[Calendar Year]** の順に選択します。  
  
 売上が年と製造元で予想どおりに分類されていることがわかります。 これは、既定のフィルター コンテキスト間**FactOnlineSales**、 **DimProduct**、および**DimDate**リレーションシップの「多」側のメジャーを正常に動作します。  
  
 同時に、売上と同じフィルター コンテキストで製品数が取得されていないこともわかります。 製品数は製造元で正しくフィルター処理されていますが (製造元と製品数は同じテーブルに存在)、日付フィルターが製品数に反映されていません。  
  
### <a name="change-the-cross-filter"></a>クロス フィルターの変更  
  
1.  モデルに戻り、 **[テーブル]**  >  **[リレーションシップの管理]** の順に選択します。  
  
2.  **FactOnlineSales** と **DimProduct**の間のリレーションシップを編集します。  
  
     フィルターの方向を両方のテーブルに変更します。  
  
3.  設定を保存します。  
  
4.  ブックで **[更新]** をクリックして、モデルを再度読み取ります。  
  
 **DimProducts** の製造元だけでなく、 **DimDate**のカレンダー年度も含まれた同じフィルター コンテキストで、製品数と売上の両方がフィルター処理されているのがわかります。  
  
## <a name="next-steps"></a>次の手順  
 双方向のクロス フィルターをいつどのように使用するかの理解は、実際のシナリオでそのしくみを確認する試行錯誤の問題と言えます。 組み込みのビヘイビアーが十分でないし、作業を完了させるために DAX 計算でフォールバックする必要がありますがあります。 **参照** セクションで、この件に関するその他のリソースをいくつかのリンクを検索します。  
  
 実際には、クロス フィルタリングにより、通常は多対多構造によってのみ実現されるデータ探索の方法を実現できます。 その双方向クロス フィルター処理を認識する重要であること、ただしは多対多構造ではありません。  このリリースの表形式モデルのデザイナーでは、実際の多対多テーブル構成は引き続きサポートされていません。  
  
## <a name="see-also"></a>関連項目  
 [Power BI Desktop でのリレーションシップの作成と管理](https://support.powerbi.com/knowledgebase/articles/464155-create-and-manage-relationships-in-power-bi-desktop)   
 [Power Pivot とテーブル モデルでの単純な多 manay 関係を処理する方法の実用的な例](http://social.technet.microsoft.com/wiki/contents/articles/22202.a-practical-example-of-how-to-handle-simple-many-to-many-relationships-in-power-pivotssas-tabular-models.aspx)   
 [Resolving Many-to-Many relationships leveraging DAX Cross Table Filtering (DAX のテーブル間フィルタリングを利用した多対多リレーションシップの解決)](http://blog.gbrueckl.at/2012/05/resolving-many-to-many-relationships-leveraging-dax-cross-table-filtering/)   
 [Many-to-Many Revolution (SQLBI ブログ)](http://www.sqlbi.com/articles/many2many/)  
  
  
