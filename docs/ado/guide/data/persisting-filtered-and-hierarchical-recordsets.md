---
title: 永続化するフィルター選択された階層レコード セットは、|Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- filtered Recordset persistence [ADO]
- persisting data [ADO]
- data updates [ADO], persisting data
- data persistence [ADO]
- updating data [ADO], persisting data
ms.assetid: d01aeb4d-4e43-450b-b3f2-0c27eaaf9f86
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: cbd237580dc8c56284552e6fe2fb00e469832c5b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66702049"
---
# <a name="persisting-filtered-and-hierarchical-recordsets"></a>フィルター処理されたレコードセットおよび階層レコードセットの保持
場合、[フィルター](../../../ado/reference/ado-api/filter-property.md)プロパティはに対して有効で、 **Recordset**フィルターでアクセス可能な行のみ保存されます。 場合、**レコード セット**は階層構造を持つ現在の子**レコード セット**と親を含む、その子が保存**レコード セット**します。 場合、**保存**子メソッド**レコード セット**は子とそのすべての子を保存すると、呼び出されるが、親はありません。 階層の詳細については**レコード セット**を参照してください[データ シェイプ](../../../ado/guide/data/data-shaping.md)します。  
  
> [!NOTE]
>  階層を保存するときにいくつかの制限が適用**レコード セット**(データ図形) XML 形式でします。 詳細については、次を参照してください。 [XML 形式で保持するレコード](../../../ado/guide/data/persisting-records-in-xml-format.md)します。
