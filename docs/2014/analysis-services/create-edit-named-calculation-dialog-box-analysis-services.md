---
title: 作成編集という名前の計算 ダイアログ ボックス (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dsveditor.createnamedcalculation.f1
helpviewer_keywords:
- Named Calculation dialog box
ms.assetid: 66fb30ae-f5c5-4bfc-80ca-8c8a3a9bb30d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 31c0444930e15d933d75dd72554c3232871cd59e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62679939"
---
# <a name="create-edit-named-calculation-dialog-box-analysis-services"></a>名前付き計算 ダイアログ ボックス (Analysis Services) の作成、編集
  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] の **[名前付き計算の作成]/[名前付き計算の編集]** ダイアログ ボックスを使用すると、データ ソース ビューにあるテーブルの名前付き計算を定義または変更できます。 **[名前付き計算の作成]/[名前付き計算の編集]** ダイアログ ボックスを表示するには、次の手順に従います。  
  
-   **データ ソース ビュー デザイナー**の **[ツール バー]** ペインにある **[新しい名前付き計算]** をクリックします。  
  
-   **データ ソース ビュー デザイナー**の **[テーブル]** ペインまたは **[ダイアグラム]** ペインにあるテーブルを右クリックして、**[新しい名前付き計算]** をクリックします。  
  
-   **データ ソース ビュー デザイナー**の **[ダイアグラム]** ペインで、名前付き計算の名前を右クリックして、**[名前付き計算の編集]** をクリックします。  
  
## <a name="options"></a>および  
 **列名**  
 名前付き計算の名前を入力します。  
  
 **[説明]**  
 名前付き計算の説明をオプションで入力します。  
  
 **[式]**  
 スカラー値を返す有効な SQL 式を入力します。 この式はプロバイダーに送られ、次の式により検証されます。  
  
```  
SELECT <Table Name in Data Source>.* , <Expression> AS <Column Name> FROM <Table Name in Data Source>AS <Table Name in Data Source View>  
```  
  
 式では、下位選択ステートメントを使用して他のテーブルへの参照を含めることができます。 If the expression would require parentheses in a SELECT statement, the expression entered must be enclosed between parentheses.  
  
## <a name="see-also"></a>参照  
 [Analysis Services のデザイナーおよびダイアログ ボックス&#40;多次元データ&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [データ ソース ビュー デザイナー (Analysis Services - 多次元データ)](data-source-view-designer-analysis-services-multidimensional-data.md)  
  
  
