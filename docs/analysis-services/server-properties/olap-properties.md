---
title: Analysis Services OLAP のプロパティ |Microsoft Docs
ms.date: 03/15/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8e2643488710548b3a773730e9b9898125783dc3
ms.sourcegitcommit: 671370ec2d49ed0159a418b9c9ac56acf43249ad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2019
ms.locfileid: "58072346"
---
# <a name="olap-properties"></a>OLAP のプロパティ
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、次の表に示す OLAP サーバー プロパティがサポートされています。 その他のサーバー プロパティとその設定方法の詳細については、「 [Analysis Services のサーバー プロパティ](../../analysis-services/server-properties/server-properties-in-analysis-services.md)」を参照してください。  
  
 **適用対象:** 多次元サーバー モードの場合のみ  
  
## <a name="memory"></a>Memory  
 **DefaultPageSizeForData**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **DefaultPageSizeForDataHeader**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **DefaultPageSizeForIndex**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **DefaultPageSizeForIndexHeader**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **DefaultPageSizeForString**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **DefaultPageSizeForHash**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **DefaultPageSizeForProp**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
## <a name="lazyprocessing"></a>LazyProcessing  
 **Enabled**  
 レイジー集計処理が有効かどうかを示すブール型プロパティです。  
  
 **SleepIntervalSecs**  
 保留中のレイジー処理ジョブがあるかどうかをサーバーが確認する間隔を秒単位で定義する、符号付き 32 ビット整数のプロパティです。  
  
 **MaxCPUUsage**  
 レイジー処理の最大 CPU 使用量を比率として定義する、符号付き 64 ビット倍精度浮動小数点数のプロパティです。 サーバーは、スナップショットに基づいて平均 CPU 使用量を監視します。 CPU が瞬間的にこのしきい値を超えるのは正常な動作です。  
  
 このプロパティの既定値は 0.5 であり、CPU の最大 50% がレイジー処理に充てられることを示します。  
  
 **MaxObjectsInParallel**  
 並列レイジー処理を実行できるパーティションの最大数を指定する、符号付き 32 ビット整数のプロパティです。  
  
 **MaxRetries**  
 レイジー処理が失敗した場合にエラーが発生する前にイベントでの再試行の回数を定義する、符号付き 32 ビット整数のプロパティです。  
  
## <a name="processplan"></a>ProcessPlan  
 **CacheRowsetRows**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **CacheRowsetToDisk**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **DistinctBuffer**  
 個別のカウントに使用される内部バッファーのサイズを定義する、符号付き 32 ビット整数のプロパティです。 メモリ使用量を犠牲にして個別のカウントの処理を高速化するには、この値を大きくします。  
  
 **EnableRolapDimQueryTableGrouping**  
 テーブルのグループ化が ROLAP ディメンションに対して有効かどうかを指定するブール型プロパティです。 True の場合、実行時に ROLAP ディメンションをクエリすると、属性ごとに別々にクエリされるのではなく、ROLAP ディメンション テーブル全体が一度にクエリされます。  
  
 **EnableTableGrouping**  
 テーブルのグループ化が有効かどうかを指定するブール型プロパティです。 True の場合、ディメンションを処理すると、属性ごとに別々にクエリされるのではなく、ディメンション テーブル全体が一度にクエリされます。  
  
 **ForceMultiPass**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **MaxTableDepth**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **MemoryAdjustConst**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **MemoryAdjustFactor**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **MemoryLimit**  
 処理に充てるメモリの最大量を定義する、符号付き 64 ビット倍精度浮動小数点数のプロパティです。物理メモリの比率として表されます。  
  
 このプロパティの既定値は 65 であり、物理メモリの最大 65% がキューブおよびディメンションの処理に充てられることを示します。  
  
 **MemoryLimitErrorEnabled**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **OptimizeSchema**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
## <a name="proactivecaching"></a>ProactiveCaching  
 **DefaultRefreshInterval**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **DimensionLatencyAccuracy**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **PartitionLatencyAccuracy**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
## <a name="process"></a>Process  
 **AggregationMemoryLimitMax**  
 集計処理に充てることができるメモリの最大量を定義する、符号付き 64 ビット倍精度浮動小数点数のプロパティです。物理メモリの比率として表されます。  
  
 このプロパティの既定値は 80 であり、物理メモリの最大 80% が集計処理に充てられることを示します。  
  
 **AggregationMemoryLimitMin**  
 集計処理に充てることができるメモリの最小量を定義する、符号付き 64 ビット倍精度浮動小数点数のプロパティです。物理メモリの比率として表されます。 値を大きくすると、メモリ使用量を犠牲にして集計処理を高速化できます。  
  
 このプロパティの既定値は 10 であり、物理メモリの最小 10% が集計処理に充てられることを示します。  
  
 **AggregationNewAlgo**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **AggregationPerfLog2**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **AggregationsBuildEnabled**  
 集計の作成が有効かどうかを指定するブール型プロパティです。 これは、集計のデザインを変更することなく集計の作成のベンチマークを行うメカニズムです。  
  
 **BufferMemoryLimit**  
 処理バッファー メモリの制限を定義する、符号付き 64 ビット倍精度浮動小数点数のプロパティです。物理メモリの比率として表されます。  
  
 このプロパティの既定値は 60 であり、物理メモリの最大 60% がバッファー メモリに使用されることを示します。  
  
 **BufferRecordLimit**  
 処理時にバッファーできるレコードの数を定義する、符号付き 32 ビット整数のプロパティです。  
  
 このプロパティの既定値は 1048576 (レコード) です。  
  
 **CacheRecordLimit**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **CheckDistinctRecordSortOrder**  
 パーティションの処理時に個別のカウント クエリの結果の並べ替え順に意味があるかどうかを定義するブール型プロパティです。 True の場合、並べ替え順に意味はなく、サーバーによる "確認" が必要であることを示します。 個別のカウント メジャーを使用してパーティションを処理すると、クエリは並べ替え順に従って SQL に送信されます。 処理を高速化するには False に設定してください。  
  
 このプロパティの既定値は True であり、並べ替え順に意味がなく、確認が必要であることを示します。  
  
 **DatabaseConnectionPoolConnectTimeout**  
 新しい接続を開くときのタイムアウトを秒単位で指定する、符号付き 32 ビット整数のプロパティです。  
  
 **DatabaseConnectionPoolGeneralTimeout**  
 外部 OLEDB 接続で使用するデータベース接続タイムアウトを秒単位で指定する、符号付き 32 ビット整数のプロパティです。  
  
 **DatabaseConnectionPoolMax**  
 プールされるデータベース接続の最大数を指定する、符号付き 32 ビット整数のプロパティです。  
  
 このプロパティの既定値は 50 (接続) です。  
  
 **DatabaseConnectionPoolTimeout**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **DataFileInitEnabled**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **DataPlacementOptimization**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **DataSliceInitEnabled**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **DeepCompressValue**  
 数値を圧縮して有効桁数を少なくすることができるかどうかを指定する、Double データ型のメジャーに適用されるブール型プロパティです。 値が False の場合は、圧縮が行われず、有効桁数は少なくならないことを示します。  
  
 このプロパティの既定値は True であり、圧縮が有効で、有効桁数が少なくなることを示します。  
  
 **DimensionPropertyKeyCache**  
 ディメンション プロパティ キーがキャッシュされるかどうかを指定するブール型プロパティです。 キーが一意でない場合は、True に設定する必要があります。  
  
 **IndexBuildEnabled**  
 処理時にインデックスが作成されるかどうかを指定するブール型プロパティです。 このプロパティは、ベンチマークおよび情報提供を目的としています。  
  
 **IndexBuildThreshold**  
 パーティションに対してインデックスが作成されなくなる下限の行数しきい値を指定する、符号付き 32 ビット整数のプロパティです。  
  
 このプロパティの既定値は 4096 (行) です。  
  
 **IndexFileInitEnabled**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **MapFormatMask**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **RecordsReportGranularity**  
 処理時にサーバーがトレース イベントを記録する頻度を行単位で指定する、符号付き 32 ビット整数のプロパティです。  
  
 このプロパティの既定値は 1000 であり、1,000 行ごとにトレース イベントがログ記録されることを示します。  
  
 **ROLAPDimensionProcessingEffort**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
## <a name="query"></a>Query  
 **AggregationsUseEnabled**  
 保存されている集計が実行時に使用されるかどうかを定義するブール型プロパティです。 このプロパティでは、情報提供およびベンチマークの目的で、集計のデザインを変更したり再処理したりせずに集計を無効にすることができます。  
  
 このプロパティの既定値は True であり、集計が有効であることを示します。  
  
 **AllowSEFiltering**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **CalculationCacheRegistryMaxIterations**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **CalculationEvaluationPolicy**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **ConvertDeletedToUnknown**  
 削除されたディメンション メンバーが不明なメンバーに変換されるかどうかを指定するブール型プロパティです。  
  
 **CopyLinkedDataCacheAndRegistry**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **DataCacheRegistryMaxIterations**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **DefaultDrillthroughMaxRows**  
 ドリルスルー クエリから返される行の最大数を指定する、符号付き 32 ビット整数のプロパティです。  
  
 このプロパティの既定値は 10000 (行) です。  
  
 **DimensionPropertyCacheSize**  
 クエリで使用するディメンション メンバーをキャッシュするために使用されるメモリ量 (バイト単位) を指定する、符号付き 32 ビット整数のプロパティです。  
  
 既定値は、属性階層ごと、およびアクティブなクエリごとに 4,000,000 バイト (4 MB) です。 既定値は、一般的な階層を持つソリューションにとってバランスのとれたキャッシュ サイズを指定します。 ただし、非常に多くのメンバー (数百万単位) を持つディメンションや多層構造のディメンションの場合は、この値を大きくするとパフォーマンスが向上します。  
  
 キャッシュ サイズを大きくする場合の暗黙的な影響:  
  
-   ディメンション キャッシュでより多くのメモリを使用できるようにすると、メモリ使用率のコストが増加します。 実際の使用率は、実行されるクエリによって異なります。 すべてのクエリが、許容される最大量のメモリを使用するわけではありません。  
  
     これらのキャッシュによって使用されるメモリは縮小不能と見なされ、 **[TotalMemoryLimit]** を計算するときはその中に含まれることに注意してください。  
  
-   サーバー上のすべてのデータベースに影響します。 **DimensionPropertyCachesize** は、サーバー全体のプロパティです。 このプロパティを変更すると、現在のインスタンスで実行されているすべてのデータベースに影響を与えます。  
  
ディメンション キャッシュの要件を推定する方法:  
  
1.  最初はサイズを大幅に増やして、ディメンション キャッシュのサイズを増やしたときに利点が得られるかどうかを判断します。 たとえば、最初のステップとして既定値を倍にすることが考えられます。  
  
2.  パフォーマンスが向上することが明らかになった場合は、パフォーマンスとメモリ使用率の間で適切なバランスに達するまで、値を徐々に小さくします。  


 **ExpressNonEmptyUseEnabled**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **IgnoreNullRolapRows**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **IndexUseEnabled**  
 インデックスが実行時に使用されるかどうかを定義するブール型プロパティです。 このプロパティは、情報提供およびベンチマークを目的としています。  
  
 **MapHandleAlgorithm**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **MaxRolapOrConditions**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
 
 **RowsetSerializationLimit**   
 Azure Analysis Services に適用されます。 行セットをクライアントに返される行の数を制限します。 既定値は-1、適用は無制限を意味します。 DAX と MDX の両方のクエリに適用されます。 広範なデータのエクスポートからサーバー リソースを保護するために使用します。 サーバーに送信された制限を超えるクエリが取り消され、エラーが返されます。  

 **UseCalculationCacheRegistry**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **UseDataCacheFreeLastPageMemory**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **UseDataCacheRegistry**  
 データ キャッシュ レジストリを有効にするかどうかを指定するブール型プロパティです。ここでは、計算された結果ではなく、クエリ結果がキャッシュされます。  
  
 **UseDataCacheRegistryHashTable**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **UseDataCacheRegistryMultiplyKey**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **UseDataSlice**  
 クエリ最適化の実行時にパーティション データ スライスを使用するかどうかを定義するブール型プロパティです。 このプロパティは、ベンチマークおよび情報提供を目的としています。  
  
 **UseMaterializedIterators**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **UseSinglePassForDimSecurityAutoExist**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **UseVBANet**  
 ユーザー定義関数に VBA .net アセンブリを使用するかどうかを定義するブール型プロパティです。  
  
 **CalculationPrefetchLocality\ ApplyIntersect**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **CalculationPrefetchLocality\ ApplySubtract**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **CalculationPrefetchLocality\ PrefetchLowerGranularities**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **DataCache\  CachedPageAlloc\ Income**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **DataCache\  CachedPageAlloc\ InitialBonus**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **DataCache\  CachedPageAlloc\ MaximumBalance**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **DataCache\  CachedPageAlloc\ MinimumBalance**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **DataCache\  CachedPageAlloc\ Tax**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **DataCache\CellStore\ Income**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **DataCache\CellStore\ InitialBonus**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **DataCache\CellStore\ MaximumBalance**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **DataCache\CellStore\ MinimumBalance**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **DataCache\CellStore\ Tax**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **DataCache\ MemoryModel \ Income**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **DataCache\ MemoryModel \ InitialBonus**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **DataCache\ MemoryModel \ MaximumBalance**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **DataCache\ MemoryModel \ MinimumBalance**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **DataCache\ MemoryModel\ Tax**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
## <a name="jobs"></a>Jobs  
 **ProcessAggregation\ MemoryModel\ Income**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **ProcessAggregation\ MemoryModel\ InitialBonus**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **ProcessAggregation\ MemoryModel\ MaximumBalance**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **ProcessAggregation\ MemoryModel\ MinimumBalance**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **ProcessAggregation\ MemoryModel\ Tax**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **ProcessAggregation\ ProcessPartition\ Income**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **ProcessAggregation\ ProcessPartition \ InitialBonus**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **ProcessAggregation\ ProcessPartition \ MaximumBalance**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **ProcessAggregation\ ProcessPartition \ MinimumBalance**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **ProcessAggregation\ ProcessPartition \ Tax**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **ProcessAggregation\ ProcessProperty\ Income**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **ProcessAggregation\ ProcessProperty\ InitialBonus**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **ProcessAggregation\ ProcessProperty\ MaximumBalance**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **ProcessAggregation\ ProcessProperty\ MinimumBalance**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **ProcessAggregation\ ProcessProperty\ Tax**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
## <a name="see-also"></a>参照  
 [Analysis Services のサーバー プロパティ](../../analysis-services/server-properties/server-properties-in-analysis-services.md)   
 [Analysis Services インスタンスのサーバー モードの決定](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
