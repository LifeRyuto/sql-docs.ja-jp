---
title: SQLSetParam のマッピング |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLSetParam
- SQLSetParam function [ODBC], mapping
ms.assetid: 022dfbc0-8d18-4c35-8a28-d9eb16063188
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c5d420bc68c4704705018a37c6459181481b1d7d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63297473"
---
# <a name="sqlsetparam-mapping"></a>SQLSetParam のマッピング
**SQLSetParam**の上にマップするのには引き続き**SQLBindParameter** ODBC 2 のようにします *。x*します。 概念的に似ていますが、にもかかわらず**SQLBindParam**、ドライバー マネージャーがマップされていない**SQLSetParam**に**SQLBindParam**します。 これは、ため特定既存の ODBC 2。*x*ドライバーの特殊な値を使用して、 *BufferLength* (SQL_SETPARAM_VALUE_MAX) に割り当てるときに、ドライバー マネージャーが生成する**SQLSetParam**の上に**SQLBindParameter** 1 で呼び出されたときを判断する *。x* ODBC アプリケーション。  
  
 呼び出し  
  
```  
SQLSetParam(hstmt, ipar, fCType, fSqlType, cbColDef, ibScale, rgbValue, pcbValue)  
```  
  
 次のようになります。  
  
```  
SQLBindParameter(StatementHandle, ParameterNumber, SQL_PARAM_INPUT_OUTPUT, ValueType, ParameterType, ColumnSize, DecimalDigits, ParameterValuePtr, SQL_SETPARAM_VALUE_MAX, StrLen_or_IndPtr)  
```
