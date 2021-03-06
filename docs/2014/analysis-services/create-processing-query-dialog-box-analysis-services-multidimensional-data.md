---
title: '[処理クエリの作成] ダイアログボックス (Analysis Services-多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.createprocessingquerydialog.f1
ms.assetid: c133d624-f35e-486e-be9f-ceafd906f168
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 225f5d757ee6b1d1da5c57b457d599fe4bb42d6c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66086764"
---
# <a name="create-processing-query-dialog-box-analysis-services---multidimensional-data"></a>[処理クエリの作成] ダイアログ ボックス (Analysis Services - 多次元データ)
  
  **の** [処理クエリの作成] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ダイアログ ボックスを使用すると、 **[ストレージのオプション]** ダイアログ ボックスの **[通知]** タブで処理クエリを作成できます。 処理クエリは、オブジェクトの多次元 OLAP (MOLAP) キャッシュを増分更新するため、最後にテーブルがポーリングされた後に、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] オブジェクトに関連付けられたテーブルへの変更を含む行セットを返すクエリです。 Analysis Services は、ポーリング クエリとして参照される他のクエリを使用して、オブジェクトに関連付けられたテーブルをポーリングし、テーブルが変更されたかどうかを判断します。 処理クエリは、オブジェクトの MOLAP キャッシュを完全に更新する場合には不要です。  
  
 通常、処理クエリはパラメーター化され、現在は次の 2 つのパラメーターがサポートされています。  
  
-   以前の定期ポーリング時のポーリング クエリによって返される単一値。  
  
-   現在の定期ポーリング時のポーリング クエリによって返される単一値。  
  
 たとえば、次の表に示すクエリは、AdventureWorksDW サンプル [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] プロジェクトの Customer ディメンションの増分更新に使用できます。  
  
|クエリの種類|クエリ ステートメント|  
|----------------|---------------------|  
|[通知]|`SELECT`<br /><br /> `MAX([CustomerKey]) AS LastCustomerKey`<br /><br /> `FROM`<br /><br /> `[dbo].[DimCustomer]`|  
|処理クエリ|`SELECT`<br /><br /> `*`<br /><br /> `FROM`<br /><br /> `[dbo].[DimCustomer]`<br /><br /> `WHERE`<br /><br /> `(CustomerKey > COALESCE (@Param1, - 1))`<br /><br /> `AND (CustomerKey <= @Param2)`|  
  
 定期ポーリング通知の増分更新の詳細については、「[プロアクティブ キャッシュ &#40;パーティション&#41;](multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md)」を参照してください。  
  
 
  **[処理クエリの作成]** ダイアログ ボックスは、**[ストレージのオプション]** ダイアログ ボックスの **[通知]** タブの **[定期ポーリング]** オプションで、グリッドの **[クエリの処理]** 列の **[...]** をクリックして表示することができます。 
  **[ストレージのオプション]** ダイアログ ボックスの **[通知]** タブの詳細については、「[[通知] ([ストレージのオプション] ダイアログ ボックス) (Analysis Services - 多次元データ)](notifications-storage-options-dialog-analysis-services-multidimensional-data.md)」を参照してください。  
  
 入力するクエリは、基になるプロバイダーで有効なクエリ コマンドである必要があります。 クエリは検証用に基になるプロバイダーが指定された状態で用意され、返される列を識別できるようになっています。 ダイアログ ボックスでは、次の 2 つのビューを表示できます。  
  
-   Visual Database Tools (VDT) クエリ ビルダー  
  
     すべてのユーザー向けです。VDT クエリ ビルダーには、SQL クエリをビジュアルに構築しテストするためのユーザー インターフェイス ツールが備えられています。  
  
-   汎用クエリ ビルダー  
  
     上級ユーザー向けです。汎用クエリ ビルダーには、SQL クエリを構築しテストするための、より単純で直接的なユーザー インターフェイスが備えられています。  
  
## <a name="options"></a>オプション  
 **Data Source**  
 クエリのデータ ソースを指定します。  
  
 **クエリ定義**  
 クエリ定義では、選択したビューに応じて、クエリの定義とテストを行うためのツール バーとペインを表示します。  
  
 **ツール バー**  
 ツール バーは、データセットの管理、表示するペインの選択、さまざまなクエリ機能の制御に使用します。  
  
|値|[説明]|  
|-----------|-----------------|  
|**[汎用クエリ ビルダーに切り替えます]**|選択すると、汎用クエリ ビルダーのビューで使用されるオプションのみが表示されます。 次のオプションのみが表示されます。<br /><br /> **SQL ペイン**<br /><br /> **結果ペイン**<br /><br /> **VDT へのスイッチ**のみを含む**ツールバー**と**実行**クエリビルダー<br /><br /> 注: このオプションは、**[VDT クエリ ビルダーに切り替えます]** が選択されている場合にのみ表示されます。|  
|**[VDT クエリ ビルダーに切り替えます]**|選択すると、Visual Database Tools (VDT) クエリ ビルダーのビューで使用できるオプションがすべて表示されます。<br /><br /> 注: このオプションは、 **[汎用クエリ ビルダーに切り替えます]** が選択されている場合にのみ表示されます。|  
|**ダイアグラムペインの表示/非表示**|**ダイアグラムペイン**の表示と非表示を切り替えます。<br /><br /> **メモ**このオプションは **、[VDT クエリビルダーに切り替え**] が選択されている場合にのみ表示されます。|  
|**[グリッドペインの表示/非表示]**|[**グリッド] ペイン**の表示と非表示を切り替えます。<br /><br /> 注: このオプションは、**[VDT クエリ ビルダーに切り替えます]** が選択されている場合にのみ表示されます。|  
|**SQL ペインの表示/非表示**|**SQL ペイン**の表示と非表示を切り替えます。<br /><br /> 注: このオプションは、**[VDT クエリ ビルダーに切り替えます]** が選択されている場合にのみ表示されます。|  
|**[結果ペインの表示/非表示]**|
  **[結果]** ペインの表示と非表示を切り替えます。<br /><br /> 注: このオプションは、**[VDT クエリ ビルダーに切り替えます]** が選択されている場合にのみ表示されます。|  
|**ラン**|クエリを実行します。 結果は**結果ペイン**に表示されます。|  
|**SQL の確認**|クエリの SQL ステートメントを確認します。<br /><br /> 注: このオプションは、**[VDT クエリ ビルダーに切り替えます]** が選択されている場合にのみ表示されます。|  
|**昇順で並べ替え**|[**グリッド] ペイン**で選択した列の出力行を昇順で並べ替えます。<br /><br /> 注: このオプションは、**[VDT クエリ ビルダーに切り替えます]** が選択されている場合にのみ表示されます。|  
|**降順で並べ替え**|[**グリッド] ペイン**で選択した列の出力行を降順で並べ替えます。<br /><br /> 注: このオプションは、**[VDT クエリ ビルダーに切り替えます]** が選択されている場合にのみ表示されます。|  
|**[フィルターの削除]**|
  **グリッド ペイン**で選択されている行に並べ替え条件を適用できる場合、その条件を削除します。<br /><br /> 注: このオプションは、**[VDT クエリ ビルダーに切り替えます]** が選択されている場合にのみ表示されます。|  
|**Group By を使用する**|クエリにグループ化機能を追加します。<br /><br /> 注: このオプションは、**[VDT クエリ ビルダーに切り替えます]** が選択されている場合にのみ表示されます。|  
|**テーブルの追加**|
  **[テーブルの追加]** ダイアログ ボックスを表示し、クエリに新しいテーブルやビューを追加できます。 
  **[テーブルの追加]** ダイアログ ボックスの詳細については、「[[テーブルの追加] ダイアログ ボックス &#40;Analysis Services - 多次元データ&#41;](add-table-dialog-box-analysis-services-multidimensional-data.md)」を参照してください。<br /><br /> 注: このオプションは、**[VDT クエリ ビルダーに切り替えます]** が選択されている場合にのみ表示されます。|  
  
 **ダイアグラムペイン**  
 クエリによって参照されるオブジェクトをダイアグラムとして表示します。 このダイアグラムには、クエリに含まれるテーブルと、その結合状態が表示されます。 テーブルの列の横にあるチェック ボックスをオンにすると、クエリの出力にその列が追加されます。オフにすると、削除されます。  
  
 テーブルをクエリに追加すると、ダイアログ ボックスでは、テーブルのキーを基にしてテーブル間の結合が行われます。 結合を追加するには、あるテーブルのフィールドを別のテーブルのフィールドにドラッグします。 結合を管理するには、結合を右クリックします。  
  
 **ダイアグラムペイン**を右クリックすると、テーブルの追加や削除、すべてのテーブルの選択、ペインの表示と非表示の切り替えを行うことができます。  
  
> [!NOTE]  
>  
  **ダイアグラム ペイン**、 **グリッド ペイン**、および **SQL ペイン** の内容は同期しているため、1 つのペインで加えた変更は他の 2 つのペインにも反映されます。  
  
> [!IMPORTANT]  
>  クエリの種類の変更は、ダイアログ ボックスではサポートされません。  
  
 **グリッド ペイン**  
 クエリから参照されるオブジェクトをグリッドに表示します。 このペインを使用して、クエリに列を追加したり、列を削除したりできます。また、各列の設定の変更も変更できます。  
  
> [!NOTE]  
>  
  **ダイアグラム ペイン**、 **グリッド ペイン**、および **SQL ペイン** の内容は同期しているため、1 つのペインで加えた変更は他の 2 つのペインにも反映されます。  
  
 **SQL ペイン**  
 クエリを SQL ステートメントとして表示します。 入力することで、クエリの SQL ステートメントを変更できます。  
  
> [!NOTE]  
>  
  **ダイアグラム ペイン**、 **グリッド ペイン**、および **SQL ペイン** の内容は同期しているため、1 つのペインで加えた変更は他の 2 つのペインにも反映されます。  
  
 **結果ペイン**  
 
  **ツール バー** ペインで **[実行]** をクリックしたときに、クエリの結果を表示します。  
  
## <a name="see-also"></a>参照  
 [多次元データ &#40;Analysis Services のデザイナーとダイアログボックス&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
