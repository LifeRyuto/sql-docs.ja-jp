---
title: Point (geography データ型) | Microsoft Docs
ms.custom: ''
ms.date: 07/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- Point
- Point_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Point method
- Point (geography Data Type)
ms.assetid: 0dc6f422-7aae-4016-b7f4-3289fa8f989c
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: ddd506ca3e78dd4ad5a12cfb108ca539e094cb4e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "65937998"
---
# <a name="point-geography-data-type"></a>Point (geography データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

**Point** インスタンスを緯度、経度、SRID (spatial reference identifier) で表す **geography** インスタンスを構築します。
  
## <a name="syntax"></a>構文  
  
```  
  
Point ( Lat, Long, SRID )  
```  
  
## <a name="arguments"></a>引数  
 *Lat*  
 生成される **Point** の x 座標を表す **float** 式です。  
  
 *Long*  
 生成される **Point** の y 座標を表す **float** 式です。 有効な経度と緯度の値の詳細については、「[Point](../../relational-databases/spatial/point.md)」をご覧ください。  
  
 *SRID*  
 返される **geography** インスタンスの SRID を表す **int** 式です。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 戻り値の型: **geography**  
  
 CLR の戻り値の型:**SqlGeography**  
  
> [!NOTE]  
>  Point (geography データ型) メソッドの引数は、WKT と比較して元に戻された座標を持ちます。  
  
## <a name="examples"></a>使用例  
 `Point()` を使用して `geography` インスタンスを作成する例を次に示します。  
  
```  
DECLARE @g geography;   
SET @g = geography::Point(47.65100, -122.34900, 4326)  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>参照  
 [拡張された静的な地理メソッド](../../t-sql/spatial-geography/extended-static-geography-methods.md)  
  
  
