---
title: モデリング フラグ (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 01be0e2d0ead01a3b6c630e0ddd0f53e55620104
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68008320"
---
# <a name="modeling-flags-dmx"></a>モデリング フラグ (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  モデリング フラグを使用する[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]データ マイニング アルゴリズムには、ケース テーブルで定義されているデータに関する追加の情報を提供します。 アルゴリズムは、この情報を使用して、より正確なデータ マイニング モデルを作成することができます。 モデリング フラグは、マイニング構造列およびマイニング モデル列のいずれに対しても定義できます。  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 次のモデリング フラグをサポートしています。  
  
 **NOT NULL**  
 この属性列の値は NULL 値を含むことはありません。 モデルの学習プロセス中に、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] がこの属性列に NULL 値を検出した場合、エラーが発生します。 このフラグはマイニング構造列で定義されます。  
  
 **REGRESSOR**  
 アルゴリズムが、指定した列を回帰アルゴリズムの回帰式に使用できることを示します。 このフラグは、[!INCLUDE[msCoName](../includes/msconame-md.md)] Linear Regression および [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees アルゴリズムによってサポートされており、マイニング モデル列で定義されます。  
  
 **MODEL_EXISTENCE_ONLY**  
 この属性列の値は、属性の有無ほど重要ではありません。 このフラグはマイニング モデル列で定義されます。  
  
 サード パーティのアルゴリズムによっては、別のモデリング フラグもサポートしている場合があります。 アルゴリズムがどのモデリング フラグを確認するには、サポートを使用して、 **SUPPORTED_MODELING_FLAGS**スキーマ行セット。 また、サーバーのマイニング サービスに対してクエリを実行し、特定のアルゴリズムでサポートされているモデリング フラグを判別することもできます。 たとえば、次のクエリでは、現在のサーバー上の Microsoft 線形回帰アルゴリズムでサポートされているモデリング フラグが返されます。  
  
```  
SELECT SUPPORTED_MODELING_FLAGS  
FROM $SYSTEM.DMSCHEMA_MINING_SERVICES  
WHERE SERVICE_NAME = 'Microsoft_Linear_Regression'  
```  
  
 期待される結果:  
  
 NOT NULL、REGRESSOR  
  
## <a name="specifying-modeling-flags-on-a-mining-model"></a>マイニング モデルでのモデリング フラグの指定  
 構文の例についてを[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]、マイニング構造列でフラグを指定するためのサポートを参照してください[CREATE MINING STRUCTURE &#40;DMX&#41;](../dmx/create-mining-structure-dmx.md)します。  
  
 マイニング モデル列にモデリング フラグを指定する構文の例は、次を参照してください。 [ALTER MINING STRUCTURE &#40;DMX&#41;](../dmx/alter-mining-structure-dmx.md)します。  
  
 マイニング モデル列の使用の詳細については、次を参照してください。[マイニング モデル列](../analysis-services/data-mining/mining-model-columns.md)します。  
  
## <a name="see-also"></a>参照  
 [データ マイニング アルゴリズム &#40;Analysis Services - データ マイニング&#41;](../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [データ マイニング拡張機能 &#40;DMX&#41; リファレンス](../dmx/data-mining-extensions-dmx-reference.md)   
 [データ マイニング拡張機能&#40;DMX&#41;構文要素](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [データ マイニング拡張機能&#40;DMX&#41;関数リファレンス](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [データ マイニング拡張機能&#40;DMX&#41;演算子リファレンス](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [データ マイニング拡張機能&#40;DMX&#41;ステートメント リファレンス](../dmx/data-mining-extensions-dmx-statements.md)   
 [データ マイニング拡張機能&#40;DMX&#41;構文表記規則](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [一般的な予測関数&#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)   
 [構造と DMX 予測クエリの使用](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [DMX 選択ステートメントについて](../dmx/understanding-the-dmx-select-statement.md)  
  
  
