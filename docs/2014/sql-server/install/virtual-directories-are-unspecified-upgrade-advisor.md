---
title: 仮想ディレクトリが指定されていない (アップグレード アドバイザー) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- virtual directories [Reporting Services]
ms.assetid: 7d32b560-49d6-4558-b5d6-9127067f82d6
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: f5e0643fad0a9e554c3c89f1d1c546a7ab69534d
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66091067"
---
# <a name="virtual-directories-are-unspecified-upgrade-advisor"></a>仮想ディレクトリが指定されていない (アップグレード アドバイザー)
  アップグレード アドバイザーで、レポート サーバー Web サービスまたはレポート マネージャーの仮想ディレクトリ設定が検出されませんでした。 アップグレードの完了後、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーを使用してレポート サーバーの URL 予約を構成する必要があります。  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のネイティブ モード。|  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>説明  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] インストールのアップグレードには、レポート サーバー Web サービスとレポート マネージャーの新しい URL の予約が含まれます。 アップグレードするインスタンスのレポート サーバーまたはレポート マネージャーの仮想ディレクトリが、アップグレード アドバイザーによって検出されませんでした。そのため、アップグレード プロセスでは、アップグレード後のレポート サーバーの URL 予約を作成するための情報が不足しています。 アップグレードを続行できますが、レポート サーバー仮想ディレクトリまたはレポート マネージャー仮想ディレクトリは、アップグレード後のインストールでは未定義になります。  
  
## <a name="corrective-action"></a>修正措置  
 アップグレードの完了後、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーを使用して、レポート サーバーおよびレポート マネージャーの URL を設定します。 IIS マネージャーを使用して、不要になった仮想ディレクトリをすべて削除します。  
  
 詳細については、次を参照してください。 [URL の構成&#40;SSRS 構成マネージャー&#41; ](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md)で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]オンライン ブックの「します。  
  
## <a name="see-also"></a>参照  
 [Reporting Services のアップグレードに関する問題&#40;アップグレード アドバイザー&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
