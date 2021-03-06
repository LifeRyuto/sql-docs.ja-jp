---
title: database_audit_specification_details (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 04/05/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- database_audit_specification_details
- sys.database_audit_specification_details_TSQL
- sys.database_audit_specification_details
- database_audit_specification_details_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.database_audit_specification_details catalog view
ms.assetid: 03fc60a9-1696-4109-b15e-a50046310859
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4dcf9664adcdeba495b53f1a1392781df3fa60bd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67940283"
---
# <a name="sysdatabase_audit_specification_details-transact-sql"></a>database_audit_specification_details (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  すべてのデータベースについてサーバー インスタンス上の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 監査に含まれる、データベース監査仕様に関する情報を含みます。 詳しくは、「[SQL Server Audit &#40;データベース エンジン&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md)」を参照してください。 すべての audit_action_id とその名前の一覧については、 [dm_audit_actions &#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql.md)をクエリします。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**database_specification_id**|**int**|監査仕様の ID。|  
|**audit_action_id**|**int**|監査アクションの ID。|  
|**audit_action_name**|**Sysname**|監査アクションまたは監査アクショングループの名前|  
|**クラス**|**int**|監査対象のオブジェクトのクラスを識別します。|  
|**class_ desc**|**Nvarchar (60)**|監査対象のオブジェクトのクラスの説明です。<br /><br /> -スキーマ<br /><br /> - TABLE|  
|**major_id**|**int**|監査対象のオブジェクトのメジャー ID (テーブル監査アクションのテーブル ID など)。|  
|**minor_id**|**通り**|監査対象のオブジェクトのセカンダリ ID。テーブル監査アクションの列 ID など、クラスに従って解釈されます。|  
|**audited_principal_id**|**int**|監査対象のプリンシパル。|  
|**audited_result**|**Nvarchar (60)**|監査アクションの結果。<br /><br /> - SUCCESS AND FAILURE (成功および失敗) – SUCCESS (成功)<br /><br /> -失敗|  
|**is_group**|**16-bit**|オブジェクトがグループかどうかを示します。<br /><br /> 0 - グループではない<br /><br /> 1 - グループ|  
  
## <a name="permissions"></a>アクセス許可  
 **ALTER ANY DATABASE AUDIT**権限または**VIEW DEFINITION**権限を持つプリンシパル、 **dbo**ロール、および**db_owners**固定データベースロールのメンバーは、このカタログビューにアクセスできます。 また、プリンシパルに対して**VIEW DEFINITION**権限を拒否することはできません。  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]詳細については、「[メタデータ表示の構成](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [CREATE SERVER AUDIT &#40;Transact-sql&#41;](../../t-sql/statements/create-server-audit-transact-sql.md)   
 [ALTER SERVER AUDIT &#40;Transact-sql&#41;](../../t-sql/statements/alter-server-audit-transact-sql.md)   
 [DROP SERVER AUDIT &#40;Transact-sql&#41;](../../t-sql/statements/drop-server-audit-transact-sql.md)   
 [Transact-sql&#41;&#40;のサーバー監査の仕様の作成](../../t-sql/statements/create-server-audit-specification-transact-sql.md)   
 [ALTER SERVER AUDIT SPECIFICATION &#40;Transact-sql&#41;](../../t-sql/statements/alter-server-audit-specification-transact-sql.md)   
 [DROP SERVER AUDIT SPECIFICATION &#40;Transact-sql&#41;](../../t-sql/statements/drop-server-audit-specification-transact-sql.md)   
 [Transact-sql&#41;&#40;データベース監査の仕様の作成](../../t-sql/statements/create-database-audit-specification-transact-sql.md)   
 [Transact-sql&#41;&#40;データベース監査の仕様の変更](../../t-sql/statements/alter-database-audit-specification-transact-sql.md)   
 [Transact-sql&#41;&#40;データベース監査の仕様を削除します。](../../t-sql/statements/drop-database-audit-specification-transact-sql.md)   
 [ALTER AUTHORIZATION &#40;Transact-sql&#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [fn_get_audit_file &#40;Transact-sql&#41;](../../relational-databases/system-functions/sys-fn-get-audit-file-transact-sql.md)   
 [server_audits &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-server-audits-transact-sql.md)   
 [server_file_audits &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-server-file-audits-transact-sql.md)   
 [server_audit_specifications &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-server-audit-specifications-transact-sql.md)   
 [server_audit_specification_details &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-server-audit-specification-details-transact-sql.md)   
 [database_audit_specifications &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-database-audit-specifications-transact-sql.md)   
 [dm_server_audit_status &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-audit-status-transact-sql.md)   
 [dm_audit_actions &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql.md)   
 [dm_audit_class_type_map &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-class-type-map-transact-sql.md)   
 [サーバー監査およびサーバー監査の仕様を作成する方法](../../relational-databases/security/auditing/create-a-server-audit-and-server-audit-specification.md)  
  
  
