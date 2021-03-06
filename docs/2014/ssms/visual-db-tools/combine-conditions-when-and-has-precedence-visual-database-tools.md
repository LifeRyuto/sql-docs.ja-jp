---
title: AND が優先する場合の条件を結合する (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- search conditions [SQL Server], combining
- precedence [SQL Server], Criteria pane
- search criteria [SQL Server], combining conditions
- combining search conditions
- AND, Criteria pane
ms.assetid: 450eb2eb-6ea3-405b-8dd2-1ff926c016e7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4d0a0bcb7115255c3c6b3750cd930e7d06b9e2df
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63225807"
---
# <a name="combine-conditions-when-and-has-precedence-visual-database-tools"></a>AND が優先する場合の条件を結合する (Visual Database Tools)
  AND で条件を結合するには、クエリに対して列を 2 回 (各条件について 1 回ずつ) 追加します。 OR で条件を結合するには、[フィルター] 列で最初の条件を指定し、次の条件を **[または...]** 列で指定します。  
  
 たとえば、初級レベルの仕事に従事している勤続 5 年以上の従業員、または入社日に関係なく中級レベルの仕事に従事している従業員を検索するとします。 このクエリには、3 つの条件が必要であり、その中の 2 つの条件を AND で結合する必要があります。  
  
-   入社日が 5 年以上前で、かつ職務レベルが 100 の従業員  
  
     または  
  
-   職務レベルが 200 の従業員  
  
### <a name="to-combine-conditions-when-and-has-precedence"></a>AND が優先する場合に条件を結合するには  
  
1.  [抽出条件ペイン](visual-database-tools.md)に検索するデータ列を追加します。 AND で結合された複数の条件を使用して同じ列を検索する場合は、検索する値ごとにデータ列名をグリッドに追加する必要があります。  
  
2.  
  **[フィルター]** 列に、AND で結合する条件をすべて入力します。 たとえば、 `hire_date` 列の条件と `job_lvl` 列の条件を AND で結合して検索するには、対応する [フィルター] 列にそれぞれ `< '1/1/91'` および `= 100`と入力します。  
  
     上のようにグリッドに値を入力すると、 [SQL ペイン](sql-pane-visual-database-tools.md)でステートメントの WHERE 句が次のように作成されます。  
  
    ```  
    WHERE (hire_date < '01/01/91') AND  
      (job_lvl = 100)  
    ```  
  
3.  
  **[または...]** グリッド列に OR で結合する条件を入力します。 たとえば、 `job_lvl` 列の別の値を検索条件として追加するには、 **[または...]** 列に `= 200`などの値を追加入力します。  
  
     
  **[または...]** 列に値を追加すると、SQL ペインでは次のようにステートメントの WHERE 句に条件が追加されます。  
  
    ```  
    WHERE (hire_date < '01/01/91' ) AND  
      (job_lvl = 100) OR   
      (job_lvl = 200)  
    ```  
  
## <a name="see-also"></a>参照  
 [Visual Database Tools &#40;またはが優先される場合に条件を結合&#41;](combine-conditions-when-or-has-precedence-visual-database-tools.md)   
 [抽出条件ペインで検索条件を組み合わせる場合の規則 &#40;Visual Database Tools&#41;](conventions-combine-search-conditions-in-criteria-pane-visual-db-tools.md)   
 [Visual Database Tools &#40;検索値を入力するための規則&#41;](rules-for-entering-search-values-visual-database-tools.md)   
 [検索基準の指定 (Visual Database Tools)](specify-search-criteria-visual-database-tools.md)  
  
  
