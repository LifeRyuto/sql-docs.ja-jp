---
title: テンプレートのキャッシュ (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- registry keys [SQLXML]
- cache [SQLXML]
- templates [SQLXML], caching
ms.assetid: 73e151c6-b24e-4422-a116-51e0846bc6f5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0024066a5a687828cc59d5053d62e891bbf198d5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66013210"
---
# <a name="template-caching-sqlxml-40"></a>テンプレートのキャッシュ (SQLXML 4.0)
  テンプレートをキャッシュすると、パフォーマンスが大幅に向上します。 テンプレートのキャッシュを設定している場合、テンプレートは初回実行時にメモリに残るので、 以降のテンプレート実行でパフォーマンスが向上します。  
  
 テンプレートのキャッシュ サイズは、レジストリに次のキーを追加することで設定できます。  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML4\TemplateCacheSize  
```  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../../includes/ssnoteregistry-md.md)]  
  
 テンプレートのサイズは、使用できるメモリと使用しているテンプレートの数に基づいて設定します。 **TemplateCacheSize**の既定値は31です。 テンプレートのアクセスが遅い場合はキャッシュ サイズを増やし、メモリが少ない場合はキャッシュ サイズを減らします。  
  
 パフォーマンスを向上させるために、通常使用するテンプレートの数より**TemplateCacheSize**を設定することをお勧めします。 **TemlateCacheSize**がテンプレートの数より少ない場合、テンプレートの数が増えるにつれてパフォーマンスが低下します。 **TemplateCacheSize**は最大128に設定できます。  
  
 キャッシュされたテンプレートが使用されるときには、毎回テンプレート ファイルの変更回数がチェックされ、更新が必要がどうかが決定されます。 これは、ディスク コピーがキャッシュ コピーより新しいためです。  
  
> [!NOTE]  
>  テンプレートのパラメーターとコマンド プロパティはキャッシュされません。  
  
## <a name="see-also"></a>参照  
 [スキーマキャッシュ &#40;SQLXML 4.0&#41;](schema-caching-sqlxml-4-0.md)   
 [XSL キャッシュ &#40;SQLXML 4.0&#41;](xsl-caching-sqlxml-4-0.md)  
  
  
