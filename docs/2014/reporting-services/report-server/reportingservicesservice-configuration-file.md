---
title: ReportingServicesService 構成ファイル | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- traces [Reporting Services]
- Report Server Windows service, ReportingServicesService configuration file
- ReportingServicesService configuration file
ms.assetid: 40f4a401-cb61-4c42-b1ec-01acdacdacd1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9fb4893304a17be264a0d5bdcb8add2732c7c271
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66103277"
---
# <a name="reportingservicesservice-configuration-file"></a>ReportingServicesService 構成ファイル
  ReportingServicesService.exe.config ファイルには、トレースを構成する設定が含まれています。  
  
## <a name="file-location"></a>ファイルの場所  
 このファイルは、\Reporting Services\Report Server\Bin フォルダーにあります。  
  
## <a name="editing-guidelines"></a>編集のガイドライン  
 このファイルを変更して、ログ ファイル名を変更したり、トレース レベルを増減させることができます。 その他の設定は変更しないでください。 手順については、「[Reporting Services の構成ファイル &#40;RSreportserver.config&#41; の変更](modify-a-reporting-services-configuration-file-rsreportserver-config.md)」を参照してください。 トレース ログの詳細については、「 [Report Server Service Trace Log](report-server-service-trace-log.md)」を参照してください。  
  
## <a name="example-configuration"></a>構成の例  
 ReportingServicesService.exe.config ファイルにある設定および既定値の例を次に示します。  
  
```  
<configSections>  
      <section name="RStrace" type="Microsoft.ReportingServices.Diagnostics.RSTraceSectionHandler,Microsoft.ReportingServices.Diagnostics" />  
</configSections>  
<system.diagnostics>  
      <switches>  
          <add name="DefaultTraceSwitch" value="3" />  
      </switches>  
</system.diagnostics>  
<RStrace>  
      <add name="FileName" value="ReportServerService_" />  
      <add name="FileSizeLimitMb" value="32" />  
      <add name="KeepFilesForDays" value="14" />  
      <add name="Prefix" value="tid, time" />  
      <add name="TraceListeners" value="debugwindow, file" />  
      <add name="TraceFileMode" value="unique" />  
      <add name="Components" value="all" />  
</RStrace>  
<runtime>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
             <dependentAssembly>  
                    <assemblyIdentity name="Microsoft.ReportingServices.Interfaces"  
                        publicKeyToken="89845dcd8080cc91"  
                        culture="neutral" />  
                    <bindingRedirect oldVersion="8.0.242.0"  
                                     newVersion="10.0.0.0"/>  
                    <bindingRedirect oldVersion="9.0.242.0"  
                                     newVersion="10.0.0.0"/>  
             </dependentAssembly>  
      </assemblyBinding>  
      <gcServer enabled="true" />  
</runtime>  
```  
  
## <a name="configuration-settings"></a>構成設定  
 次の表では、特定の設定に関する情報を示します。 構成ファイルに出現する順に、設定を示します。  
  
|設定|[説明]|  
|-------------|-----------------|  
|**RStrace**|エラーおよびトレースに使用される名前空間を指定します。|  
|**DefaultTraceSwitch**|ReportServerService トレース ログにレポートされる情報のレベルを指定します。 各レベルには、そのレベルより低いすべてのレベルでレポートされる情報が含まれます。 トレースを無効にすることはお勧めしません。 有効な値は、次のとおりです。<br /><br /> 0= トレースの無効化<br /><br /> 1= 例外および再起動<br /><br /> 2= 例外、再起動、警告<br /><br /> 3= 例外、再起動、警告、状態メッセージ (既定)<br /><br /> 4= 詳細モード|  
|**/Db**|ログ ファイル名の最初の部分を指定します。 
  `Prefix` で指定した値が付加されて、完全な名前になります。 既定では、この名前は ReportServerService_ です。|  
|**FileSizeLimitMb**|トレース ログのサイズの上限を指定します。 ファイルは MB 単位で測定されます。 正しい値は、0 から整数型の最大値までです。 既定値は 32 です。|  
|**KeepFilesForDays**|トレース ログ ファイルを削除するまでの保持期間を日数で指定します。 正しい値は、0 から整数型の最大値までです。 既定値は 14 です。|  
|`Prefix`|あるログのインスタンスを別のログのインスタンスと区別するために生成する値を指定します。 既定では、トレース ログ ファイル名にタイムスタンプの値が追加されます。 この値は、" tid, time " に設定されます。 この設定は変更しないでください。|  
|**TraceListeners**|トレース ログ コンテンツの出力先を指定します。 複数の出力先を指定する場合、各出力先をコンマで区切ってください。 有効な値は、次のとおりです。<br /><br /> DebugWindow (既定値)<br /><br /> File (既定値)<br /><br /> StdOut|  
|**TraceFileMode**|トレース ログに 24 時間データを含めるかどうかを指定します。 コンポーネントごとに、毎日 1 つ、一意のトレース ログが必要です。 この値は、"Unique (既定値)" に設定されます。 この値は変更しないでください。|  
|**Components**|トレース ログを作成するコンポーネントを指定します。 既定値は `all` です。 この設定に対する他の有効な値には、内部コンポーネントの名前があります。 この値は変更しないでください。|  
|**ランタイム**|以前のバージョンとの下位互換性をサポートする構成設定を指定します。 Microsoft.ReportingServices.Interfaces の以前のバージョンを対象とする要求を新しいバージョンにリダイレクトするには、Runtime 設定を使用します。<br /><br /> このセクションの構成設定は、すべて [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] の製品ドキュメントで説明されています。 詳細については、MSDN Web サイトまたは [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] ドキュメントの「ランタイム設定スキーマ」を参照してください。|  
  
## <a name="see-also"></a>参照  
 [Reporting Services 構成ファイル](reporting-services-configuration-files.md)   
 [Report Server Service Trace Log](report-server-service-trace-log.md)  
  
  
