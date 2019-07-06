---
title: sys.sp_cdc_cleanup_change_table (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cdc_cleanup_change_table
- sp_cdc_cleanup_change_table_TSQL
- sys.sp_cdc_cleanup_change_table
- sys.sp_cdc_cleanup_change_table_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_cdc_cleanup_change_tables
- sp_cdc_cleanup_change_tables
ms.assetid: 02295794-397d-4445-a3e3-971b25e7068d
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 7bbcc576ab0ff38adde9042a713e0dfd0c7d54be
ms.sourcegitcommit: cff8dd63959d7a45c5446cadf1f5d15ae08406d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/05/2019
ms.locfileid: "67583291"
---
# <a name="sysspcdccleanupchangetable-transact-sql"></a>sys.sp_cdc_cleanup_change_table (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  に基づいて、指定された現在のデータベースの変更テーブルから行を削除します。 *low_water_mark*値。 このストアド プロシージャは、直接変更テーブルのクリーンアップ プロセスを管理するユーザーに提供されます。 ただし、このプロシージャは、変更テーブルに含まれるデータのすべてのコンシューマーに影響を及ぼすため、使用する際は注意が必要です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sys.sp_cdc_cleanup_change_table   
  [ @capture_instance = ] 'capture_instance',   
  [ @low_water_mark = ] low_water_mark ,  
  [ @threshold = ]'delete threshold'  
```  
  
## <a name="arguments"></a>引数  
 [ @capture_instance = ] '*capture_instance*'  
 変更テーブルに関連付けられたキャプチャ インスタンスの名前を指定します。 *capture_instance*は**sysname**、既定値はありません、NULL にすることはできません。  
  
 *capture_instance*現在のデータベースに存在するキャプチャ インスタンス名を指定します。  
  
 [ @low_water_mark = ] *low_water_mark*  
 新しい低水位マークとして使用するログ シーケンス番号 (LSN) は、*キャプチャ インスタンス*します。 *low_water_mark*は**binary (10)** 、既定値はありません。  
  
 現在のエントリの start_lsn 値として表示される必要があります、値が null でない場合、 [cdc.lsn_time_mapping](../../relational-databases/system-tables/cdc-lsn-time-mapping-transact-sql.md)テーブル。 cdc.lsn_time_mapping の他のエントリが、新しい低レベルのウォーターマークで識別されたエントリと同じコミット時間を共有する場合、そのグループのエントリに関連付けられた最小 LSN が低レベルのウォーターマークとして選択されます。  
  
 値が明示的に null の場合、現在に設定されている場合*低レベルのウォーターマーク*の*キャプチャ インスタンス*クリーンアップ操作の上限の境界を定義するために使用します。  
  
 [ @threshold=] '*しきい値を削除*'  
 クリーンアップ時に 1 つのステートメントを使用して削除できるエントリの削除の最大数です。 *delete_threshold*は**bigint**、既定値は 5000 です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>コメント  
 sys.sp_cdc_cleanup_change_table は次の操作を実行します。  
  
1.  場合、@low_water_markパラメーターが NULL でない、start_lsn の値を設定、*キャプチャ インスタンス*を新しい*低レベルのウォーターマーク*します。  
  
    > [!NOTE]  
    >  新しい低レベルのウォーターマークは、ストアド プロシージャ呼び出しで指定されている低レベルのウォーターマークと異なる場合があります。 cdc.lsn_time_mapping テーブルの他のエントリが同じコミット時間を共有する場合、そのグループのエントリで表される最小の start_lsn が、調整された低レベルのウォーターマークとして選択されます。 場合、@low_water_markパラメーターが NULL または現在の低レベルのウォーターマークが新しい低レベルのウォーターマークより大きい、start_lsn 値は、キャプチャ インスタンスのままには変更されません。  
  
2.  変更テーブル エントリが持つ __$start_lsn の値が低レベルのウォーターマークより小さい場合は、その変更テーブル エントリが削除されます。 削除のしきい値を使用して、1 つのトランザクションで削除された行の数を制限できます。 正常にエントリを削除に失敗したレポートされます。 ただし、キャプチャ インスタンス低レベルのウォーターマーク行われた可能性がありますが、呼び出しに基づいてへの変更には影響しません。  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

 sys.sp_cdc_cleanup_change_table は、次のような場合に使用します。  
  
-   クリーンアップ エージェント ジョブのレポートは、エラーを削除します。  
  
     管理者は、失敗した操作を再試行するには、明示的にこのストアド プロシージャを実行できます。 指定したキャプチャ インスタンスのクリーンアップを再試行するには、sys.sp_cdc_cleanup_change_table を実行し、NULL を指定する、@low_water_markパラメーター。  
  
-   クリーンアップ エージェント ジョブで使用される単純な保有期間に基づくポリシーが十分でないです。  
  
     の単一のキャプチャ インスタンスのクリーンアップをこのストアド プロシージャためは、個々 のキャプチャ インスタンスにクリーンアップの規則が調整されたカスタム クリーンアップ戦略の構築に使用できます。  
  
## <a name="permissions"></a>アクセス許可  
 db_owner 固定データベース ロールのメンバーシップが必要です。  
  
## <a name="see-also"></a>参照  
 [cdc.fn_cdc_get_all_changes_&#60;capture_instance&#62;  &#40;TRANSACT-SQL&#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql.md)   
 [sys.fn_cdc_get_min_lsn &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-cdc-get-min-lsn-transact-sql.md)   
 [sys.fn_cdc_increment_lsn &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-cdc-increment-lsn-transact-sql.md)  
  
  
