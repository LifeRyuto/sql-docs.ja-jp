---
title: ログのプロパティ |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- QueryLogFileSize property
- QueryLogTableName property
- TraceBackgroundDistributionPeriod property
- TraceMaxRowsetSize property
- NullKeyConvertedToUnknown property
- CrashReportsFolder property
- TraceDefinitionFile property
- SQLDumperFlagsOn property
- KeyErrorLimit property
- SnapshotDefinitionFile property
- MinidumpErrorList property
- ErrorLogFileName property
- KeyDuplicate property
- IgnoreDataTruncation property
- logs [Analysis Services]
- Enabled property
- FileSizeMB property
- TraceFileWriteTrailerPeriod property
- TraceQueryResponseTextChunkSize property
- File property
- FileBufferSize property
- TraceRowsetBackgroundFlushPeriod property
- ErrorLogFileSize property
- TraceRequestParameters property
- KeyErrorLimitAction property
- CreateQueryLogTable property
- LogDir property
- TraceBackgroundFlushPeriod property
- TraceFileBufferSize property
- SQLDumperFlagsOff property
- QueryLogConnectionString property
- KeyNotFound property
- KeyErrorLogFile property
- TraceReportFQDN property
- KeyErrorAction property
- QueryLogFileName property
- MessageLogs property
- MiniDumpFlagsOn property
- SnapshotFrequencySec property
- QueryLogSampling property
- CreateAndSendCrashReports property
- LogDurationSec property
ms.assetid: 33fd90ee-cead-48f0-8ff9-9b458994c766
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 81653d9b93a7dc8ec71a88e70cee8b2d68f33a8e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66068916"
---
# <a name="log-properties"></a>ログのプロパティ
  
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、次の表に示すログ サーバー プロパティがサポートされています。 その他のサーバー プロパティとその設定方法の詳細については、「 [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md)」を参照してください。  
  
## <a name="general"></a>全般  
 `File`  
 サーバーのログ ファイルの名前を識別する文字列プロパティです。 このプロパティは、データベース テーブル (既定の動作) ではなく、ディスク ファイルがログ記録に使用される場合にのみ適用されます。  
  
 このプロパティの既定値は msmdsrv.log です。  
  
 `FileBufferSize`  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 `MessageLogs`  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
## <a name="error-log"></a>エラー ログ  
 次のプロパティをサーバー インスタンス レベルで設定し、他のツールとデザイナーに表示されるエラーの構成の既定値を変更できます。 詳細については、「 [SSAS-多次元&#41;の &#40;キューブ、パーティション、およびディメンションの処理のエラー構成](../multidimensional-models/error-configuration-for-cube-partition-and-dimension-processing.md)」を<xref:Microsoft.AnalysisServices.MiningStructure.ErrorConfiguration%2A>参照してください。  
  
 **ErrorLog\ErrorLogFileName**  
 サーバーによる処理操作の実行時に既定値として使用されるプロパティです。  
  
 **Errorlog\ errorlogのサイズ**  
 サーバーによる処理操作の実行時に既定値として使用されるプロパティです。  
  
 **Errorlog\ keyerroraction**  
 
  `KeyNotFound` エラーが発生した場合に、サーバーが実行するアクションを指定します。 このエラーへの有効な応答は次のとおりです。  
  
-   
  `ConvertToUnknown` は、不明なメンバーにエラーのキー値を割り当てるようにサーバーに指示します。  
  
-   
  `DiscardRecord` は、レコードを除外するようにサーバーに指示します。  
  
 **Errorlog\ keyerrorlogfile**  
 サービス アカウントが読み取り/書き込み権限を持つフォルダーにある、.log ファイル拡張子を持つ必要があるユーザー定義のファイル名です。 このログ ファイルには、処理中に生成されたエラーのみが含まれます。 詳細情報が必要な場合はフライト レコーダーを使用します。  
  
 **Errorlog\ keyerrorlimit**  
 処理が失敗するまでにサーバーが許可するデータ整合性エラーの最大数です。 値が 1 の場合は、数に制限がないことを示します。 既定値は 0 です。これは、最初のエラーが発生した後に処理が停止することを意味します。 整数に設定することもできます。  
  
 **Errorlog\ keyerrorlimitaction**  
 キー エラー数が上限に達した場合にサーバーが実行するアクションを指定します。 このアクションへの有効な応答は次のとおりです。  
  
-   
  `StopProcessing` は、エラーの上限に到達した場合に処理を停止するようにサーバーに指示します。  
  
-   
  `StopLogging` は、エラーの上限に到達した場合にエラーの記録を停止するものの、処理を継続するようにサーバーに指示します。  
  
 **エラーログ \ LogErrorTypes\KeyNotFound**  
 
  `KeyNotFound` エラーが発生した場合に、サーバーが実行するアクションを指定します。 このエラーへの有効な応答は次のとおりです。  
  
-   
  `IgnoreError` は、エラーを記録せずに処理を継続するか、キー エラーの上限に達するまでカウントするようにサーバーに指示します。 エラーを無視すると、エラー カウントに追加したり画面またはログ ファイルに記録することなく、処理を継続します。 レコードにデータの整合性の問題があり、データベースに追加できません。 レコードは、`KeyErrorAction` プロパティで指定されているとおりに、破棄されるか、不明なメンバーに集計されます。  
  
-   
  `ReportAndContinue` は、エラーを記録して、キー エラーの上限に達するまでカウントし、処理を継続するようにサーバーに指示します。 エラーをトリガーするレコードは、破棄されるか、不明メンバーに変換されます。  
  
-   
  `ReportAndStop` は、エラーを記録し、キー エラーの上限に関係なく処理を直ちに停止するようにサーバーに指示します。 エラーをトリガーするレコードは、破棄されるか、不明メンバーに変換されます。  
  
 **エラーログ \ Logerrortyp/keyduplicate**  
 重複したキーが見つかった場合に、サーバーが実行するアクションを指定します。 有効な値は、エラーが発生しなかったかのように処理を継続する `IgnoreError`、エラーを記録して処理を継続する `ReportAndContinue`、エラー数がエラーの上限に達していなくてもエラーを記録して直ちに処理を停止する `ReportAndStop` です。  
  
 **エラーログ \ LogErrorTypes\NullKeyConvertedToUnknown**  
 NULL キーが不明なメンバーに変換された場合にサーバーが実行する操作を指定します。 有効な値は、エラーが発生しなかったかのように処理を継続する `IgnoreError`、エラーを記録して処理を継続する `ReportAndContinue`、エラー数がエラーの上限に達していなくてもエラーを記録して直ちに処理を停止する `ReportAndStop` です。  
  
 **エラーログ \ logerrorタイプ \N ullkeynotallowed**  
 
  `NullProcessing` がディメンション属性の `Error` に設定されている場合にサーバーが実行するアクションを指定します。 エラーは、指定された属性で NULL 値が許可されていない場合に生成されます。 このエラー構成プロパティは、次の手順を通知します。つまり、エラーを報告してエラーの上限に達するまで処理を継続します。 有効な値は、エラーが発生しなかったかのように処理を継続する `IgnoreError`、エラーを記録して処理を継続する `ReportAndContinue`、エラー数がエラーの上限に達していなくてもエラーを記録して直ちに処理を停止する `ReportAndStop` です。  
  
 **エラーログ \ Logerrortyp/電卓 ationerror**  
 サーバーによる処理操作の実行時に既定値として使用されるプロパティです。  
  
 **Errorlog/ignoredatatrunて**  
 サーバーによる処理操作の実行時に既定値として使用されるプロパティです。  
  
## <a name="exception"></a>Exception  
 **Exception\CreateAndSendCrashReports**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **Exception\CrashReportsFolder**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **Exception\SQLDumperFlagsOn**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **Exception\SQLDumperFlagsOff**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **Exception\MiniDumpFlagsOn**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **Exception\MinidumpErrorList**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
## <a name="flight-recorder"></a>Flight Recorder  
 **FlightRecorder\Enabled**  
 フライト レコーダー機能が有効かどうかを示すブール型プロパティです。  
  
 **FlightRecorder\FileSizeMB**  
 フライト レコーダーのディスク ファイルのサイズを MB 単位で定義する、符号付き 32 ビット整数のプロパティです。  
  
 **FlightRecorder\LogDurationSec**  
 フライト レコーダーがロール オーバーされる頻度を秒単位で定義する、符号付き 32 ビット整数のプロパティです。  
  
 **FlightRecorder\SnapshotDefinitionFile**  
 スナップショット定義ファイルの名前を定義する文字列プロパティです。このファイルには、スナップショットの取得時にサーバーに発行される検出コマンドが含まれています。  
  
 このプロパティの既定値は空白です。その場合、既定で使用されるファイル名は FlightRecorderSnapshotDef.xml になります。  
  
 **FlightRecorder\SnapshotFrequencySec**  
 スナップショットの頻度を秒単位で定義する、符号付き 32 ビット整数のプロパティです。  
  
 **FlightRecorder\TraceDefinitionFile**  
 フライト レコーダーのトレース定義ファイルの名前を指定する文字列プロパティです。  
  
 このプロパティの既定値は空白です。その場合、既定で使用されるファイル名は FlightRecorderTraceDef.xml になります。  
  
## <a name="query-log"></a>クエリ ログ  
 **適用対象:** 多次元サーバーモードのみ  
  
 **QueryLog\QueryLogFileName**  
 クエリ ログ ファイルの名前を指定する文字列プロパティです。 このプロパティは、データベース テーブル (既定の動作) ではなく、ディスク ファイルがログ記録に使用される場合にのみ適用されます。  
  
 **Querylog\ querylogサンプリング**  
 クエリ ログのサンプリング レートを指定する、符号付き 32 ビット整数のプロパティです。  
  
 このプロパティの既定値は 10 であり、10 回のサーバー クエリごとに 1 回がログ記録されることを意味します。  
  
 **Querylog\ querylogのサイズ**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **Querylog\ querylogconnectionstring**  
 クエリ ログ データベースへの接続を指定する文字列プロパティです。  
  
 **Querylog\ querylogtablename**  
 クエリ ログ テーブルの名前を指定する文字列プロパティです。  
  
 このプロパティの既定値は OlapQueryLog です。  
  
 **Querylog\ createquerylogtable**  
 クエリ ログ テーブルを作成するかどうかを指定するブール型プロパティです。  
  
 このプロパティの既定値は False であり、サーバーによってログ テーブルが自動的に作成されず、クエリ イベントがログ記録されないことを示します。  
  
> [!NOTE]  
>  クエリログの構成の詳細については、「 [Analysis Services のログ操作](../instances/log-operations-in-analysis-services.md)」を参照してください。  
  
## <a name="trace"></a>Trace  
 **トレース/tracebackgroundの時間**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **Tracebackgroundflushperiod**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **Tracefilebuffersize**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **Trace\TraceFileWriteTrailerPeriod**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **Trace\TraceMaxRowsetSize**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **Traceprotocoltraffic**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **Tracequeryendersetextchunksize**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **Traceereportfqdn**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **Trace\TraceRequestParameters**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **Trace\TraceRowsetBackgroundFlushPeriod**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
## <a name="see-also"></a>参照  
 [Analysis Services でのサーバープロパティの構成](server-properties-in-analysis-services.md)   
 [Analysis Services インスタンスのサーバーモードの決定](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
