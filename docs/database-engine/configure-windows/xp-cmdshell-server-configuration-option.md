---
title: xp_cmdshell サーバー構成オプション | Microsoft Docs
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- xp_cmdshell
ms.assetid: c147c9e1-b81d-49c8-b800-3019f4d86a13
author: MikeRayMSFT
ms.author: mikeray
manager: jroth
ms.openlocfilehash: 4679a937c99dcf4e58fa1b8184de48f189663980
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66775048"
---
# <a name="xpcmdshell-server-configuration-option"></a>xp_cmdshell サーバー構成オプション
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  **xp_cmdshell** オプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] xp_cmdshell **拡張ストアド プロシージャをシステムで実行できるかどうかをシステム管理者が制御できるようにする、** のサーバー構成オプションです。 新規インストールの場合、**xp_cmdshell** オプションは既定で無効になっています。 このオプションを有効にする前に、このオプションを使用した場合に関連する潜在的なセキュリティの影響を考慮することが重要です。 通常、このオプションは無効のままにする必要があるため、新しく開発するコードではこのオプションを使用しないでください。 一部のレガシ アプリケーションでは、このオプションを有効にする必要があります。このオプションを使用しないように変更できない場合は、ポリシー ベースの管理を使用するか、次のコード例に示すように **sp_configure** システム ストアド プロシージャを実行して有効にすることができます。  
  
```  
-- To allow advanced options to be changed.  
EXEC sp_configure 'show advanced options', 1;  
GO  
-- To update the currently configured value for advanced options.  
RECONFIGURE;  
GO  
-- To enable the feature.  
EXEC sp_configure 'xp_cmdshell', 1;  
GO  
-- To update the currently configured value for this feature.  
RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [サーバー構成オプション &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [ポリシー ベースの管理を使用したサーバーの管理](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  
