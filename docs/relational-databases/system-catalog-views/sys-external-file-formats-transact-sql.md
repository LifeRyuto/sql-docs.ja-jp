---
title: external_file_formats (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: a89efb2c-0a3a-4b64-9284-6e93263e29ac
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: eae119fe16b916f47f1acdcd2ebe15efd96e51e9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68048390"
---
# <a name="sysexternal_file_formats-transact-sql"></a>external_file_formats (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssSDS](../../includes/sssds-md.md)]、および[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]の現在のデータベース内の外部ファイル形式ごとに1行のデータを格納します。  
  
 の[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]サーバー上の外部ファイル形式ごとに1行の値を格納します。  
  
|列名|データ型|[説明]|Range|  
|-----------------|---------------|-----------------|-----------|  
|file_format_id|**int**|外部ファイル形式のオブジェクト ID。||  
|name|**sysname**|ファイル形式の名前。 と[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]では、これはデータベースに対して一意です。 で[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]は、これはサーバーに対して一意です。||  
|format_type|**tinyint**|ファイル形式の種類。|DELIMITEDTEXT、RCFILE、ORC、PARQUET|  
|field_terminator|**nvarchar (10)**|Format_type = DELIMITEDTEXT の場合、これはフィールドターミネータです。||  
|string_delimiter|**nvarchar (10)**|Format_type = DELIMITEDTEXT の場合、これは文字列の区切り記号です。||  
|date_format|**nvarchar(50)**|Format_type = DELIMITEDTEXT の場合は、ユーザー定義の日付と時刻の形式です。||  
|use_type_default|**bit**|Format_type = 区切られたテキストの場合、PolyBase が HDFS テキストファイルからに[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]データをインポートするときに欠損値を処理する方法を指定します。|0-文字列 ' NULL ' として欠損値を格納します。<br /><br /> 1-欠損値を列の既定値として格納します。|  
|serde_method|**nvarchar(255)**|Format_type = RCFILE の場合、これはシリアル化/逆シリアル化の方法です。||  
|row_terminator|**nvarchar (10)**|Format_type = DELIMITEDTEXT の場合、これは外部の Hadoop ファイル内の各行を終了する文字列です。|常に ' \n ' です。|  
|encoding|**nvarchar (10)**|Format_type = DELIMITEDTEXT の場合、これは外部の Hadoop ファイルのエンコード方法です。|常に ' UTF8 ' です。|  
|data_compression|**nvarchar(255)**|外部データのデータ圧縮方法。|Format_type = DELIMITEDTEXT の場合:<br /><br /> -' org. hadoop...........................<br />-' Org.apache.hadoop.io.compress.gzipcodec ' のようになります。<br /><br /> Format_type = RCFILE の場合:<br /><br /> -' org. hadoop...........................<br /><br /> Format_type = ORC の場合:<br /><br /> -' org. hadoop...........................<br />-' Org.apache.io.compress.snappycodec ' のようになります。<br /><br /> Format_type = PARQUET の場合:<br /><br /> -' Org.apache.hadoop.io.compress.gzipcodec ' のようになります。<br />-' Org.apache.io.compress.snappycodec ' のようになります。|  
  
## <a name="permissions"></a>アクセス許可  
 カタログ ビューでのメタデータの表示が、ユーザーが所有しているかそのユーザーが権限を許可されている、セキュリティ保護可能なメタデータに制限されます。 詳細については、「[メタデータ表示の構成](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [external_data_sources &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-external-data-sources-transact-sql.md)   
 [external_tables &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-external-tables-transact-sql.md)   
 [Transact-sql&#41;&#40;外部ファイル形式を作成する](../../t-sql/statements/create-external-file-format-transact-sql.md)  
  
  
