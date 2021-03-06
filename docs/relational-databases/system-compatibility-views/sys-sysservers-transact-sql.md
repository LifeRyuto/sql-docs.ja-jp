---
title: システムの sysservers (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sysservers
- sysservers_TSQL
- sysservers
- sys.sysservers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysservers system table
- sys.sysservers compatibility view
ms.assetid: d02f186f-c00f-44a6-b38d-dc78a3d2145b
author: rothja
ms.author: jroth
ms.openlocfilehash: 333be9cb6c86c1db3801ac50159610c6d19d1611
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68941101"
---
# <a name="syssysservers-transact-sql"></a>システムの sysservers (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスが OLE DB データ ソースとしてアクセスできるサーバーごとに、1 行のデータを格納します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**srvid**|**smallint**|リモートサーバーの ID (ローカルでのみ使用)。|  
|**srvstatus**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**srvname**|**sysname**|サーバー名。|  
|**srvproduct**|**sysname**|リモート サーバーの製品名。|  
|**プロバイダー**|**nvarchar(128**|サーバーへのアクセスを提供する OLE DB プロバイダー名。|  
|**ソース**|**nvarchar(4000)**|データソース値を OLE DB します。|  
|**設置**|**nvarchar(4000)**|OLE DB の場所の値です。|  
|**providerstring**|**nvarchar(4000)**|OLE DB プロバイダーの文字列値。|  
|**schemadate**|**DATETIME**|この行が最後に更新された日付。|  
|**topologyx**|**int**|使用されません。|  
|**topologyy**|**int**|使用されません。|  
|**カタログ**|**sysname**|OLE DB プロバイダーへの接続が確立されるときに使用されるカタログ。|  
|**srvcollation**|**sysname**|サーバーの照合順序。|  
|**connecttimeout**|**int**|サーバー接続のタイムアウト設定です。|  
|**querytimeout**|**int**|サーバーに対するクエリのタイムアウト設定です。|  
|**srvnetname 名**|**char (30)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**isremote**|**bit**|1 = サーバーはリモートサーバーです。<br /><br /> 0 = サーバーはリンクサーバーです。|  
|**rpc-epmap**|**bit**|1 = **rpc\@** が**true**または on に設定され**て**sp_serveroption。<br /><br /> 0 = **sp_serveroption\@rpc**が**false**または**off**に設定されています。|  
|**pub**|**bit**|1 = **sp_serveroption\@pub**が**true**または**on**に設定されています。<br /><br /> 0 = **sp_serveroption\@pub**が**false**または**off**に設定されています。|  
|**サブ**|**bit**|1 = **sp_serveroption\@sub**が**true**または**on**に設定されています。<br /><br /> 0 = **sp_serveroption\@sub**を**false**または**off**に設定します。|  
|**dist**|**bit**|1 = **sp_serveroption\@dist**が**true**または**on**に設定されています。<br /><br /> 0 = **sp_serveroption\@dist**が**false**または**off**に設定されています。|  
|**dpub**|**bit**|1 = **sp_serveroption\@dpub**が**true**または**on**に設定されています。<br /><br /> 0 = **sp_serveroption\@dpub**が**false**または**off**に設定されています。|  
|**rpcout**|**bit**|1 = **sp_serveroption\@rpc out**が**true**または**on**に設定されています。<br /><br /> 0 = **sp_serveroption\@rpc out**が**false**または**off**に設定されています。|  
|**dataaccess**|**bit**|1 = **sp_serveroption\@データアクセス**が**true**または**on**に設定されています。<br /><br /> 0 = **sp_serveroption\@データアクセス**が**false**または**off**に設定されています。|  
|**collationcompatible**|**bit**|1 = **sp_serveroption\@照合順序互換**に設定**true**または**on**です。<br /><br /> 0 = **sp_serveroption\@照合順序互換**に設定**false**または**オフ**です。|  
|**system**|**bit**|1 = **sp_serveroption\@システム**が**true**または**on**に設定されています。<br /><br /> 0 = **sp_serveroption\@システム**が**false**または**off**に設定されています。|  
|**useremotecollation**|**bit**|1 =**リモート\@照合順序**が**true**または**on**に設定されて sp_serveroption。<br /><br /> 0 =**リモート\@照合順序**を**false**または**off**に設定 sp_serveroption ます。|  
|**lazyschemavalidation**|**bit**|1 = **sp_serveroption\@lazy schema validation**を**true**または**on**に設定します。<br /><br /> 0 = **sp_serveroption\@lazy schema validation**を**false**または**off**に設定します。|  
|**規則**|**sysname**|**Sp_serveroption\@の照合順序名**によって設定されたサーバーの照合順序。|  
|**非 sqlsub**|bit|0 = サーバーは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンス。<br /><br /> 1 = サーバーはのインスタンスではありません。[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
  
## <a name="see-also"></a>参照  
 [システムビューへのシステムテーブルのマッピング &#40;Transact-sql&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [互換性ビュー &#40;Transact-sql&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
