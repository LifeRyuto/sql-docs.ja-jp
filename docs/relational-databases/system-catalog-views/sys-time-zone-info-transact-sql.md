---
title: time_zone_info (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 08/06/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.time_zone_info
- sys.time_zone_info_TSQL
- time_zone_info
- time_zone_info_TSQL
helpviewer_keywords:
- sys.time_zone_info system table
ms.assetid: 3f51a9a4-75f8-4a11-9552-8bf6118b68da
author: stevestein
ms.author: sstein
monikerRange: =azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 69bfcbb7e1eeaf6b456a2e10d1f3bfcc581c3d76
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68106703"
---
# <a name="systime_zone_info-transact-sql"></a>sys.time_zone_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  サポートされているタイムゾーンに関する情報を返します。 コンピューターにインストールされているすべてのタイムゾーンは、次のレジストリハイブに格納されます。  
`KEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time Zones`.  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|タイムゾーンの名前 (Windows 標準形式)。 たとえば、中央の**オーストラリア標準時**または**中央ヨーロッパ標準時**です。|  
|**current_utc_offset**|**nvarchar (12)**|UTC への現在のオフセット。 たとえば、 **+ 01:00**や **-07:00**のようになります。|  
|**is_currently_dst**|**bit**|現在夏時間を観察している場合は True。|  
  
## <a name="see-also"></a>参照  
 [GETUTCDATE &#40;Transact-sql&#41;](../../t-sql/functions/getutcdate-transact-sql.md)   
 [AT TIME ZONE &#40;Transact-sql&#41;](../../t-sql/queries/at-time-zone-transact-sql.md)   
 [日付と時刻のデータ型および関数 &#40;Transact-sql&#41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md)   
 [サーバー全体の構成のカタログビュー &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/server-wide-configuration-catalog-views-transact-sql.md)  
