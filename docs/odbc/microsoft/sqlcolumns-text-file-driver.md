---
title: SQLColumns (テキストファイルドライバー) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- text file driver [ODBC], SQLColumns
- SQLColumns function [ODBC], Text File Driver
ms.assetid: c99e5f8d-4e43-48f8-9e0e-086707b411f5
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 893ffa40f346a878b4cdde87a9a0a55fbb9e1c7a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68132522"
---
# <a name="sqlcolumns-text-file-driver"></a>SQLColumns (テキスト ファイル ドライバー)
> [!NOTE]  
>  このトピックでは、テキストファイルドライバー固有の情報について説明します。 この関数の一般的な情報については、「 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)」の該当するトピックを参照してください。  
  
|列|説明|  
|------------|--------------|  
|TABLE_QUALIFIER|ディレクトリへのパスが返されます。|  
|TABLE_OWNER|所有者名がサポートされていないため、この列には NULL が返されます。|  
|NULLABLE|主キーまたは一意のインデックスに含まれる列に対して SQL_NO_NULLS が返されます。|
