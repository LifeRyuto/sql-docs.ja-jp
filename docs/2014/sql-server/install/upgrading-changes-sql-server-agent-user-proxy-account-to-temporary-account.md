---
title: アップグレードと SQL Server エージェント ユーザー プロキシ アカウントが一時的な UpgradedProxyAccount に変更されます |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server Agent]
ms.assetid: cd2d08c3-4e56-4034-8b68-0c78df8b5471
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6e08ed37f94a60e1727dfcd006de7faff0545a23
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62473170"
---
# <a name="upgrading-will-change-the-sql-server-agent-user-proxy-account-to-the-temporary-upgradedproxyaccount"></a>アップグレードすると SQL Server エージェント ユーザーのプロキシ アカウントが一時的な UpgradedProxyAccount に変更される
  ログ配布を有効にしたデータベース メンテナンス プランは、アップグレード後に無効になります。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント  
  
## <a name="description"></a>説明  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] には新しいログ配布関数のセットが用意されており、この関数はデータベース メンテナンス プランと直接的な互換性がありません。  
  
## <a name="corrective-action"></a>修正措置  
 ログ配布関数を含むデータベース メンテナンス プランを [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] で使用していた場合は、新しい関数を使用するようにログ配布を構成する必要があります。 詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックで「ログ配布」を検索してください。  
  
## <a name="see-also"></a>参照  
 [SQL Server エージェント ログ配布ジョブ カテゴリが原因でアップグレードが失敗するには](../../../2014/sql-server/install/sql-server-agent-log-shipping-job-category-causes-upgrade-to-fail.md)   
 [アップグレード後にログ配布が実行されない](../../../2014/sql-server/install/log-shipping-will-not-run-after-upgrading.md)  
  
  
