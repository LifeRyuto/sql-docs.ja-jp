---
title: log_shipping_monitor_alert (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- log_shipping_monitor_alert
- log_shipping_monitor_alert_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- log_shipping_monitor_alert system table
ms.assetid: 1c775e48-9898-4149-b9d1-04d465f23438
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5a97fe48c710fb2945cd377da92808404addd094
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67990078"
---
# <a name="log_shipping_monitor_alert-transact-sql"></a>log_shipping_monitor_alert (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ログ配布の警告ジョブ ID を格納します。 このテーブルは、 **msdb**データベースに格納されます。   
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**alert_job_id**|**uniqueidentifier**|ログ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]配布警告ジョブのエージェントジョブ ID。|  
  
## <a name="see-also"></a>参照  
 [ログ配布について &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [sp_add_log_shipping_alert_job &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-add-log-shipping-alert-job-transact-sql.md)   
 [sp_delete_log_shipping_alert_job &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-delete-log-shipping-alert-job-transact-sql.md)   
 [sp_help_log_shipping_alert_job &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-help-log-shipping-alert-job-transact-sql.md)   
 [システム テーブル &#40;Transact-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
