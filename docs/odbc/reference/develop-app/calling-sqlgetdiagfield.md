---
title: SQLGetDiagField の呼び出し |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- application upgrades [ODBC], SQLGetDiagField
- backward compatibility [ODBC], SqlGetDiagField
- upgrading applications [ODBC], SQLGetDiagField
- SQLGetDiagField function [ODBC], calling
- compatibility [ODBC], SQLGetDiagField
ms.assetid: 3c4fb606-b81c-4f11-9820-f0a54e3bc401
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a27584a0892bc468b50286b79edbe92d7c968a0a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63199157"
---
# <a name="calling-sqlgetdiagfield"></a>SQLGetDiagField の呼び出し
ODBC 3 時にします。*x*アプリケーション呼び出し**SQLGetDiagField** ODBC 2 で *.x*ドライバー、ドライバーは SQL_SUCCESS と適切な情報を返すは *\*DiagInfoPtr*場合、 *DiagIdentifier*引数が SQL_DIAG_CLASS_ORIGIN、SQL_DIAG_CLASS_SUBCLASS_ORIGIN、SQL_DIAG_CONNECTION_NAME、SQL_DIAG_MESSAGE_TEXT、SQL_DIAG_NATIVE、SQL_DIAG_SQL_DIAG_RETURNCODE、SQL_DIAG_SERVER_NAME、または SQL_DIAG_SQLSTATE 数。 その他のすべての診断フィールドには、SQL_ERROR が返されます。
