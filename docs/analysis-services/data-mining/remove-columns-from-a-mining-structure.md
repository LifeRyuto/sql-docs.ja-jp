---
title: マイニング構造から列を削除 |Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bd8691d8ec0cc1546e27e8195e7d0bbc20709f59
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68209688"
---
# <a name="remove-columns-from-a-mining-structure"></a>マイニング構造からの列の削除
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  データ マイニング デザイナーを使用して、マイニング構造の作成後に構造から列を削除できます。 マイニング構造列を削除する理由には、次のようなものがあります。  
  
-   マイニング構造に列の複数のコピーが格納されており、モデルで重複データを使用しないようにする。  
  
-   データを保護する必要があるが、ドリルスルーが有効になっている。  
  
-   データがモデリングで使用されておらず、処理する必要がない。  
  
 マイニング構造から列を削除しても、データ ソース ビュー内の列または外部データ内の列は変更されません。メタデータのみ削除されます。 ただし、マイニング構造で使用される列を変更する場合は、構造およびその構造に基づくモデルを再処理する必要があります。  
  
### <a name="to-remove-a-column-from-the-mining-structure"></a>マイニング構造から列を削除するには  
  
1.  データ マイニング デザイナーで **[マイニング構造]** タブを選択します。  
  
2.  マイニング構造のツリーを展開し、すべての列を表示します。  
  
3.  削除する列を右クリックして、 **[削除]** をクリックします。  
  
4.  **[オブジェクトの削除]** ダイアログ ボックスで **[OK]** をクリックします。  
  
## <a name="see-also"></a>関連項目  
 [マイニング構造のタスクと操作方法](../../analysis-services/data-mining/mining-structure-tasks-and-how-tos.md)  
  
  
