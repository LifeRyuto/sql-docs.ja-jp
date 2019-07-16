---
title: MDX (MDX) でのサブキューブの構築 |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7bf6396ebe7cfe18aa7d1005d39095a35713e10b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68208799"
---
# <a name="building-subcubes-in-mdx-mdx"></a>MDX でのサブキューブの作成 (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  サブキューブは、基になるデータにフィルターを適用したビューを表す、キューブのサブセットです。 キューブをサブキューブに限定することによって、クエリのパフォーマンスを向上させることができます。  
  
 サブキューブを定義するには、このトピックで説明されている [CREATE SUBCUBE](../../../mdx/mdx-data-definition-create-subcube.md) ステートメントを使用します。  
  
## <a name="create-subcube-syntax"></a>CREATE SUBCUBE の構文  
 サブキューブを作成するための構文は、以下のとおりです。  
  
```  
CREATE SUBCUBE Subcube_Identifier AS Subcube_Expression  
```  
  
 CREATE SUBCUBE の構文は非常に単純です。 *Subcube_Identifier* パラメーターは、サブキューブの基になるキューブを識別します。 *Subcube_Expression* パラメーターでは、サブキューブにするキューブの部分を選択します。  
  
 サブキューブを作成すると、そのサブキューブは、セッションが閉じるまで、あるいは [DROP SUBCUBE](../../../mdx/mdx-data-definition-drop-subcube.md) ステートメントを実行するまですべての MDX クエリのコンテキストになります。  
  
### <a name="what-a-subcube-contains"></a>サブキューブの内容  
 CREATE SUBCUBE ステートメントの使用法は単純ですが、サブキューブに含まれるすべてのメンバーがステートメント自体で明示的に指定されるわけではありません。 サブキューブを定義する場合には、以下の規則が適用されます。  
  
-   ある階層の **(All)** メンバーを含める場合、その階層のすべてのメンバーが含まれます。  
  
-   任意のメンバーを含める場合、そのメンバーの先祖と子孫も含まれます。  
  
-   あるレベルの各メンバーを含める場合、階層のすべてのメンバーが含まれます。 他の階層のメンバーは、そのレベルのメンバーと共に存在していない場合 (たとえば、顧客を含まない都市のような不均衡階層など)、除外されます。  
  
-   サブキューブには、キューブの各 **(All)** メンバーが常に含まれます。  
  
 さらに、サブキューブ内の集計値は視覚的に合計されます。 たとえば、 `USA`、 `WA`、 `OR`を含むサブキューブがあるとします。 サブキューブによって定義されている州は `USA` と `{WA,OR}` だけなので、 `WA` の集計値は `OR` の合計になります。 他の州は無視されます。  
  
 また、サブキューブの外部にあるセルへの明示的な参照を行うと、キューブ全体のコンテキストで評価されるセル値が返されます。 たとえば、今年度に限定したサブキューブを作成するとします。 この場合、 [ParallelPeriod](../../../mdx/parallelperiod-mdx.md) 関数を使用して今年度を前年度と比較することができます。 前年度の値が、サブキューブの外部にある場合でも、値の差が返されます。  
  
 さらに、元のコンテキストを上書きしない場合、サブセレクト内で評価されるセット関数は、サブセレクトのコンテキストで評価されます。 コンテキストを上書きする場合、セット関数はキューブ全体のコンテキストで評価されます。  
  
## <a name="create-subcube-example"></a>CREATE SUBCUBE の例  
 以下の例では、Budget キューブを 4200 と 4300 のアカウントに限定するサブキューブを作成しています。  
  
 `CREATE SUBCUBE Budget AS SELECT {[Account].[Account].&[4200], [Account].[Account].&[4300] } ON 0 FROM Budget`  
  
 セッションに対するサブキューブが作成されるので、以降のクエリは、キューブ全体ではなくサブキューブに対して実行されます。 たとえば、次のクエリを実行します。 このクエリでは、アカウント 4200 と 4300 のメンバーだけが返されます。  
  
 `SELECT [Account].[Account].Members ON 0, Measures.Members ON 1 FROM Budget`  
  
## <a name="see-also"></a>関連項目  
 [クエリ内のキューブ コンテキストの確立 (MDX)](../../../analysis-services/multidimensional-models/mdx/establishing-cube-context-in-a-query-mdx.md)   
 [MDX クエリの基礎 (Analysis Services)](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  
