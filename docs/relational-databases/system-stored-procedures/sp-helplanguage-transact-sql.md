---
title: sp_helplanguage (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helplanguage
- sp_helplanguage_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helplanguage
- default languages
ms.assetid: 8c4651a5-7dbc-49c5-8691-dc72103c2dfa
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d46e178fc1872a84bb573f16629803c59f2fb6c6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68122509"
---
# <a name="sp_helplanguage-transact-sql"></a>sp_helplanguage (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] での特定の代替言語、またはすべての言語に関する情報を報告します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helplanguage [ [ @language = ] 'language' ]  
```  
  
## <a name="arguments"></a>引数  
`[ @language = ] 'language'`情報を表示する代替言語の名前を指定します。 *language*は**sysname**,、既定値は NULL です。 *Language*を指定すると、指定した言語に関する情報が返されます。 場合言語が指定されていない、 **sys.syslanguages**互換性ビューのすべての言語に関する情報が返されます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**langid**|**smallint**|言語 ID 番号です。|  
|**dateformat**|**nchar (3)**|日付の形式。|  
|**datefirst**|**tinyint**|週の最初の曜日: 1 の場合は1、火曜日の場合は2、日曜日の場合は7です。|  
|**増設**|**int**|この言語を使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の最新アップグレード バージョンです。|  
|**name**|**sysname**|言語名。|  
|**エイリアス**|**sysname**|言語の別名です。|  
|**前月**|**nvarchar (372)**|月の名前。|  
|**shortmonths**|**nvarchar (132)**|短い月の名前。|  
|**日時**|**nvarchar (217)**|曜日名。|  
|**lcid**|**int**|この言語を使用する  Windows のロケール ID。|  
|**msglangid**|**smallint**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]メッセージグループ ID。|  
  
## <a name="permissions"></a>アクセス許可  
 **Public**ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>例  
  
### <a name="a-returning-information-about-a-single-language"></a>A. 1つの言語に関する情報を返す  
 次の例では、代替言語`French`に関する情報を表示します。  
  
```  
sp_helplanguage French;  
```  
  
### <a name="b-returning-information-about-all-languages"></a>B. すべての言語に関する情報を返す  
 次の例では、インストールされているすべての代替言語に関する情報を表示します。  
  
```  
sp_helplanguage;  
```  
  
## <a name="see-also"></a>参照  
 [Transact-sql&#41;&#40;のストアドプロシージャのデータベースエンジン](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [@@LANGUAGE &#40;transact-sql&#41;](../../t-sql/functions/language-transact-sql.md)   
 [SET LANGUAGE &#40;Transact-sql&#41;](../../t-sql/statements/set-language-transact-sql.md)   
 [システムストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
