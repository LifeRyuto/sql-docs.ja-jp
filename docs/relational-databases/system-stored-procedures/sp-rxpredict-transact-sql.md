---
title: sp_rxPredict |Microsoft Docs
ms.date: 07/24/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: machine-learning
ms.topic: language-reference
f1_keywords:
- sp_rxPredict
- sp_rxPredict_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_rxPredict procedure
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 9cd9bb481ec54f9d99c80aba54241827c2a118cf
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68471071"
---
# <a name="sprxpredict"></a>sp_rxPredict  
[!INCLUDE[tsql-appliesto-ss-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss-xxxx-xxxx-xxx-md.md)]

SQL Server データベースにバイナリ形式で格納されている機械学習モデルで構成される、指定された入力の予測値を生成します。

R と Python の機械学習モデルのスコア付けをほぼリアルタイムで提供します。 `sp_rxPredict`は、 `rxPredict` [RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler)と[microsoft ml](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package)の R 関数のラッパーとして提供されているストアドプロシージャであり、 [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package)および[microsoft ml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package)の[rx_predict](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict) Python 関数のためのものです。 これは、でC++記述され、スコアリング操作専用に最適化されています。

モデルは R または Python を使用して作成する必要がありますが、シリアル化され、ターゲットデータベースエンジンインスタンスでバイナリ形式で格納されると、R または Python の統合がインストールされていない場合でも、そのデータベースエンジンのインスタンスから使用できます。 詳細については、「 [sp_rxPredict を使用したリアルタイムスコアリング](https://docs.microsoft.com/sql/advanced-analytics/real-time-scoring)」を参照してください。

## <a name="syntax"></a>構文

```
sp_rxPredict  ( @model, @input )
```

### <a name="arguments"></a>引数

**model**

サポートされている形式の事前トレーニング済みモデル。 

**input**

有効な SQL クエリ

### <a name="return-values"></a>戻り値

スコア列、および入力データソースのすべてのパススルー列が返されます。
アルゴリズムがそのような値の生成をサポートしている場合は、信頼区間などの追加のスコア列を返すことができます。

## <a name="remarks"></a>コメント

ストアドプロシージャを使用できるようにするには、インスタンスで SQLCLR が有効になっている必要があります。

> [!NOTE]
> このオプションの enabing には、セキュリティ上の影響があります。 サーバーで SQLCLR が有効になっていない場合は、 [TRANSACT-SQL PREDICT](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql?view=sql-server-2017)関数などの代替の実装を使用します。

ユーザーは、 `EXECUTE`データベースに対する権限が必要です。

### <a name="supported-algorithms"></a>サポートされているアルゴリズム

モデルを作成してトレーニングするには、R または Python のサポートされているアルゴリズムのいずれかを使用します。 [SQL Server 2016 r Services](https://docs.microsoft.com/sql/advanced-analytics/r/sql-server-r-services?view=sql-server-2017)、 [SQL Server 2016 r Server (スタンドアロン)](https://docs.microsoft.com/sql/advanced-analytics/r/r-server-standalone?view=sql-server-2016)、 [SQL Server 2017 Machine Learning Services (R または Python)](https://docs.microsoft.com//sql/advanced-analytics/what-is-sql-server-machine-learning?view=sql-server-2017)、または[SQL Server 2017 によって提供されます。サーバー (スタンドアロン) (R または Python)](https://docs.microsoft.com/sql/advanced-analytics/r/r-server-standalone?view=sql-server-2017)。

#### <a name="r-revoscaler-models"></a>\R\N\R\NRevoScaleR モデル

  + [rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod)
  + [rxLogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit)
  + [rxBTrees](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxbtrees)
  + [rxDtree](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdtree)
  + [rxdForest](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdforest)

#### <a name="r-microsoftml-models"></a>\R\N\R\NMicrosoft Ml モデル

  + [rxFastTrees](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees)
  + [rxFastForest](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastforest)
  + [rxLogisticRegression](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxlogisticregression)
  + [rxOneClassSvm](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxoneclasssvm)
  + [rxNeuralNet](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet)
  + [rxFastLinear](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastlinear)

#### <a name="r-transformations-supplied-by-microsoftml"></a>\R\N\R\NMicrosoft Ml によって提供される変換

  + [featurizeText](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees)
  + [concat](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/concat)
  + [categorical](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categorical)
  + [categoricalHash](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categoricalHash)
  + [selectFeatures](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/selectFeatures)

#### <a name="python-revoscalepy-models"></a>Python: revoscalepy モデル

  + [rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod)
  + [rx_logit](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-logit)
  + [rx_btrees](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-btrees)
  + [rx_dtree](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dtree)
  + [rx_dforest](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dforest)


#### <a name="python-microsoftml-models"></a>Python: microsoft ml モデル

  + [rx_fast_trees](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-trees)
  + [rx_fast_forest](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-forest)
  + [rx_logistic_regression](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-logistic-regression)
  + [rx_oneclass_svm](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-oneclass-svm)
  + [rx_neural_network](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-neural-network)
  + [rx_fast_linear](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-linear)

#### <a name="python-transformations-supplied-by-microsoftml"></a>PythonMicrosoft ml によって提供される変換

  + [featurize_text](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-trees)
  + [concat](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/concat)
  + [categorical](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/categorical)
  + [categorical_hash](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/categorical-hash)
  
### <a name="unsupported-model-types"></a>サポートされていないモデルの種類

次の種類のモデルはサポートされていません。

+ RevoScaleR のアルゴリズム`rxGlm`また`rxNaiveBayes`はアルゴリズムを使用するモデル
+ R の PMML モデル
+ 他のサードパーティライブラリを使用して作成されたモデル 

## <a name="examples"></a>使用例

```sql
DECLARE @model = SELECT @model 
FROM model_table 
WHERE model_name = 'rxLogit trained';

EXEC sp_rxPredict @model = @model,
@inputData = N'SELECT * FROM data';
```

の *@inputData* 入力データには、有効な SQL クエリに加えて、格納されているモデルの列と互換性のある列が含まれている必要があります。

`sp_rxPredict`でサポートされている .NET 列の型は、double、float、short、ushort、long、ulong、および string のみです。 リアルタイムスコアリングに使用する前に、入力データでサポートされていない型を除外することが必要になる場合があります。 

  対応する SQL 型の詳細については、「 [sql-Clr 型のマッピング](/dotnet/framework/data/adonet/sql/linq/sql-clr-type-mapping)」または「 [clr パラメーターデータのマッピング](../clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md)」を参照してください。

