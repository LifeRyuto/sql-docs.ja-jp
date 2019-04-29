---
title: コマンド ウィンドウ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Command Window [Transact-SQL]
ms.assetid: e567ebf9-0793-451b-92c7-26193a02d9da
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 481ed4b4c1667017a5677ee734cff153128eff32
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62718039"
---
# <a name="command-window"></a>[コマンド] ウィンドウ
  **[コマンド]** ウィンドウを使用すると、現在デバッグ中の[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] クエリ エディター ウィンドウのコードに対してデバッグ コマンドや編集コマンドなどのコマンドを実行できます。 **[コマンド]** ウィンドウを使用するには、デバッグ モードである必要があります。  [!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **[コマンド]** ウィンドウでもサポートされているコマンドの多くをサポートしています。 詳細については、 [Visual Studio のコマンド ウィンドウに関するページ](https://go.microsoft.com/fwlink/?LinkId=112007)を参照してください。  
  
## <a name="task-list"></a>タスク一覧  
 **[コマンド] ウィンドウにアクセスするには**  
  
-   **[デバッグ]** メニューの **[デバッグの開始]** をクリックします。  
  
 **変数の値を出力するには**  
  
-   **[コマンド] ウィンドウ**で、「**Debug.Print \<変数名>**」と入力し、Enter キーを押します。  
  
 **現在のスレッドに関する情報を一覧表示するには**  
  
-   **コマンド**、型`Debug.ListThread`、し、ENTER キーを押します。  
  
 **[クイック ウォッチ] ウィンドウに変数を追加するには**  
  
-   **[コマンド] ウィンドウ**で、「**Debug.QuickWatch \<変数名>**」と入力し、Enter キーを押します。  
  
## <a name="see-also"></a>参照  
 [Transact-SQL デバッガー](transact-sql-debugger.md)  
