---
title: '付録 G: 旧バージョンとの互換性のためのドライバーガイドライン |Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC drivers [ODBC], backward compatibility
- backward compatibility [ODBC], drivers
- compatibility [ODBC], drivers
ms.assetid: 911cd335-f2c0-4d03-9739-1078308a678a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2a07e936617100c56f8fa873df1b490e1d61e3f3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67909955"
---
# <a name="appendix-g-driver-guidelines-for-backward-compatibility"></a>付録 G: ドライバーの下位互換性のガイドライン
この付録では、ODBC 3 で動作するドライバーライターに関する情報を提供します。ODBC 2 をサポートする必要がある*x*ドライバー。*x*アプリケーション。 旧バージョンとの互換性の詳細については、「[旧バージョンとの互換性と標準の準拠](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md)」を参照してください。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [Odbc 3.X ドライバーのブロックカーソル、スクロール可能なカーソル、および旧バージョンとの互換性](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md)-新機能は odbc 3 に存在する機能です。*x*は ODBC 2 ではありません。*x*。 ODBC 3.*x*ドライバーは、通常、ODBC 2 のために新機能との下位互換性について心配する必要はありません。*x*アプリケーションは使用しません。 この唯一の例外は、 **Sqlfetch**、 **sqlfetchscroll**、 **SQLSetPos**、および**SQLExtendedFetch**に関連する機能です。詳細については、この付録の「」を参照してください。  
  
-   [非推奨の関数のマッピング](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)-ODBC 3 では、重複する機能が異なる方法で実装されています。*x*および ODBC 2。*x*。 ODBC 3.ドライバーマネージャーは常に ODBC 2 をマップするため、 *x*ドライバーは重複した機能との下位互換性について心配する必要はありません。ODBC 3 の*x*機能。ODBC 3 を呼び出すときの*x*機能。*x*ドライバー。 つまり、ODBC 3 です。*x*ドライバーは ODBC 3 のみを認識します。*x*の機能。 これらのマッピングの詳細については、この付録の「」を参照してください。  
  
-   動作の[変更と odbc 3.X ドライバー](../../../odbc/reference/appendixes/behavioral-changes-and-odbc-3-x-drivers.md) -動作の変更は、odbc 3 で異なる方法で処理される機能です。*x*および ODBC 2。*x*。 ODBC 3.*x*ドライバーは、動作の変更について心配し、アプリケーションによって設定された SQL_ATTR_ODBC_VERSION 環境属性に応答して動作する必要があります。
