---
title: SQLProcedureColumns (Access Driver) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Access driver [ODBC], SQLProcedureColumns
- SQLProcedureColumns function [ODBC], Access Driver
ms.assetid: 34fee995-5848-4ecb-bda0-fc362a77b2d9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1a33d449396b5cc80e8d29767708d2f9f16736fa
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67987848"
---
# <a name="sqlprocedurecolumns-access-driver"></a>SQLProcedureColumns (Access ドライバー)
> [!NOTE]  
>  このトピックでは、ドライバー固有の情報にアクセスします。 この関数の一般的な情報については、「 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)」の該当するトピックを参照してください。  
  
 アプリケーション開発者は、ドライバー定義の列を検索し、結果セットの末尾から逆方向に進む必要があります。  
  
|列|説明|  
|------------|--------------|  
|COLUMN_TYPE|SQL_PARAM_INPUT または SQL_RESULT_COL|  
|数値|これは、結果セットの末尾に返されるドライバー固有の列です。 列の SQL 型は整数です。|
