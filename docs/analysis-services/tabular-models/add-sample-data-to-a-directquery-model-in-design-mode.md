---
title: デザイン モードで Analysis Services の DirectQuery モデルにサンプル データを追加する |Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: db5ef518a715553b1eecbeeaf5a5ba248b365bf5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68207857"
---
# <a name="add-sample-data-to-a-directquery-model-in-design-mode"></a>Design モードで DirectQuery モデルにサンプル データを追加する
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
 DirectQuery モードでは、テーブルのパーティションがモデルのデザイン時に使用されるサンプル データのサブセットを作成するか、完全なデータ ビューの代替手段の作成に使用されます。
 
 DirectQuery テーブル モデルを配置するとき、パーティションはテーブルあたり 1 つだけ許可されます。そのパーティションは完全データ ビューにする必要があります。 追加パーティションは完全データ ビューの代替かサンプル データになります。 このトピックでは、データのサブセットを含むサンプル パーティションの作成について説明します。
 
 既定では、SSDT で DirectQuery モデルにテーブル モデルをデザインするとき、モデルの作業用データベースにデータは含まれません。 テーブルごとに 1 つの既定パーティションがあり、このパーティションがすべてのクエリをデータ ソースに送信します。 
  
ただし、デザイン時に使用するために少量のサンプル データをモデルの作業用データベースに追加することができます。 サンプル データは、デザイン時にのみ使用されるパーティションに対するクエリを使用して指定されます。 モデルと共にメモリ内にキャッシュされます。 そのため、データ ソースに影響を与えずに、モデリングに関する決定を検証できます。 SQL Server Data Tools (SSDT) の **Excel で分析** の利用時に、または、ワークスペース データベースに接続する他のクライアント アプリケーションから、サンプル データセットを使用してモデリングに関する決定事項をテストすることができます。  
  
> [!TIP]  
>  空のモデルの DirectQuery モードでも、各テーブルの小規模な組み込み行セットをいつでも表示できます。 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]で、 **[テーブル]**  >  **[テーブルのプロパティ]** の順にクリックすると、50 行データセットが表示されます。  
  
## <a name="create-a-sample-partition"></a>サンプル パーティションの作成
 これらの手順では、表形式モデルで作成されたか、互換性レベル 1200 以上にアップグレードします。 それより下の互換性レベルのモデルでは、キャッシュされたデータの取得に別のプロパティが使用されます。 プロパティの説明については、「 [SSMS での DirectQuery モードの有効化](../../analysis-services/tabular-models/enable-directquery-mode-in-ssms.md) 」を参照してください。  
  
1.  SQL Server Data Tools の [図] または [データ ビュー] で、ファクト テーブルをクリックし、そのプロパティ ページを開きます。 ファクト テーブルには、モデルで集計された数値データや指標が表示されます。 ファクト テーブルは複数ある場合があります。  
  
2.  **[テーブル]**  >  **[プロパティ]** の順にクリックして [パーティション管理] ダイアログ ボックスを開きます。  
  
    既定のパーティションは **(直接クエリ)\<テーブル名 >** します。 これが完全データ ビューです。 このパーティションは削除しないでください。 このパーティションは、モデルを配置するときに使用されます。  
  
4.  パーティションを選択し、 **[コピー]** をクリックします。  

    これにより既定のパーティションのコピーが作成されますが、このコピーには、クエリで指定したサンプル データが含まれています。 以下に例を示します。
  
     ![ssas_tabularproject_copypartition](../../analysis-services/tabular-models/media/ssas-tabularproject-copypartition.jpg "ssas_tabularproject_copypartition")  
  
5.  コピーされたパーティションを選択し、 **[SQL クエリ エディター]** ボタンをクリックしてフィルターを追加します。 モデルの作成中はサンプル データのサイズを小さくします。 たとえば、AdventureWorksDW から **[FactInternetSales]** を選択した場合、フィルターは次のようになります。  
  
    ```  
    SELECT [dbo].[FactInternetSales].* FROM [dbo].[FactInternetSales]  
    JOIN DimSalesTerritory as ST  
    ON ST.SalesTerritoryKey = FactInternetSales.SalesTerritoryKey  
    WHERE ST.SalesTerritoryGroup='North America';  
    ```  
  
6.  **[検証]** をクリックすると、構文エラーがチェックされます。  
  
     DirectQuery モードでは、[パーティション] ダイアログ ボックスの **[新規]** 、 **[コピー]** 、 **[削除]** ボタンに加え、 **[サンプルとして設定する]** または **[DirectQuery として設定する]** と表示する切り替えボタンもあります。  
  
     DirectQuery パーティションになれるパーティションは 1 つだけです。 これは、テーブルに定義されているパーティションを選択し、 **[サンプルとして設定する]** をクリックすることで変更できます。  
  
7.  テーブルを処理します。  
  


  
  
