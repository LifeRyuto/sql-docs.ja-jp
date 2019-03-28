---
title: sp_dropdynamicsnapshot_job (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_dropdynamicsnapshot_job_TSQL
- sp_dropdynamicsnapshot_job
helpviewer_keywords:
- sp_dropdynamicsnapshot_job
ms.assetid: 128e428a-01b3-4062-8c6e-d22d5fa268a9
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 04564b2d2830a6bd925a1c334c8026b376d0894f
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58526384"
---
# <a name="spdropdynamicsnapshotjob-transact-sql"></a>sp_dropdynamicsnapshot_job (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  パラメーター化された行フィルターを持つパブリケーションに関する、フィルター選択されたデータ スナップショット ジョブを削除します。 このストアド プロシージャは、パブリッシャー、パブリケーション データベースに対して実行されます。 すべての関連データが削除ジョブが削除されたときに、 [MSdynamicsnapshotjobs](../../relational-databases/system-tables/msdynamicsnapshotjobs-transact-sql.md)システム テーブル。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_dropdynamicsnapshot_job [ @publication = ] 'publication'   
    [ , [ @dynamic_snapshot_jobname = ] 'dynamic_snapshot_jobname' ]   
    [ , [ @dynamic_snapshot_jobid = ] 'dynamic_snapshot_jobid' ]   
    [ , [ @ignore_distributor =] ignore_distributor ]  
```  
  
## <a name="arguments"></a>引数  
`[ @publication = ] 'publication'` フィルター選択されたデータ スナップショット ジョブの削除元となるパブリケーションの名前です。 *パブリケーション* は **sysname** 、既定値はありません。  
  
`[ @dynamic_snapshot_jobname = ] 'dynamic_snapshot_jobname'` フィルター選択されたデータ スナップショット ジョブの名前を削除しています。 *dynamic_snapshot_jobname*が sysname で、既定の設定でない場合にどのようなジョブ名に関連付けられている*dynamic_snapshot_jobid*します。  
  
`[ @dynamic_snapshot_jobid = ] 'dynamic_snapshot_jobid'` フィルター選択されたデータ スナップショット ジョブの識別子を削除しています。 *dynamic_snapshot_jobid*は**uniqueidentifier**、既定値は NULL です。  
  
> [!IMPORTANT]  
>  のみ*dynamic_snapshot_jobid*または*dynamic_snapshot_jobname*を指定できます。 いずれかの値が指定されなかった場合*dynamic_snapshot_jobid*または*dynamic_snapshot_jobname*パブリケーションのすべての動的スナップショット ジョブが削除されます。  
  
`[ @ignore_distributor = ] ignore_distributor` *ignore_distributor*は**ビット**、既定値は**0**します。 このパラメーターは、ディストリビューターでクリーンアップを実行せずに動的スナップショット ジョブを削除する場合に使用できます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_dropdynamicsnapshot**はマージ レプリケーションで使用します。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_dropdynamicsnapshot**します。  
  
## <a name="see-also"></a>参照  
 [sp_adddynamicsnapshot_job &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddynamicsnapshot-job-transact-sql.md)  
  
  
