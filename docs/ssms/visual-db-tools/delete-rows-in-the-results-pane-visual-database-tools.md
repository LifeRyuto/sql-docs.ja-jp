---
title: 結果ペイン内の行の削除 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- View Designer, Results pane
- removing rows
- row removal [SQL Server], Visual Database Tools Results pane
- row deletions [SQL Server], Visual Database Tools Results pane
- Query Designer [SQL Server], Results pane
- deleting rows
- Results pane
ms.assetid: a1147905-fe4a-4fac-b576-a17622477e66
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 63f480358f0f6fffea0e63c4c2ff06a3993eee73
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/06/2019
ms.locfileid: "65105790"
---
# <a name="delete-rows-in-the-results-pane-visual-database-tools"></a>結果ペイン内の行の削除 (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
データベース内のレコードを削除するには、結果ペイン内の行を削除します。 すべての行を削除する場合、削除クエリを使用できます。 詳細については、「 [削除クエリの作成 (Visual Database Tools)](../../ssms/visual-db-tools/create-delete-queries-visual-database-tools.md)」を参照してください。 結果ペインからの行の削除だけを行う場合は、クエリの条件を変更します。 詳細については、「 [検索基準の指定 (Visual Database Tools)](../../ssms/visual-db-tools/specify-search-criteria-visual-database-tools.md)」を参照してください。  
  
### <a name="to-delete-a-row-or-rows"></a>1 行または複数の行を削除するには  
  
1.  結果ペイン内で、削除する行の左側にあるボックスを選択します。  
  
2.  Del キーを押します。  
  
3.  確認を要求するメッセージ ボックスで、 **[はい]** をクリックします。  
  
> [!CAUTION]  
> この方法で削除した行は、データベースから完全に削除され、再度呼び出すことはできません。  
  
> [!NOTE]  
> 選択した行をデータベースから削除できない場合、行の削除は行われず、削除できない行を通知するメッセージが表示されます。  
  
## <a name="see-also"></a>参照  
[削除クエリの作成 (Visual Database Tools)](../../ssms/visual-db-tools/create-delete-queries-visual-database-tools.md)  
[検索基準の指定 (Visual Database Tools)](../../ssms/visual-db-tools/specify-search-criteria-visual-database-tools.md)  
  
