---
title: cdc です。&lt;capture_instance&gt;_CT (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 05/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- cdc
- cdc_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- cdc.<capture_instance>_CT
ms.assetid: 979c8110-3c54-4e76-953c-777194bc9751
author: stevestein
ms.author: sstein
ms.openlocfilehash: e4ad2d32c313919ed4446a5506f22e9048e09288
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68119309"
---
# <a name="cdcltcaptureinstancegtct-transact-sql"></a>cdc です。&lt;capture_instance&gt;_CT (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ソース テーブルに対して変更データ キャプチャを有効にすると作成される変更テーブルです。 ソース テーブルに対して実行された操作が挿入や削除の場合は、各操作について 1 行を返します。ソース テーブルに対して実行された操作が更新の場合は、各操作について 2 行を返します。 ソース テーブルで変更データ キャプチャを有効にしたときに変更テーブルの名前を指定しなかった場合は、名前が自動的に生成されます。 名前の形式は、cdc です。*capture_instance*_CT 場所*capture_instance*はソース テーブルのスキーマ名とソース テーブル名の形式で*schema_table*します。 たとえば場合の表に、 **Person.Address**で、 **AdventureWorks**サンプル データベースが変更データ キャプチャを有効になっている、変更テーブル名になります**cdc です。Person_Address_CT**します。  
  
 お勧めする**直接システム テーブルを照会できません**します。 代わりに、実行、 [cdc.fn_cdc_get_all_changes_ < capture_instance >](../../relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql.md)と[cdc.fn_cdc_get_net_changes_ < capture_instance >](../../relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql.md)関数。  
  

  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**__$start_lsn**|**binary(10)**|変更のコミット トランザクションに関連付けられたログ シーケンス番号 (LSN)。<br /><br /> 同じトランザクションでコミットされたすべての変更は、同じコミット LSN を共有します。 たとえば、ソース テーブルに対する削除操作は、2 つの行を削除した場合、変更テーブルが格納されます 2 つの行がすべて同じ **_ _ $start_lsn**値。|  
|**__$end_lsn**|**binary(10)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]<br /><br /> [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] では、この列は常に NULL です。|  
|**__$seqval**|**binary(10)**|特定のトランザクションに含まれる行の変更を並べ替えるためのシーケンス値。|  
|**__$operation**|**int**|変更に関連付けられているデータ操作言語 (DML) 操作を識別します。 次のいずれかになります。<br /><br /> 1 = 削除<br /><br /> 2 = 挿入<br /><br /> 3 = 更新 (古い値)<br /><br /> 列データには、更新ステートメントを実行する前の行の値が割り当てられます。<br /><br /> 4 = 更新 (新しい値)<br /><br /> 列データには、更新ステートメントを実行した後の行の値が割り当てられます。|  
|**__$update_mask**|**varbinary (128)**|変更された列を識別する、変更テーブルの列序数に基づくビット マスク。|  
|*\< キャプチャ対象のソース テーブルの列 >*|各種|変更テーブル内のその他の列は、ソース テーブルの列のうち、キャプチャ インスタンスの作成時にキャプチャ対象として指定された列です。 キャプチャ対象列リストで列が指定されなかった場合、ソース テーブルのすべての列がこのテーブルに格納されます。|  
|**_ _ $ command_id** |**int** |トランザクション内の操作の順序を追跡します。 |  
  
## <a name="remarks"></a>コメント  

`__$command_id`列が列は、バージョン 2012 2016年からの累積的な更新で導入されました。 バージョンとダウンロードについては、サポート技術情報記事 3030352 を参照して[修正します。変更テーブルは注文が間違って更新の変更データを有効にした後の行は、Microsoft SQL Server データベースのキャプチャ](https://support.microsoft.com/help/3030352/fix-the-change-table-is-ordered-incorrectly-for-updated-rows-after-you)します。  詳細については、次を参照してください。 [for SQL Server 2012、2014、2016、最新の CU へのアップグレード後に CDC の機能が動作](https://blogs.msdn.microsoft.com/sql_server_team/cdc-functionality-may-break-after-upgrading-to-the-latest-cu-for-sql-server-2012-2014-and-2016/)します。

## <a name="captured-column-data-types"></a>キャプチャ対象列のデータ型  
 このテーブルに含まれるキャプチャ対象列は、ソースの対応する列と同じデータ型および値を持ちます。ただし、次の例外があります。  
  
-   **タイムスタンプ**列として定義は**binary (8)** します。  
  
-   **Identity**列がいずれかとして定義されている**int**または**bigint**します。  
  
 ただし、これらの列の値は、ソース列の値と同じです。  
  
### <a name="large-object-data-types"></a>ラージ オブジェクト データ型  
 データ型の列**イメージ**、**テキスト**、および**ntext**常に割り当てられている、 **NULL**ときの値 _ _ $操作 = 1 または\_\_$operation = 3。 データ型の列**varbinary (max)** 、 **varchar (max)** 、または**nvarchar (max)** 割り当てられている、 **NULL**値と\_\_$operation 列は、更新中に変更しない限り、3 を = です。 ときに\_ \_$operation = 1、これらの列には、削除時にその値が割り当てられます。 キャプチャ インスタンスに常に含まれる計算列の値がある**NULL**します。  
  
 既定では、INSERT、UPDATE、WRITETEXT、または UPDATETEXT の 1 回のステートメントでキャプチャ対象列に追加できる最大サイズは、65,536 バイト (64 KB) です。 大きな LOB データをサポートするためには、このサイズを増やすには使用、 [max text repl size サーバー構成オプションを構成する](../../database-engine/configure-windows/configure-the-max-text-repl-size-server-configuration-option.md)より大きな最大サイズを指定します。 詳細については、「 [max text repl size サーバー構成オプションの構成](../../database-engine/configure-windows/configure-the-max-text-repl-size-server-configuration-option.md)」を参照してください。  
  
## <a name="data-definition-language-modifications"></a>データ定義言語の修正  
 追加や削除、列など、ソース テーブルに対する DDL 修正に記録されます、 [cdc.ddl_history](../../relational-databases/system-tables/cdc-ddl-history-transact-sql.md)テーブル。 これらの変更は変更テーブルに適用されません。 つまり、変更テーブルの定義は以前のままとなります。 ソース テーブルには、キャプチャ対象列リストが関連付けられていますが、キャプチャ プロセスで変更テーブルに行を挿入する際、そのリストに存在しない列は無視されます。 キャプチャ対象列リストに指定されていた列が、ソース テーブルから既に削除されていた場合、その列には NULL 値が割り当てられます。  
  
 記録は、ソース テーブル内の列のデータ型の変更、 [cdc.ddl_history](../../relational-databases/system-tables/cdc-ddl-history-transact-sql.md)テーブル。 ただし、この変更によって、変更テーブルの定義が修正されることはありません。 ソース テーブルに対する DDL 変更のログ レコードがキャプチャ プロセスで見つかった場合は、変更テーブルにおけるキャプチャ対象列のデータ型が変更されます。  
  
 ソース テーブルにおけるキャプチャ対象列のデータ型を、より小さなデータ型に変更する必要がある場合は、次の手順に従って、変更テーブル内の対応する列が正しく変更されるように配慮してください。  
  
1.  ソース テーブルで、変更する列の値を、変更後のデータ型に収まるように更新します。 データ型を変更する場合など**int**に**smallint**、サイズに収まるように値を更新、 **smallint** -32,768 ~ 32,767 の範囲します。  
  
2.  変更テーブル側の対応する列にも、同じ更新操作を実行します。  
  
3.  ソース テーブル側で新しいデータ型を指定します。 データ型の変更が正しく変更テーブルに反映されます。  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

## <a name="data-manipulation-language-modifications"></a>データ操作言語の変更  
 変更データ キャプチャが有効になっているソース テーブルに対して挿入、更新、削除の各操作を実行すると、それらの DML 操作のレコードがデータベース トランザクション ログに表示されます。 変更データ キャプチャのプロセスは、トランザクション ログからそれらの変更に関する情報を取得し、変更を記録する変更テーブルに 1 つまたは 2 つの行を追加します。 エントリは、ソース テーブルでコミットされたときと同じ順序で変更テーブルに追加されますが、変更テーブルのエントリのコミットは通常 1 つのエントリではなく変更のグループに対して実行される必要があります。  
  
 変更テーブル エントリ内、 **_ _ $start_lsn**列を使用して、コミット、ソース テーブルへの変更に関連付けられている LSN を記録し、 **_ _ $$seqval 列**内での変更の並べ替えに使用されますそのトランザクション。 これらのメタデータ列を使用して、ソース変更のコミット順を維持することができます。 キャプチャ プロセスではトランザクション ログから変更情報を取得するため、変更テーブルのエントリが、対応するソース テーブルの変更と同期して表示されていないか確認することが重要です。 代わりに、キャプチャ プロセスがトランザクション ログから関連の変更エントリを処理した後、対応する変更が非同期で表示されます。  
  
 挿入操作と削除操作については、更新マスクのすべてのビットが設定されます。 更新操作の場合、更新操作中に変更された列を反映するため、update old 行と update new 行の両方の更新マスクが変更されます。  
  
## <a name="see-also"></a>参照  
 [sys.sp_cdc_enable_table &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-table-transact-sql.md)   
 [sys.sp_cdc_get_ddl_history &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-get-ddl-history-transact-sql.md)  
  
  
