---
title: マイニング モデル (DMX) の作成 |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0e7ca6765ee44201badc54d15fb2a20aa9a863a5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62853472"
---
# <a name="create-mining-model-dmx"></a>CREATE MINING MODEL (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  新しいマイニング モデルとマイニング構造の両方をデータベースに作成します。 モデルを作成するには、新しいモデルをステートメントで定義するか、Predictive Model Markup Language (PMML) を使用します。 後者については、詳しい知識のあるユーザーのみ使用してください。  
  
 マイニング構造には、モデル名の後に「_structure」を追加した名前を付けます。これにより、構造名がモデル名から一意であることが保証されます。  
  
 既存のマイニング構造のマイニング モデルを作成するには、使用、 [ALTER MINING STRUCTURE &#40;DMX&#41; ](../dmx/alter-mining-structure-dmx.md)ステートメント。  
  
## <a name="syntax"></a>構文  
  
```  
  
CREATE [SESSION] MINING MODEL <model>  
(  
    [(<column definition list>)]  
)  
USING <algorithm> [(<parameter list>)] [WITH DRILLTHROUGH]  
CREATE MINING MODEL <model> FROM PMML <xml string>  
```  
  
## <a name="arguments"></a>引数  
 *model*  
 モデルの一意の名前です。  
  
 *列定義リスト*  
 列定義のコンマ区切りのリストです。  
  
 *algorithm*  
 現在のプロバイダーによって定義された、データ マイニング アルゴリズムの名前です。  
  
> [!NOTE]  
>  使用して現在のプロバイダーでサポートされているアルゴリズムの一覧を取得できる[DMSCHEMA_MINING_SERVICES 行セット](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-services-rowset)します。 現在のインスタンスでサポートされているアルゴリズムを表示する[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]を参照してください[データ マイニング プロパティ](../analysis-services/server-properties/data-mining-properties.md)します。  
  
 *パラメーター リスト*  
 任意。 アルゴリズムのプロバイダー定義パラメーターのコンマ区切りのリストです。  
  
 *XML 文字列*  
 (詳しい知識のあるユーザーのみ。)XML でエンコードされたモデル (PMML) です。 文字列を示すには必ず単一引用符 (') を使用してください。  
  
 **セッション**句では、接続が終了またはセッションがタイムアウトになるときに、サーバーから自動的に削除されるマイニング モデルを作成することができます。**セッション**マイニング モデルは、するには、データベース管理者、ユーザーは必要ありませんし、接続が開いている限りのみディスク容量を使用するので便利です。  
  
 **WITH DRILLTHROUGH**句は、新しいマイニング モデルでドリルスルーを使用します。 ドリルスルーは、モデルの作成時にのみ可能です。 モデルの種類によっては、カスタム ビューアーでモデルを参照するためにドリルスルーが必要な場合があります。 Microsoft 汎用コンテンツ ツリー ビューアーを使用してモデルを予測または参照する場合は、ドリルスルーは必要ありません。  
  
 **CREATE MINING MODEL**ステートメントは、列定義の一覧、アルゴリズム、およびアルゴリズム パラメーターのリストに基づく新しいマイニング モデルを作成します。  
  
### <a name="column-definition-list"></a>列定義リスト  
 列定義の一覧を使用するモデルの構造を定義するには、次の情報を各列に含めます。  
  
-   名前 (必須)  
  
-   データ型 (必須)  
  
-   Distribution  
  
-   モデリング フラグの一覧  
  
-   コンテンツの種類 (必須)  
  
-   示される予測の要求は、この列を予測するためのアルゴリズムを示す、 **PREDICT**または**PREDICT_ONLY**句  
  
-   によって示される属性列 (適用される場合にのみ必須)、リレーションシップ、 **RELATED TO**句  
  
 1 つの列を定義するのにには、列定義リストの次の構文を使用します。  
  
```  
<column name>    <data type>    [<Distribution>]    [<Modeling Flags>]    <Content Type>    [<prediction>]    [<column relationship>]   
```  
  
 入れ子になったテーブル列を定義するのにには、列定義リストの次の構文を使用します。  
  
```  
<column name>    TABLE    [<prediction>] ( <non-table column definition list> )  
```  
  
 モデリング フラグを除き、特定のグループから句を 1 つだけ使用して列を定義します。 列には複数のモデリング フラグを定義できます。  
  
 構造列の定義に使用できる、データ型、コンテンツの種類、列分布、モデリング フラグのリストについては、次のトピックを参照してください。  
  
-   [データ型 (データ マイニング)](../analysis-services/data-mining/data-types-data-mining.md)  
  
-   [コンテンツの種類 (データ マイニング)](../analysis-services/data-mining/content-types-data-mining.md)  
  
-   [列の分布 (データ マイニング)](../analysis-services/data-mining/column-distributions-data-mining.md)  
  
-   [モデリング フラグ (データ マイニング)](../analysis-services/data-mining/modeling-flags-data-mining.md)  
  
 ステートメントに句を追加して、2 つの列間のリレーションシップを記述できます。 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 次の使用をサポートする\<Column relationship > 句。  
  
 **関連するには**  
 この形式は値の階層を示します。 RELATED TO 列の対象にすることが可能なのは、入れ子になったテーブル内のキー列、ケース行内の不連続値の列、RELATED TO 句のある別の列です。これにより、より深い階層が示されます。  
  
 予測列の使用方法を説明するには、予測句を使用します。 次の表は、使用できる 2 つの句について示しています。  
  
|\<予測 > 句|説明|  
|---------------------------|-----------------|  
|**PREDICT**|この列は、モデルによって予測が可能で、入力ケースで指定されることで、その他の予測可能列の値を予測することができます。|  
|**PREDICT_ONLY**|この列は、モデルによって予測が可能ですが、その他の予測可能列の値を予測するためにこの列の値を入力ケースで使用することはできません。|  
  
### <a name="parameter-definition-list"></a>パラメーター定義リスト  
 マイニング モデルのパフォーマンスおよび機能を調整するには、パラメーターの一覧を使用します。 パラメーター リストの構文は次のとおりです。  
  
```  
[<parameter> = <value>, <parameter> = <value>,...]  
```  
  
 各アルゴリズムに関連付けられているパラメーターの一覧は、次を参照してください。[データ マイニング アルゴリズム&#40;Analysis Services - データ マイニング&#41;](../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)します。  
  
## <a name="remarks"></a>コメント  
 組み込みのテスト データセットを持つモデルを作成する場合は、CREATE MINING STRUCTURE ステートメントの後に ALTER MINING STRUCTURE ステートメントを使用します。 ただし、すべての種類のモデルで予約データセットがサポートされるわけではありません。 詳細については、「[CREATE MINING STRUCTURE &#40;DMX&#41;](../dmx/create-mining-structure-dmx.md)」を参照してください。  
  
 CREATEMODEL ステートメントを使用してマイニング モデルを作成する方法のチュートリアルは、次を参照してください。[時系列予測の DMX チュートリアル](https://msdn.microsoft.com/library/38ea7c03-4754-4e71-896a-f68cc2c98ce2)します。  
  
## <a name="naive-bayes-example"></a>Naive Bayes の例  
 次の例では、[!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes アルゴリズムを使用して、新しいマイニング モデルを作成しています。 Bike Buyer の列は、予測可能属性として定義されています。  
  
```  
CREATE MINING MODEL [NBSample]  
(  
    CustomerKey LONG KEY,   
    Gender TEXT DISCRETE,  
    [Number Cars Owned] LONG DISCRETE,  
    [Bike Buyer] LONG DISCRETE PREDICT  
)  
USING Microsoft_Naive_Bayes  
```  
  
## <a name="association-model-example"></a>結合モデルの例  
 次の例では、[!INCLUDE[msCoName](../includes/msconame-md.md)] 結合アルゴリズムを使用して、新しいマイニング モデルを作成しています。 このステートメントは、テーブル列を使用することで、モデル定義内でテーブルを入れ子にする機能を利用しています。 モデルを使用して、変更、 *MINIMUM_PROBABILITY*と*MINIMUM_SUPPORT*パラメーター。  
  
```  
CREATE MINING MODEL MyAssociationModel (  
    OrderNumber TEXT KEY,  
    [Products] TABLE PREDICT (  
        [Model] TEXT KEY  
    )  
)  
USING Microsoft_Association_Rules (Minimum_Probability = 0.1, MINIMUM_SUPPORT = 0.01)  
```  
  
## <a name="sequence-clustering-example"></a>シーケンス クラスタリングの例  
 次の例では、[!INCLUDE[msCoName](../includes/msconame-md.md)] シーケンス クラスタリング アルゴリズムを使用して、新しいマイニング モデルを作成しています。 2 つのキーを使用してモデルを定義しています。 OrderNumber 列は、ケース キーとして使用され、個々の注文を指定します。 LineNumber 列は、入れ子になったテーブルのキーとして使用され、注文が追加されたアイテムのシーケンスを指定します。  
  
```  
CREATE MINING MODEL BuyingSequence (  
    [Order Number] TEXT KEY,  
    [Products] TABLE   
     (  
        [Line Number] LONG KEY SEQUENCE,  
        [Model] TEXT DISCRETE PREDICT  
    )  
)  
USING Microsoft_Sequence_Clustering  
```  
  
## <a name="time-series-example"></a>時系列の例  
 次の例では、[!INCLUDE[msCoName](../includes/msconame-md.md)] タイム シリーズ アルゴリズムで、ARTxp アルゴリズムを使用して新しいマイニング モデルを作成しています。 ReportingDate は時系列のキー列で、ModelRegion はデータ系列のキー列です。 この例では、データの周期を 12 か月としています。 そのため、 *PERIODICITY_HINT*パラメーター 12 に設定されます。  
  
> [!NOTE]  
>  指定する必要があります、 *PERIODICITY_HINT*中かっこ文字を使用してパラメーター。 さらに、値は文字列であるため、囲む必要があります単一引用符で:"{\<数値 >}"。  
  
```  
CREATE MINING MODEL SalesForecast (  
        ReportingDate DATE KEY TIME,  
        ModelRegion TEXT KEY,  
        Amount LONG CONTINUOUS PREDICT,  
        Quantity LONG CONTINUOUS PREDICT  
)  
USING Microsoft_Time_Series (PERIODICITY_HINT = '{12}', FORECAST_METHOD = 'ARTXP')  
```  
  
## <a name="see-also"></a>参照  
 [データ マイニング拡張機能&#40;DMX&#41;データ定義ステートメント](../dmx/dmx-statements-data-definition.md)   
 [データ マイニング拡張機能&#40;DMX&#41;データ操作ステートメント](../dmx/dmx-statements-data-manipulation.md)   
 [データ マイニング拡張機能 &#40;DMX&#41; ステートメント リファレンス](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
