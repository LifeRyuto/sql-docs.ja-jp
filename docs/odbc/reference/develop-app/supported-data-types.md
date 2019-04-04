---
title: サポートされているデータの種類 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], DBMS support
- interoperability [ODBC], data types
ms.assetid: a89d4bab-ef3c-45c2-aa72-2639b3e0f856
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2a8848bad9d27dfd9318b725b77203706d3dfd5a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47753260"
---
# <a name="supported-data-types"></a>サポートされるデータ型
Dbms でサポートされるデータ型は大きく異なります。 アプリケーションが呼び出すことによって、名前とサポートされるデータ型の特性を確認できます**SQLGetTypeInfo**します。 データ型の名前で、広範のため、アプリケーションがによって返されるデータ型の名前を使用する必要があります**SQLGetTypeInfo**で**CREATE TABLE**ステートメント。 詳細については、[ODBC のデータ型](../../../odbc/reference/develop-app/data-types-in-odbc.md)を参照してください。
