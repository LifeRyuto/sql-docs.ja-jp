---
title: ヒット カウントの指定
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- vs.debug.breakpt.hitcount
helpviewer_keywords:
- Transact-SQL debugger, breakpoint hit count
ms.assetid: 24836939-94ed-4e57-aa85-5d6938d859e4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a049491513b826b2b050081b40cb5319ca74160f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "75243213"
---
# <a name="specify-a-hit-count"></a>ヒット カウントの指定
  ブレークポイントのヒット カウントは、ブレークポイントに達するたびに [!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーによって増加されるカウンターです。 指定したヒット カウントに達し、指定したブレークポイントの条件が満たされると、ブレークポイントに指定されたアクションがデバッガーによって実行されます。  
  
## <a name="hit-count-considerations"></a>ヒット カウントの考慮事項  
 既定では、ブレークポイントにヒットするたびに、実行が中断します。 次のオプションのいずれかを選択できます。  
  
-   常に中断する (既定)。  
  
-   ヒット カウントが指定した値と等しくなったときに中断する。  
  
-   ヒット カウントが指定した値の倍数と等しくなったときに中断する。  
  
-   ヒット カウントが指定した値以上になったときに中断する。  
  
 ブレークポイントのヒット カウントは、デバッグ セッションのスコープ内で増加します。 すべてのヒット カウントは各デバッグ セッションの開始時に 0 に設定されます。  
  
 ブレークポイントで実行を中断せずに、ブレークポイントにヒットした回数を追跡する場合は、ヒット カウントに非常に大きい値を指定して、ブレークポイントで中断しないようにします。  
  
 ブレークポイントの既定のアクションでは、ヒット カウントとブレークポイントの条件の両方が満たされたときに、実行が中断されます。 他のアクションを指定する方法の詳細については、「 [ブレークポイント アクションの指定](specify-a-breakpoint-action.md)」を参照してください。  
  
#### <a name="to-specify-a-hit-count"></a>ヒット カウントを指定するには  
  
1.  エディター ウィンドウで、ブレークポイント グリフを右クリックし、ショートカット メニューの **[ヒット カウント]** をクリックします。  
  
     または  
  
     **[ブレークポイント]** ウィンドウで、ブレークポイント グリフを右クリックし、ショートカット メニューの **[ヒット カウント]** をクリックします。  
  
2.  **[ブレークポイントのヒット カウント]** ダイアログ ボックスで、 **[ブレークポイントをヒットした時]** ボックスから目的の動作を選択します。  
  
     **[常に中断]** 以外の設定を選択すると、一覧の右側にテキスト ボックスが表示されます。 テキスト ボックスに整数を入力して、目的のヒット カウントを指定します。  
  
3.  **[OK]** をクリックして変更を適用するか、 **[キャンセル]** をクリックして変更を適用せずに終了します。  
  
#### <a name="to-view-or-reset-the-current-hit-count"></a>現在のヒット カウントを表示またはリセットするには  
  
1.  エディター ウィンドウで、ブレークポイント グリフを右クリックし、ショートカット メニューの **[ヒット カウント]** をクリックします。  
  
     または  
  
     **[ブレークポイント]** ウィンドウで、ブレークポイント グリフを右クリックし、ショートカット メニューの **[ヒット カウント]** をクリックします。  
  
2.  **[ブレークポイントのヒット カウント]** ダイアログ ボックスの **[リセット]** ボタンのすぐ上に、 **[現在のヒット カウント]** が表示されます。  
  
3.  現在のヒット カウントを 0 に設定する場合は、 **[リセット]** をクリックします。  
  
4.  **[OK]** または **[キャンセル]** をクリックして、ダイアログ ボックスを終了します。  
  
## <a name="see-also"></a>参照  
 [ブレークポイント条件の指定](specify-a-breakpoint-condition.md)  
  
  
