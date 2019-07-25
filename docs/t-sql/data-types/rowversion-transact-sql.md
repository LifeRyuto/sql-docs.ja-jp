---
title: rowversion (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/22/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- timestamp_TSQL
- timestamp
dev_langs:
- TSQL
helpviewer_keywords:
- rowversion data type
- size [SQL Server], rowversion
- row version-stamping [SQL Server]
- rowversion columns
- version-stamping table rows
- unique rowversion numbers
- unique timestamp numbers
- timestamp data type
- timestamp columns
- size [SQL Server], timestamp
ms.assetid: 65c9cf0e-3e8a-45f8-87b3-3460d96afb0b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b08c5653243bce5852bab54bee267a43cc3b16e4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68000582"
---
# <a name="rowversion-transact-sql"></a>rowversion (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

データベース内で自動的に生成された一意の 2 進数を公開するデータ型です。 **rowversion** は、通常、テーブルの行のバージョンを記録するためのメカニズムとして使用します。 ストレージ サイズは 8 バイトです。 **Rowversion** データ型は数値を加算していくだけであり、日付や時刻では保持されません。 日付または時刻を記録するには、使用、 **datetime2** データ型。
  
## <a name="remarks"></a>Remarks  
各データベースを含むテーブルで実行される update 操作または挿入ごとにインクリメントされるカウンターには、 **rowversion** 、データベース内の列です。 このカウンターは、データベース rowversion です。 これにより、クロックへの関連付けが可能な実際の時間ではなく、データベース内の相対時間が追跡されます。 テーブルには、1 つだけ保持できます **rowversion** 列です。 たびにを持つ行、 **rowversion** で増加したデータベース rowversion 値が挿入される、列が変更または挿入、 **rowversion** 列です。 このため、 **rowversion** 列、不適切なキーとして、特に主キー。 行を更新すると rowversion 値が変わるので、キーの値も変わります。 列が主キー内にある場合、以前のキーの値は無効になり、この以前の値を参照する外部キーも無効になります。 動的カーソルでテーブルを参照する場合、すべての更新操作はカーソル上の行の位置を変更します。 列がインデックス キーの場合は、データ行に対するすべての更新によって、インデックスの更新も生成されます。  行の値が変更されない場合でも、**rowversion** 値は、update ステートメントによって増分されます (たとえば、列の値が 5 のときに、update ステートメントによって値が 5 に設定された場合、この操作は値の変更がないにもかかわらず更新とみなされ、**rowversion** は増分されます)。
  
**タイムスタンプ** のシノニムには、**rowversion** データを入力し、動作が適用のデータ型のシノニム。 DDL ステートメントでは、次のように使用します。 **rowversion** の代わりに **タイムスタンプ** 可能な限りです。 詳しくは、「[データ型のシノニム &#40;Transact-SQL&#41;](../../t-sql/data-types/data-type-synonyms-transact-sql.md)」をご覧ください。
  
[!INCLUDE[tsql](../../includes/tsql-md.md)] の **timestamp** データ型は、ISO 標準に定義されている **timestamp** データ型とは異なります。
  
> [!NOTE]  
>  **タイムスタンプ** 構文は非推奨とされます。 [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
CREATE TABLE または ALTER TABLE ステートメントでは、列名を指定する必要はありません、 **タイムスタンプ** などのデータ型します。
  
```sql
CREATE TABLE ExampleTable (PriKey int PRIMARY KEY, timestamp);  
```  
  
列名を指定しない場合、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 生成、 **タイムスタンプ** 列の名前。 ただし、、 **rowversion** シノニムがこの動作に従っていません。 使用すると **rowversio**n, 、たとえば、列名を指定する必要があります。
  
```sql
CREATE TABLE ExampleTable2 (PriKey int PRIMARY KEY, VerCol rowversion) ;  
```  
  
> [!NOTE]  
>  重複して **rowversion** を SELECT INTO ステートメントを使用して値を生成することができます、 **rowversion** 列が SELECT リストです。 使用しないで **rowversion** をこのようにします。  
  
Null 値非許容 **rowversion** 列と同じ意味、 **binary (8)** 列です。 Null 値を許容 **rowversion** 列と同じ意味、 **varbinary (8)** 列です。
  
行の **rowversion** 列を使用して、最後の読み取り以降、その行に対して update ステートメントが実行されているかどうかを簡単に判断できます。 行に対して update ステートメントが実行されていれば、rowversion 値は更新されています。 行に対して update ステートメントが実行されていなければ、rowversion 値は前回の読み取り時と同じです。 データベースの現在の rowversion 値を返すには、[@@DBTS](../../t-sql/functions/dbts-transact-sql.md) を使用します。
  
追加することができます、 **rowversion** 列を複数のユーザーが同時に行を更新するときに、データベースの整合性を維持するためにテーブルです。 テーブルに対するクエリを再度実行せずに、行数や更新された行を把握する必要がある場合もあります。
  
たとえば、`MyTest` という名前のテーブルを作成するとします。 以下を実行して、テーブル内のデータを設定する [!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントです。
  
```sql
CREATE TABLE MyTest (myKey int PRIMARY KEY  
    ,myValue int, RV rowversion);  
GO   
INSERT INTO MyTest (myKey, myValue) VALUES (1, 0);  
GO   
INSERT INTO MyTest (myKey, myValue) VALUES (2, 0);  
GO  
```  
  
次に、以下のサンプル [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用して、更新中に `MyTest` テーブルにオプティミスティック コンカレンシーを実装します。
  
```sql
DECLARE @t TABLE (myKey int);  
UPDATE MyTest  
SET myValue = 2  
    OUTPUT inserted.myKey INTO @t(myKey)   
WHERE myKey = 1   
    AND RV = myRv;  
IF (SELECT COUNT(*) FROM @t) = 0  
    BEGIN  
        RAISERROR ('error changing row with myKey = %d'  
            ,16 -- Severity.  
            ,1 -- State   
            ,1) -- myKey that was changed   
    END;  
```  
  
`myRv` は、その行の前回の読み取り時間を示す、行の **rowversion** 列の値です。 実際、この値を置き換える必要があります **rowversion** 値。 実際の例 **rowversion** 値は、0x00000000000007d3 などになります。
  
また、サンプル [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントをトランザクションに置くことができます。 トランザクションの範囲内で `@t` 変数に対してクエリを実行すると、`MyTest` テーブルに対するクエリを再度実行しなくても、テーブルの更新済みの `myKey` 列を取得できます。
  
同じ例を次に示しますを使用して、 **タイムスタンプ** 構文。
  
```sql
CREATE TABLE MyTest2 (myKey int PRIMARY KEY  
    ,myValue int, TS timestamp);  
GO   
INSERT INTO MyTest2 (myKey, myValue) VALUES (1, 0);  
GO   
INSERT INTO MyTest2 (myKey, myValue) VALUES (2, 0);  
GO  
DECLARE @t TABLE (myKey int);  
UPDATE MyTest2  
SET myValue = 2  
    OUTPUT inserted.myKey INTO @t(myKey)   
WHERE myKey = 1   
    AND TS = myTS;  
IF (SELECT COUNT(*) FROM @t) = 0  
    BEGIN  
        RAISERROR ('error changing row with myKey = %d'  
            ,16 -- Severity.  
            ,1 -- State   
            ,1) -- myKey that was changed   
    END;  
```  
  
## <a name="see-also"></a>参照
[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
[CAST および CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)  
[データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)  
[INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)  
[MIN_ACTIVE_ROWVERSION &#40;Transact-SQL&#41;](../../t-sql/functions/min-active-rowversion-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)  
[UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)
  
  
