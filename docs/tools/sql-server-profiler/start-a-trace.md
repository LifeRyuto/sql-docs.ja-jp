---
title: トレースの開始 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Profiler, stopping traces
- pausing traces
- Profiler [SQL Server Profiler], stopping traces
- Profiler [SQL Server Profiler], starting traces
- traces [SQL Server], starting
- SQL Server Profiler, pausing traces
- traces [SQL Server], stopping
- Profiler [SQL Server Profiler], pausing traces
- traces [SQL Server], pausing
- SQL Server Profiler, starting traces
- stopping traces
- starting traces
ms.assetid: aeeb38eb-229a-4c8b-ad66-57e9ce45fb6a
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 1d27aeff0582edf59c2bc02a94172a4194fab8f1
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67729694"
---
# <a name="start-a-trace"></a>トレースの開始
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用して新しいトレース定義するか、テンプレートを作成したら、新しいトレース定義またはテンプレートを使用してデータのキャプチャを開始、一時停止、または停止することができます。  
  
## <a name="starting-a-trace"></a>トレースの開始  
 定義されているトレース元が [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] または [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスである場合、トレースを開始すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] により、キャプチャしたサーバー イベントを一時的に保持する場所を提供するキューが作成されます。  
  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を使用して SQL トレースにアクセスすると、トレース ウィンドウが表示されていない場合、トレースの開始時に新しいトレース ウィンドウが表示され、データがすぐにキャプチャされます。  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] システム ストアド プロシージャを使用して SQL トレースにアクセスする際には、データをキャプチャする [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスが起動されるたびにトレースを開始する必要があります。 トレースの開始後に変更できるのはトレースの名前のみです。  
  
> [!NOTE]  
>  既存のトレースを使用する場合、プロパティを参照できますが、変更できません。 プロパティを変更するには、トレースを停止または一時停止する必要があります。  
  
## <a name="see-also"></a>参照  
 [サーバーへの接続後の自動的なトレースの開始 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/start-a-trace-automatically-after-connecting-to-a-server-sql-server-profiler.md)   
 [トレースの一時停止 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/pause-a-trace-sql-server-profiler.md)   
 [トレースの停止 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/stop-a-trace-sql-server-profiler.md)   
 [トレース ウィンドウの消去 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/clear-a-trace-window-sql-server-profiler.md)   
 [一時停止または停止したトレースの再開 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/run-a-trace-after-it-has-been-paused-or-stopped-sql-server-profiler.md)  
  
  
