---
title: '[パーティション処理変換先エディター] ([詳細設定] ページ)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.partprocessingtransformation.advanced.f1
helpviewer_keywords:
- Partition Processing Destination Editor
ms.assetid: 2039ee0f-069d-479d-90b2-2a12481b1162
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: de7c84a463d15e3260cc64c53ba1f82c6808dd93
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66056774"
---
# <a name="partition-processing-destination-editor-advanced-page"></a>[パーティション処理変換先エディター] ([詳細設定] ページ)
  
  **[パーティション処理変換先エディター]** ダイアログ ボックスの **[詳細設定]** ページを使用すると、エラー処理を設定できます。  
  
 パーティション処理変換先の詳細については、「 [Partition Processing Destination](data-flow/partition-processing-destination.md)」を参照してください。  
  
> [!NOTE]  
>  ここで説明されているタスクは、Analysis Services テーブル モデルには適用されません。  テーブル モデルで入力列をパーティション列にマップすることはできません。 代わりに Analysis Services DDL 実行タスク [Analysis Services Execute DDL Task](control-flow/analysis-services-execute-ddl-task.md) を使用してパーティションを処理することができます。  
  
## <a name="options"></a>オプション  
 **既定のエラー構成を使用します。**  
 既定の [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] エラー処理を使用するかどうかを指定します。 この値の既定値は `True` です。  
  
 **キーエラーアクション**  
 許容されないキー値を持つレコードを処理する方法を指定します。  
  
|値|[説明]|  
|-----------|-----------------|  
|**ConvertToUnknown**|不正なキー値を不明な値に変換します。|  
|**DiscardRecord**|レコードを破棄します。|  
  
 **エラーを無視する**  
 エラーを無視することを指定します。  
  
 **エラー時に停止**  
 エラーが発生した場合に処理を停止することを指定します。  
  
 **エラーの数**  
 
  **[エラー時に停止する]** を選択した場合は、処理を停止するエラーのしきい値を指定します。  
  
 **エラー時のアクション**  
 
  **[エラー時に停止する]** を選択した場合は、エラーのしきい値に達した場合に実行する操作を指定します。  
  
|値|[説明]|  
|-----------|-----------------|  
|**StopProcessing**|処理を停止します。|  
|**StopLogging**|ログ記録エラーを停止します。|  
  
 **キーが見つかりません**  
 見つからないキーのエラーに対する操作を指定します。 既定では、この値は **[ReportAndContinue]** です。  
  
|値|[説明]|  
|-----------|-----------------|  
|**IgnoreError**|エラーを無視して処理を続行します。|  
|**ReportAndContinue**|エラーを報告して処理を続行します。|  
|**ReportAndStop**|エラーを報告して処理を停止します。|  
  
 **重複するキー**  
 重複キーのエラーに対する操作を指定します。 既定では、この値は **IgnoreError**です。  
  
|値|[説明]|  
|-----------|-----------------|  
|**IgnoreError**|エラーを無視して処理を続行します。|  
|**ReportAndContinue**|エラーを報告して処理を続行します。|  
|**ReportAndStop**|エラーを報告して処理を停止します。|  
  
 **Null キーが不明な値に変換されました**  
 NULL キーが不明な値に変換された場合に実行する操作を指定します。 既定では、この値は **IgnoreError**です。  
  
|値|[説明]|  
|-----------|-----------------|  
|**IgnoreError**|エラーを無視して処理を続行します。|  
|**ReportAndContinue**|エラーを報告して処理を続行します。|  
|**ReportAndStop**|エラーを報告して処理を停止します。|  
  
 **Null キーは使用できません**  
 NULL キーが許可されていない場合に NULL キーが検出されたときに実行する操作を指定します。 既定では、この値は **[ReportAndContinue]** です。  
  
|値|[説明]|  
|-----------|-----------------|  
|**IgnoreError**|エラーを無視して処理を続行します。|  
|**ReportAndContinue**|エラーを報告して処理を続行します。|  
|**ReportAndStop**|エラーを報告して処理を停止します。|  
  
 **エラーログのパス**  
 エラー ログのパスを入力するか、 **(...)** 参照ボタンを使用してログの保存先を選択します。  
  
 **参照 (...)**  
 エラー ログのパスを選択します。  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーとメッセージの参照](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [[パーティション処理変換先エディター &#40;マッピング] ページ&#41;](../../2014/integration-services/partition-processing-destination-editor-mappings-page.md)  
  
  
