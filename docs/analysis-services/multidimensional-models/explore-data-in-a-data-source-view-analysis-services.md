---
title: データ ソース ビュー (Analysis Services) でのデータの探索 |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4a7cb3d9895c7524bf0517270b50ac7830774dd9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68177805"
---
# <a name="explore-data-in-a-data-source-view-analysis-services"></a>データ ソース ビューでのデータの検索 (Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  **のデータ ソース ビュー デザイナーにある** [データの探索] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ダイアログ ボックスを使用すると、テーブル、ビュー、または名前付きクエリのデータをデータ ソース ビュー (DSV) で参照できます。 データ ソース ビュー デザイナーでデータを探索すると、選択したテーブル、ビュー、または名前付きクエリの各データ列の内容を表示できます。 実際の内容を表示すると、すべての列が必要であるかどうか、使いやすさを向上させるために名前付き計算が必要であるかどうか、既存の名前付き計算または名前付きクエリによって予想値が返されるかどうかなどを判断できます。  
  
 データを表示するには、DSV で選択したオブジェクトのデータ ソースに対するアクティブな接続が必要です。 また、テーブル内の名前付き計算もクエリで送信されます。  
  
 データは表形式で返されるので、並べ替えてコピーできます。 列のヘッダーをクリックすると、その列で行が再度並べ替えられます。 グリッドでデータを選択して、Ctrl キーを押しながら C キーを押すと、選択範囲をクリップボードにコピーできます。  
  
 また、サンプリング方法やサンプル数を制御することもできます。 既定では、上位 5,000 行が返されます。  
  
## <a name="to-browse-data-or-change-sampling-options"></a>データの参照またはサンプリング オプションを変更するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]でプロジェクトを開くか、またはデータを参照するデータ ソース ビューが含まれているデータベースに接続します。  
  
2.  ソリューション エクスプローラーで、 **[データ ソース ビュー]** フォルダーを展開して、データ ソース ビューをダブルクリックします。  
  
3.  表示するデータが含まれているテーブル、ビュー、または名前付きクエリを右クリックして、 **[データの探索]** をクリックします。  
  
     データは、ソースの基になるテーブル、ビュー、または、名前付きクエリのデータ ソース ビューがクエリと、結果に表示されます、**探索\<オブジェクト名 > テーブル**タブ。  
  
4.  **探索\<オブジェクト名 > テーブル**ツールバーで、をクリックして、**サンプリング オプション**アイコン。  
  
     **[データ探索オプション]** ダイアログ ボックスが開きます。 このダイアログ ボックスでは、サンプリング方法 (既定のサンプリング サイズである 5,000 行以外のレコード数) またはサンプル数を指定できます。  
  
5.  **[OK]** または **[キャンセル]** をクリックします。  
  
6.  データのサンプルを再取得には、次のようにクリックします。**データの再取得**上、**探索\<オブジェクト名 > テーブル**ツールバー。  
  
## <a name="see-also"></a>関連項目  
 [「多次元モデルのデータ ソース ビュー」](../../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)  
  
  
