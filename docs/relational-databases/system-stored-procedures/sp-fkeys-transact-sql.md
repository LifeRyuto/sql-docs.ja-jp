---
title: sp_fkeys (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 09/08/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_fkeys
- sp_fkeys_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_fkeys
ms.assetid: 18110444-d38d-4cff-90d2-d1fc6236668b
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: cb5f684321a11d56a419ae73be0bfb2950fb9939
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68124400"
---
# <a name="sp_fkeys-transact-sql"></a>sp_fkeys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  現在の環境への論理外部キーの情報を返します。 この手順では、無効な外部キーを含む外部キーリレーションシップを示します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
sp_fkeys [ @pktable_name = ] 'pktable_name'   
     [ , [ @pktable_owner = ] 'pktable_owner' ]   
     [ , [ @pktable_qualifier = ] 'pktable_qualifier' ]   
     { , [ @fktable_name = ] 'fktable_name' }   
     [ , [ @fktable_owner = ] 'fktable_owner' ]   
     [ , [ @fktable_qualifier = ] 'fktable_qualifier' ]  
```  
  
## <a name="arguments"></a>引数  
 [ @pktable_name=]'*pktable_name*'  
 カタログ情報を返すために使用される主キーを含むテーブルの名前を指定します。 *pktable_name*は**sysname**,、既定値は NULL です。 ワイルドカードのパターンマッチングはサポートされていません。 このパラメーターまたは*fktable_name*パラメーター (またはその両方) を指定する必要があります。  
  
 [ @pktable_owner=]'*pktable_owner*'  
 カタログ情報を返すために使用される (主キーを持つ) テーブルの所有者の名前を指定します。 *pktable_owner*は**sysname**,、既定値は NULL です。 ワイルドカードのパターンマッチングはサポートされていません。 *Pktable_owner*が指定されていない場合は、基になる DBMS の既定のテーブル可視性ルールが適用されます。  
  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、指定した名前のテーブルを現在のユーザーが所有している場合、そのテーブルの列が返されます。 *Pktable_owner*が指定されておらず、現在のユーザーが指定された*pktable_name*のテーブルを所有していない場合、プロシージャは、データベース所有者が所有する、指定された*pktable_name*を持つテーブルを検索します。 存在する場合は、そのテーブルの列が返されます。  
  
 [ @pktable_qualifier =]'*pktable_qualifier*'  
 (主キーを持つ) テーブル修飾子の名前を指定します。 *pktable_qualifier*は sysname,、既定値は NULL です。 さまざまな DBMS 製品では、3部構成のテーブル名 (*qualifier.owner.name*) がサポートしています。 で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は、修飾子はデータベース名を表します。 一部の製品では、テーブルのデータベース環境のサーバー名を表します。  
  
 [ @fktable_name=]'*fktable_name*'  
 カタログ情報を返すために使用する (外部キーが設定された) テーブルの名前を指定します。 *fktable_name*は sysname,、既定値は NULL です。 ワイルドカードのパターンマッチングはサポートされていません。 このパラメーターまたは*pktable_name*パラメーター (またはその両方) を指定する必要があります。  
  
 [ @fktable_owner =]'*fktable_owner*'  
 カタログ情報を返すために使用する (外部キーが設定された) テーブルの所有者の名前を指定します。 *fktable_owner*は**sysname**,、既定値は NULL です。 ワイルドカードのパターンマッチングはサポートされていません。 *Fktable_owner*が指定されていない場合は、基になる DBMS の既定のテーブル可視性ルールが適用されます。  
  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、指定した名前のテーブルを現在のユーザーが所有している場合、そのテーブルの列が返されます。 *Fktable_owner*が指定されておらず、現在のユーザーが指定された*fktable_name*のテーブルを所有していない場合、プロシージャは、データベース所有者が所有する、指定された*fktable_name*を持つテーブルを検索します。 存在する場合は、そのテーブルの列が返されます。  
  
 [ @fktable_qualifier= ]'*fktable_qualifier*'  
 (外部キーが指定された) テーブル修飾子の名前を指定します。 *fktable_qualifier*は**sysname**,、既定値は NULL です。 で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は、修飾子はデータベース名を表します。 一部の製品では、テーブルのデータベース環境のサーバー名を表します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 なし  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|PKTABLE_QUALIFIER|**sysname**|(主キーを持つ) テーブル修飾子の名前。 このフィールドは NULL にすることができます。|  
|PKTABLE_OWNER|**sysname**|主キーが設定されたテーブルの所有者名です。 このフィールドは常に値を返します。|  
|PKTABLE_NAME|**sysname**|テーブルの名前 (主キーを含む)。 このフィールドは常に値を返します。|  
|PKCOLUMN_NAME|**sysname**|返される TABLE_NAME の各列に対する、主キー列の名前です。 このフィールドは常に値を返します。|  
|FKTABLE_QUALIFIER|**sysname**|外部キーが設定されたテーブルの修飾子の名前です。 このフィールドは NULL にすることができます。|  
|FKTABLE_OWNER|**sysname**|(外部キーを持つ) テーブルの所有者の名前。 このフィールドは常に値を返します。|  
|FKTABLE_NAME|**sysname**|外部キーが設定されたテーブルの名前です。 このフィールドは常に値を返します。|  
|FKCOLUMN_NAME|**sysname**|返される TABLE_NAME の各列の外部キー列の名前。 このフィールドは常に値を返します。|  
|KEY_SEQ|**smallint**|複数列の主キーの列のシーケンス番号。 このフィールドは常に値を返します。|  
|UPDATE_RULE|**smallint**|SQL 操作が更新である場合に、外部キーに適用されるアクションです。  指定できる値<br /> 0 = 外部キーに対して連鎖変更を行います。<br /> 1 = 外部キーが存在する場合、アクションの変更はありません。<br />   2 = null に設定 <br /> 3 = 既定値に設定 |  
|DELETE_RULE|**smallint**|SQL 操作が削除の場合に、外部キーに適用されるアクションです。 指定できる値<br /> 0 = 外部キーに対して連鎖変更を行います。<br /> 1 = 外部キーが存在する場合、アクションの変更はありません。<br />   2 = null に設定 <br /> 3 = 既定値に設定 |  
|FK_NAME|**sysname**|外部キー識別子。 データ ソースに適用されない場合は NULL になります。 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、FOREIGN KEY 制約の名前を返します。|  
|PK_NAME|**sysname**|主キー識別子。 データ ソースに適用されない場合は NULL になります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]PRIMARY KEY 制約の名前を返します。|  
  
 返される結果は、FKTABLE_QUALIFIER、FKTABLE_OWNER、FKTABLE_NAME、KEY_SEQ の順序に従って並べ替えられます。  
  
## <a name="remarks"></a>解説  
 無効な外部キーを含むテーブルを含むアプリケーションのコーディングは、次の方法で実装できます。  
  
-   そのテーブルで作業している間は、一時的に制約チェックを無効にして (ALTER TABLE NOCHECK または CREATE TABLE NOT FOR REPLICATION)、その後再び有効にします。  
  
-   トリガーまたはアプリケーションコードを使用してリレーションシップを適用する。  
  
主キー テーブルの名前を指定され、外部キー テーブルの名前が NULL の場合、sp_fkeys は指定されたテーブルに対する外部キーを含むすべてのテーブルを返します。 外部キー テーブルの名前を指定し、主キー テーブルの名前が NULL の場合、sp_fkeys は、主キー/外部キー関係によって外部キー テーブルの外部キーに関係付けられるすべてのテーブルを返します。  
  
sp_fkeys ストアド プロシージャは、ODBC の SQLForeignKeys に相当します。  
  
## <a name="permissions"></a>アクセス許可  
 スキーマ`SELECT`に対する権限が必要です。  
  
## <a name="examples"></a>例  
 次の例では、 `HumanResources.Department` `AdventureWorks2012`データベース内のテーブルの外部キーの一覧を取得します。  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_fkeys @pktable_name = N'Department'  
    ,@pktable_owner = N'HumanResources';  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 次の例では、 `DimDate` `AdventureWorksPDW2012`データベース内のテーブルの外部キーの一覧を取得します。 は外部キーをサポート[!INCLUDE[ssDW](../../includes/ssdw-md.md)]していないので、行は返されません。  
  
```sql  
EXEC sp_fkeys @pktable_name = N'DimDate;  
```  
  
## <a name="see-also"></a>参照  
 [Transact-sql&#41;&#40;のカタログストアドプロシージャ](../../relational-databases/system-stored-procedures/catalog-stored-procedures-transact-sql.md)   
 [システムストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sp_pkeys &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-pkeys-transact-sql.md)  
  
  

