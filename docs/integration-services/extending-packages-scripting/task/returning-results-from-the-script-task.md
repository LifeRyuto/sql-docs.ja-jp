---
title: スクリプト タスクから結果を返す | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], status information
- ExecutionValue property
- status information [Integration Services]
- TaskResult property
- SSIS Script task, status information
ms.assetid: ac06805b-c2db-44bd-af5c-5a0debe36dd7
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: b5db80c310c7810123d5702b729a227ebe891527
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/20/2019
ms.locfileid: "58290838"
---
# <a name="returning-results-from-the-script-task"></a>スクリプト タスクから結果を返す
  スクリプト タスクは <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A> プロパティと、オプションの <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> プロパティを使用して、スクリプト タスクの完了後にワークフローのパスを決定するために使用できるステータス情報を [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] ランタイムに返します。  
  
## <a name="taskresult"></a>TaskResult  
 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A> プロパティは、タスクが成功したか失敗したかを報告します。 例 :  
  
 `Dts.TaskResult = ScriptResults.Success`  
  
## <a name="executionvalue"></a>ExecutionValue  
 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> プロパティは、必要に応じて、スクリプト タスクの成功または失敗の回数を示す、またはそれに関する詳細情報を提供するユーザー定義オブジェクトを返します。 たとえば、FTP タスクは、<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> プロパティを使用して、転送されたファイル数を返します。 SQL 実行タスクは、タスクによって処理された行数を返します。 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> は、ワークフローのパスを決定するときにも使用できます。 例 :  
  
 `Dim rowsAffected as Integer`  
  
 `...`  
  
 `rowsAffected = 1000`  
  
 `Dts.ExecutionValue = rowsAffected`  
