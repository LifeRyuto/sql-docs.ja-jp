---
title: dm_os_windows_info (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/30/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_os_windows_info
- dm_os_windows_info_TSQL
- sys.dm_os_windows_info
- sys.dm_os_windows_info_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_windows_info dynamic management view
ms.assetid: adc81283-fdc2-46c0-bb48-abe82bbf2459
author: stevestein
ms.author: sstein
ms.openlocfilehash: d25713ba8fb298ce465910eae786befb710961d7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67899592"
---
# <a name="sysdm_os_windows_info-transact-sql"></a>dm_os_windows_info (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Windows オペレーティングシステムのバージョン情報を表示する1行を返します。  
  
  Windows で実行されている SQL Server にのみ適用されます。 Linux など、Windows 以外のホストで実行されている SQL Server について同様のについを表示するには、 [dm_os_host_info &#40;transact-sql&#41;](~/relational-databases/system-dynamic-management-views/sys-dm-os-host-info-transact-sql.md)を使用します。 
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**windows_release**|**nvarchar(256)**|Windows の場合は、リリース番号を返します。 値と説明の一覧については、「[オペレーティングシステムのバージョン (Windows)](/windows/desktop/SysInfo/operating-system-version)」を参照してください。 NULL にすることはできません。|  
|**windows_service_pack_level**|**nvarchar(256)**| Windows の場合、Service Pack 番号を返します。 NULL にすることはできません。 |  
|**windows_sku**|**int**|Windows の場合は、Windows の在庫保持ユニット (SKU) ID を返します。 SKU Id と説明の一覧については、「 [Getproductinfo 関数](https://msdn.microsoft.com/library/ms724358.aspx)」を参照してください。 Null 値は許容されます。 |  
|**os_language_version**|**int**| Windows の場合、オペレーティングシステムの Windows ロケール識別子 (LCID) を返します。 LCID 値と説明の一覧については、「 [Microsoft によって割り当てられたロケール id](https://go.microsoft.com/fwlink/?LinkId=208080)」を参照してください。 NULL にすることはできません。|  
  
  
## <a name="permissions"></a>アクセス許可  
既定では、dm_os_windows_info の SELECT 権限が public ロールに付与されます。 取り消す場合は、サーバーに対する VIEW SERVER STATE 権限が必要です。  

## <a name="limitations-and-restrictions"></a>制限事項と制約事項
Linux など、Windows 以外のホストで実行されている SQL のについを表示するには、 [&#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-host-info-transact-sql.md)を使用 dm_os_host_info ます。 
  
## <a name="examples"></a>例  
 次の例では、 **dm_os_windows_info**ビューからすべての列を返します。  
  
```  
SELECT windows_release, windows_service_pack_level, windows_sku, os_language_version  
FROM sys.dm_os_windows_info;  
```  
  
 次に結果セットの例を示します。  
  
 `windows_release  windows_service_pack_level   windows_sku   os_language_version`  
  
 `---------------  ---------------------------  ------------  -------------------`  
  
 `6.0              Service Pack 2                4            1033`  
  
## <a name="see-also"></a>参照  
 [dm_os_sys_info &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)   
 [sys.dm_os_host_info](../../relational-databases/system-dynamic-management-views/sys-dm-os-host-info-transact-sql.md)  
  
  

