---
title: SQLAllocStmt のマッピング |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLAllocStmt
- SQLAllocStmt function [ODBC], mapping
ms.assetid: a2449dbb-1b6c-4b49-81b9-ebdddd4442fd
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 330c245d8b5839fd8a721a7399a22edea78a2417
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63269960"
---
# <a name="sqlallocstmt-mapping"></a>SQLAllocStmt のマッピング
アプリケーションを呼び出すと**SQLAllocStmt**を通じて、ODBC 3 *.x*ドライバーへの呼び出し。  
  
```  
SQLAllocStmt(hdbc, phstmt)  
```  
  
 マップされて**SQLAllocHandle**ドライバー マネージャーによってドライバーとして次のとおりです。  
  
```  
SQLAllocHandle(SQL_HANDLE_STMT, InputHandle, OutputHandlePtr)  
```  
  
 *InputHandle*に設定*hdbc*と*OutputHandlePtr*設定*phstmt*します。
