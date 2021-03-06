---
title: GUID エスケープシーケンス |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC escape sequences [ODBC], GUID
- escape sequences [ODBC], guid
- guid escape sequence [ODBC]
ms.assetid: 71d43ef9-4a31-493e-b9e0-f864e9ef3ce6
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a74ed9d4dfe0afb8bf59abb11220a0677d000bfb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67947582"
---
# <a name="guid-escape-sequences"></a>GUID エスケープ シーケンス
ODBC では、GUID リテラルにエスケープシーケンスを使用します。 このエスケープシーケンスの構文は次のとおりです。  
  
```  
{guid 'nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn'}  
```  
  
## <a name="remarks"></a>解説  
 BNF 表記では、構文は次のようになります。  
  
 *ODBC-guid-escape* :: =  
     *ODBC-esc-イニシエーター guid*'*guid-値*' *ODBC-esc-ターミネータ*  
  
 *ODBC-esc-イニシエーター* :: = {  
  
 *ODBC-esc-ターミネータ*:: =}  
  
 *guid-値*:: = *clock-低値 guid-区切り時計-中間値 guid-区切り時計-高値 guid* -区切り時計-シーケンス値 guid-区切りノード-値  
  
 *guid-separator* :: =-  
  
 *clock-低値*:: = *hex_digit hex_digit hex_digit hex_digit hex_digit* hex_digit hex_digit hex_digit  
  
 *時計中央値*:: = *hex_digit hex_digit hex_digit hex_digit*  
  
 *clock-高値-value* :: = *hex_digit hex_digit hex_digit hex_digit*  
  
 *clock-seq-value* :: = *hex_digit hex_digit hex_digit hex_digit*  
  
 *clock-node-value* :: = *hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit* hex_digit hex_digit hex_digit  
  
 *hex_digit* :: = 0 &#124; 1 &#124; 2 &#124; 3 &#124; 4 &#124; 5 &#124; 6 &#124; 7 &#124; 8 &#124; 9 &#124; &#124; B &#124; C &#124; D &#124; E &#124; F  
  
 Guid リテラルのエスケープシーケンスは、GUID データ型がデータソースでサポートされている場合にサポートされます。 アプリケーションは、このデータ型がサポートされているかどうかを判断するために、 **SQLGetTypeInfo**を呼び出す必要があります。
