---
title: SQL Server テーブルから列を削除する |Microsoft Docs
description: SQL Server の OLE DB ドライバーを使用して SQL Server テーブルから列を削除します。
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- columns [OLE DB]
- removing columns
- DropColumn function
- OLE DB Driver for SQL Server, columns
author: pmasl
ms.author: pelopes
manager: jroth
ms.openlocfilehash: 5c7df54441d2777a7799660f8e28c9248ae2620b
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66766228"
---
# <a name="removing-a-column-from-a-sql-server-table"></a>SQL Server テーブルからの列の削除
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  OLE DB Driver for SQL Server を公開、 **itabledefinition::dropcolumn**関数。 コンシューマーはこの関数を使用して、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] テーブルから列を削除できます。  
  
 コンシューマーはテーブル名は、*pTableID* パラメーターの *uName* 共用体の *pwszName* メンバーに Unicode 文字列で指定します。 *pTableID* の *eKind* メンバーを DBKIND_NAME にする必要があります。  
  
 コンシューマーで列の名前を示す、 *pwszName*のメンバー、 *uName*共用体の*pColumnID*パラメーター。 列名は Unicode 文字列で指定します。 *pColumnID* の *eKind* メンバーを DBKIND_NAME にする必要があります。  
  
## <a name="example"></a>例  
  
### <a name="code"></a>コード  
  
```  
DBID TableID;  
DBID ColumnID;  
HRESULT hr;  
  
TableID.eKind = DBKIND_NAME;  
TableID.uName.pwszName = L"MyTableName";  
  
ColumnID.eKind = DBKIND_NAME;  
ColumnID.uName.pwszName = L"MyColumnName";  
  
hr = m_pITableDefinition->DropColumn(&TableID, &ColumnID);  
```  
  
## <a name="see-also"></a>参照  
 [テーブルとインデックス](../../oledb/ole-db-tables-indexes/tables-and-indexes.md)  
  
  
