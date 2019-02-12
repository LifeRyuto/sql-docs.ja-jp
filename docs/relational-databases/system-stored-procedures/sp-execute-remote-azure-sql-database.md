---
title: sp_execute_remote (Azure SQL データベース) |Microsoft Docs
ms.custom: ''
ms.date: 02/01/2017
ms.service: sql-database
ms.reviewer: ''
ms.topic: conceptual
f1_keywords:
- sp_execute_remote
- sp_execute_remote_TSQL
helpviewer_keywords:
- remote execution
- queries, remote execution
ms.assetid: ca89aa4c-c4c1-4c46-8515-a6754667b3e5
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: a475ba50aa8d3ba140ea551306d8b9f17fe66d22
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56035903"
---
# <a name="spexecuteremote-azure-sql-database"></a>sp_execute_remote (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  実行、[!INCLUDE[tsql](../../includes/tsql-md.md)]のステートメントでは、リモートの Azure SQL Database は 1 つまたは一連のデータベースを水平方向のパーティション構成にシャードとして機能します。  
  
 ストアド プロシージャには、エラスティック クエリ機能の一部です。  参照してください[Azure SQL Database エラスティック データベース クエリの概要](https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-overview/)と[(水平パーティション) シャーディングのエラスティック データベース クエリ](https://azure.microsoft.com/documentation/articles/sql-database-elastic-query-horizontal-partitioning/)します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
sp_execute_remote [ @data_source_name = ] datasourcename  
[ , @stmt = ] statement  
[   
  { , [ @params = ] N'@parameter_name data_type [,...n ]' }   
     { , [ @param1 = ] 'value1' [ ,...n ] }  
]  
```  
  
## <a name="arguments"></a>引数  
 [ \@data_source_name = ] *datasourcename*  
 ステートメントを実行する外部データ ソースを識別します。 参照してください[外部データ ソースの作成 & #40 です。TRANSACT-SQL と #41 です](../../t-sql/statements/create-external-data-source-transact-sql.md)。 外部データ ソースは、"RDBMS"または"SHARD_MAP_MANAGER"の型指定できます。  
  
 [ \@stmt= ] *statement*  
 含む Unicode 文字列には、 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントまたはバッチです。 \@stmt は、Unicode 定数または Unicode 変数のいずれかである必要があります。 + 演算子で 2 つの文字列を連結するなどの複雑な Unicode 式は使用できません。 文字定数も使用できません。 Unicode 定数が指定されている場合に付ける必要があります、 **N**します。Unicode 定数など**N 'sp_who'** が有効で、文字定数 **'sp_who'** はありません。 文字列のサイズは、データベース サーバーで利用可能なメモリにより制限されます。 64 ビット サーバーで、文字列のサイズが 2 GB の最大サイズに制限、 **nvarchar (max)** します。  
  
> [!NOTE]  
>  \@stmt には、たとえば、名前の変数と同じ形式を持つパラメーターを含めることができます。 `N'SELECT * FROM HumanResources.Employee WHERE EmployeeID = @IDParameter'`  
  
 含まれる各パラメーター \@stmt では、両方に対応するエントリがあります、 \@params パラメーター定義リストとパラメーター値の一覧。  
  
 [ \@params= ] N'\@*parameter_name**data_type* [ ,... *n* ] '  
 1 つの文字列に埋め込まれたすべてのパラメーターの定義を含む\@stmt します。この文字列は Unicode 定数または Unicode 変数にする必要があります。 各パラメーター定義は、パラメーター名とデータ型で構成されます。 *n*は追加のパラメーター定義を示すプレース ホルダーです。 すべてのパラメーターで指定された\@で定義されている stmtmust \@params します。 場合、[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントまたはバッチに\@stmt にパラメーターが含まれていない\@params は必要ありません。 このパラメーターの既定値は NULL です。  
  
 [ \@param1= ] '*value1*'  
 パラメーター文字列に定義する最初のパラメーターの値を指定します。 Unicode 定数または Unicode 変数を指定できます。 含まれるすべてのパラメーターに指定されたパラメーター値が必要がある\@stmt します。ときに、値は必要ありません、[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントまたはバッチに\@stmt にパラメーターがありません。  
  
 *n*  
 追加するパラメーター値のプレースホルダーです。 定数または変数のみを指定できます。 関数などの複雑な式や演算子を使用した式は指定できません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 0 以外 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 最初の SQL ステートメントの結果セットを返します。  
  
## <a name="permissions"></a>アクセス許可  
 `ALTER ANY EXTERNAL DATA SOURCE` 権限が必要です。  
  
## <a name="remarks"></a>コメント  
 `sp_execute_remote` 上記の「構文」の説明に従って、特定の順序でパラメーターを入力する必要があります。 パラメーターを不適切な順序で入力した場合、エラー メッセージが表示されます。  
  
 `sp_execute_remote`として動作は同じ[EXECUTE &#40;TRANSACT-SQL &#41;](../../t-sql/language-elements/execute-transact-sql.md)に関してバッチおよび名前のスコープです。 TRANSACT-SQL ステートメントまたはバッチ、sp_execute_remote に *\@stmt*パラメーターは、sp_execute_remote ステートメントが実行されるまでコンパイルされません。  
  
 `sp_execute_remote` という名前の '$ShardName'、行を生成したリモート データベースの名前を含む結果セットに追加の列を追加します。  
  
 `sp_execute_remote`同様に使用できる[sp_executesql & #40 です。TRANSACT-SQL と #41 です](../../relational-databases/system-stored-procedures/sp-executesql-transact-sql.md)。  
  
## <a name="examples"></a>使用例  
### <a name="simple-example"></a>簡単な例  
 次の例では、作成し、リモート データベースで単純な SELECT ステートメントを実行します。  
  
```sql  
EXEC sp_execute_remote  
    N'MyExtSrc',  
    N'SELECT COUNT(w_id) AS Count_id FROM warehouse'   
```  
  
### <a name="example-with-multiple-parameters"></a>複数のパラメーターの例  
ユーザー データベース、master データベースの管理者の資格情報を指定することで、データベース スコープ資格情報を作成します。 Master データベースをポイントし、データベース スコープ資格情報を指定する外部データ ソースを作成します。 次の例で、ユーザー データベースを実行し、 `sp_set_firewall_rule` master データベース内のプロシージャです。 `sp_set_firewall_rule`手順 3 つのパラメーターとが必要です、`@name`パラメーターを Unicode になります。

```
EXEC sp_execute_remote @data_source_name  = N'PointToMaster', 
@stmt = N'sp_set_firewall_rule @name, @start_ip_address, @end_ip_address', 
@params = N'@name nvarchar(128), @start_ip_address varchar(50), @end_ip_address varchar(50)',
@name = N'TempFWRule', @start_ip_address = '0.0.0.2', @end_ip_address = '0.0.0.2';
```

## <a name="see-also"></a>参照:

[作成するデータベース スコープ資格情報](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)  
[外部データ ソース (TRANSACT-SQL) を作成します。](../../t-sql/statements/create-external-data-source-transact-sql.md)  
    
