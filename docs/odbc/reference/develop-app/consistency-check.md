---
title: 整合性チェック |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], consistency checks
- consistency checks [ODBC]
ms.assetid: deb80efa-ad1f-4ea5-b334-9817cd279e5c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cb73d8a4de482f24eae5794232019af9890e3624
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63043737"
---
# <a name="consistency-check"></a>整合性チェック
アプリケーションが APD、ARD、または IPD の SQL_DESC_DATA_PTR フィールドを設定するたびに、整合性チェックがドライバーによって自動的に実行されます。 このフィールドが設定されるたびに、SQL_DESC_TYPE フィールドの値と同じのレコードの SQL_DESC_TYPE フィールドに適用可能な値が有効であり、一貫性のあるドライバーを確認します。  
  
 IPD の SQL_DESC_DATA_PTR フィールドが正常に設定されていません。ただし、アプリケーションは、IPD フィールドの整合性チェックを強制するために行うことができます。 IPD の SQL_DESC_DATA_PTR フィールドに設定されている値が実際に保存されていないとへの呼び出しで取得することはできません**SQLGetDescField**または**SQLGetDescRec**; のみを強制的には、設定、整合性チェックです。 整合性チェックは、IRD では実行できません。  
  
 整合性チェックの詳細については、次を参照してください。 [SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md)します。
