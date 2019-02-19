---
title: グラフの余白の追加または削除 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.date: 03/03/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 91c43f58-5771-4d33-a54d-0e802d2f5cba
author: markingmyname
ms.author: maghan
ms.openlocfilehash: f67d19d880cabce72d99bc841e0142520234afc7
ms.sourcegitcommit: 31800ba0bb0af09476e38f6b4d155b136764c06c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2019
ms.locfileid: "56290090"
---
# <a name="add-or-remove-margins-from-a-chart-report-builder-and-ssrs"></a>グラフの余白の追加または削除 (レポート ビルダーおよび SSRS)
[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のページ分割されたレポート内の縦棒グラフおよび散布図では、横余白が X 軸の両端に自動的に追加されます。 横棒グラフでは、横余白が Y 軸の両端に自動的に追加されます。 その他すべての種類のグラフでは、横余白は追加されません。 余白のサイズは変更できません。  
  
 このトピックは、円グラフ、ドーナツ グラフ、じょうごグラフ、またはピラミッド グラフには当てはまりません。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-enable-or-disable-side-margins"></a>横余白を有効または無効にするには  
  
1.  軸を右クリックし、 **[軸のプロパティ]** を選択します。 **[縦軸のプロパティ]** ダイアログ ボックスまたは **[横軸のプロパティ]** ダイアログ ボックスが表示されます。  
  
2.  **[軸のオプション]** ページで、 **[横余白]** プロパティを設定します。  
  
    -   **[自動]** グラフの種類に基づいて横余白を追加するかどうかが判断されます。  
  
    -   **[無効]** 横棒グラフ、縦棒グラフ、および散布図では、横余白はなしになります。  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>参照  
 [グラフの軸ラベルの書式設定 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)   
 [[軸のオプション] ([軸のプロパティ] ダイアログ ボックス) &#40;レポート ビルダーおよび SSRS&#41;](https://msdn.microsoft.com/library/b276e210-7a12-48ae-971b-7dabae51df11)   
 [軸の間隔の指定 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/specify-an-axis-interval-report-builder-and-ssrs.md)   
 [日付または通貨として軸ラベルを書式設定する &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md)   
 [グラフ &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)  
  
  
