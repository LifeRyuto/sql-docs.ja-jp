---
title: sys.dm_xe_database_session_object_columns
titleSuffix: Azure SQL Database
ms.custom: seo-dt-2019
ms.date: 06/10/2016
ms.service: sql-database
ms.prod_service: sql-database
ms.reviewer: ''
ms.topic: language-reference
ms.assetid: 0e6adc54-4d97-4ef0-bf4f-b4538d69f136
author: MightyPen
ms.author: genemi
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 36dfed5d0c24082d01248d7e6e8e1e62e1725e0a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "73844417"
---
# <a name="sysdm_xe_database_session_object_columns-azure-sql-database"></a>sys.dm_xe_database_session_object_columns (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  セッションにバインドされたオブジェクトの構成値を示します。  
  
||  
|-|  
|**に適用さ**れます: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 およびそれ以降のすべてのバージョン。|  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|event_session_address|**varbinary (8)**|イベントセッションのメモリアドレス。 には、dm_xe_database_sessions との多対一のリレーションシップがあります。 NULL 値は許可されません。|  
|column_name|**nvarchar (60)**|構成値の名前。 NULL 値は許可されません。|  
|column_id|**int**|列の ID。 は、オブジェクト内で一意です。 NULL 値は許可されません。|  
|column_value|**nvarchar (2048)**|列の構成値。 NULL 値が許可されます。|  
|object_type|**nvarchar (60)**|オブジェクトの古い型。  Null 値はありません。 object_type は次のいずれかです。<br /><br /> イベント<br /><br /> ターゲット (target)|  
|object_name|**nvarchar (60)**|この列が所属するオブジェクトの名前。 NULL 値は許可されません。|  
|object_package_guid|**UNIQUEIDENTIFIER**|オブジェクトを含むパッケージの GUID。 NULL 値は許可されません。|  
  
## <a name="permissions"></a>アクセス許可  
 VIEW DATABASE STATE 権限が必要です。  
  
### <a name="relationship-cardinalities"></a>リレーションシップ基数  
  
|移行元|To|リレーションシップ|  
|----------|--------|------------------|  
|dm_xe_database_session_object_columns。 object_name<br /><br /> dm_xe_database_session_object_columns。 object_package_guid|sys.dm_xe_objects.package_guid<br /><br /> sys.dm_xe_objects.name|多対一|  
|dm_xe_database_session_object_columns。 column_name<br /><br /> dm_xe_database_session_object_columns。 column_id|sys.dm_xe_object_columns.name<br /><br /> sys.dm_xe_object_columns.column_id|多対一|  
  
## <a name="see-also"></a>参照  
 [拡張イベント](../../relational-databases/extended-events/extended-events.md)  
  
  
