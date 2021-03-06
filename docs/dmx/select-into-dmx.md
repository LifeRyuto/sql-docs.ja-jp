---
title: SELECT INTO (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: a2e9fb0dfd3607adc1773d4a43561f32ba650ee5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68887680"
---
# <a name="select-into-dmx"></a>SELECT INTO (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  既存のマイニングモデルのマイニング構造に基づいて構築された新しいマイニングモデルを作成します。 **SELECT INTO**ステートメントでは、スキーマや実際のアルゴリズムに固有ではないその他の情報をコピーすることによって、新しいマイニングモデルを作成します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SELECT INTO <new model>   
USING <algorithm> [(<parameter list>)] [WITH DRILLTHROUGH[,] [FILTER(<expression>)]]  
FROM <existing model>  
```  
  
## <a name="arguments"></a>引数  
 *new model*  
 作成される新しいモデルの一意の名前。  
  
 *アルゴリズム*  
 プロバイダーによって定義された、データ マイニング アルゴリズムの名前です。  
  
 *パラメーターリスト*  
 省略可能。 アルゴリズムに対してプロバイダーが定義したパラメーターのコンマ区切りのリスト。  
  
 *条件*  
 トレーニングデータの有効なフィルター条件に評価される式。 フィルターとして使用できる式の詳細については、「 [Analysis Services データマイニング&#41;&#40;マイニングモデルのフィルター ](https://docs.microsoft.com/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining)」を参照してください。  
  
 *既存のモデル*  
 コピーする既存のモデルの名前。  
  
## <a name="remarks"></a>解説  
 既存のモデルがトレーニングされている場合は、このステートメントの実行時に新しいモデルが自動的に処理されます。 学習済みではない場合、新しいモデルは処理されないままとなります。  
  
 **SELECT INTO**ステートメントは、既存のモデルの構造が新しいモデルのアルゴリズムと互換性がある場合にのみ機能します。 このため、このステートメントは、同じアルゴリズムに基づくモデルを迅速に作成およびテストする場合に最も役立ちます。 アルゴリズムの種類を変更する場合、新しいアルゴリズムでは、既存のモデル内の各列のデータ型をサポートする必要があります。または、モデルの処理時にエラーが発生する可能性があります。  
  
 **WITH ドリルスルー**句を使用すると、新しいマイニングモデルでドリルスルーを実行できます。 ドリルスルーは、モデルの作成時にのみ可能です。  
  
## <a name="example-1-altering-the-parameters-of-the-model"></a>例 1: モデルのパラメーターを変更する  
 次の例では、 `TM_Clustering`「[基本的なデータマイニングチュートリアル](https://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c)」で作成した既存のマイニングモデルに基づいて、新しいマイニングモデルを作成します。 新しいモデルでは、CLUSTER_COUNT パラメーターが変更され、最大5つのクラスターが新しいモデルに存在するようになりました。 これに対して、既存のモデルでは既定値 10 が使用されています。  
  
```  
SELECT * INTO [New_Clustering]  
USING [Microsoft_Clustering] (CLUSTER_COUNT = 5)   
FROM [TM Clustering]  
```  
  
## <a name="example-2-adding-a-filter-to-the-model"></a>例 2: モデルへのフィルターの追加  
 次の例では、既存のマイニングモデルに基づいて新しいマイニングモデルを作成し、そのモデルにフィルターを追加します。 フィルターは、トレーニング データを特定の地域に住んでいる顧客だけに制限します。  
  
```  
SELECT * INTO [Clustering Europe Region]  
USING [Microsoft_Clustering] WITH FILTER(Region='Europe')  
FROM [TM Clustering]  
```  
  
> [!NOTE]  
>  ケース テーブルに適用されるフィルターは、この例に示すように、SELECT INTO ステートメントを使用して変更できます。ただし、入れ子になったテーブルに対するフィルターが元のモデルに含まれている場合、入れ子になったテーブルのフィルターは、この構文を使用しても変更または削除することができず、元のモデルからそのままコピーされます。 入れ子になったテーブルに別のフィルターを使用しているモデルを作成するには、ALTER STRTUCTURE...ADD MODEL 構文を使用します。  
  
## <a name="see-also"></a>参照  
 [DMX&#41; データ定義ステートメント &#40;のデータマイニング拡張機能](../dmx/dmx-statements-data-definition.md)   
 [DMX&#41; データ操作ステートメントを &#40;データマイニング拡張機能](../dmx/dmx-statements-data-manipulation.md)   
 [DMX&#41; ステートメントリファレンス &#40;データマイニング拡張機能](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
