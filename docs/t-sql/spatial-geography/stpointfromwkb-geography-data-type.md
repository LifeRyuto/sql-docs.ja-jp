---
title: STPointFromWKB (geography データ型) | Microsoft Docs
ms.custom: ''
ms.date: 07/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STPointFromWKB_TSQL
- STPointFromWKB (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STPointFromWKB method
ms.assetid: b3b4e3bb-47bc-4621-99c4-c97aa60cdf8b
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: 3db903d9d586da5a73356aea1d68b4b6ecbb2b5e
ms.sourcegitcommit: 57c3b07cba5855fc7b4195a0586b42f8b45c08c2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2019
ms.locfileid: "65936102"
---
# <a name="stpointfromwkb-geography-data-type"></a>STPointFromWKB (geography データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Open Geospatial Consortium (OGC) Well-Known Binary (WKB) 表現から **geographyPoint** インスタンスを返します。
  
## <a name="syntax"></a>構文  
  
```  
  
STPointFromWKB ( 'WKB_point' , SRID )  
```  
  
## <a name="arguments"></a>引数  
 *WKB_point*  
 返される **geographyPoint** インスタンスの WKB 表現です。 *WKB_point* は、**varbinary (max)** 式です。  
  
 *SRID*  
 返される **geographyPoint** インスタンスの SRID (spatial reference ID) を表す **int** 式です。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 戻り値の型: **geography**  
  
 CLR の戻り値の型:**SqlGeography**  
  
 OGC の型:**Point**  
  
## <a name="remarks"></a>Remarks  
 このメソッドでは、入力が整形式でない場合に、**FormatException** がスローされます。  
  
## <a name="examples"></a>使用例  
 `STPointFromWKB()` を使用して `geography` インスタンスを作成する例を次に示します。  
  
```  
DECLARE @g geography;  
SET @g = geography::STPointFromWKB(0x010100000017D9CEF753D347407593180456965EC0, 4326);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>参照  
 [OGC の静的な地理メソッド](../../t-sql/spatial-geography/ogc-static-geography-methods.md)  
  
  
