---
title: サブスクリプションの種類 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.newsubwizard.subscriptiontype.f1
ms.assetid: 9a50f588-ee45-4a87-826f-372ff0798587
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: b3809a0f7b3113ccf1c0cfb605ae01655ecdd89e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67928004"
---
# <a name="subscription-type"></a>サブスクリプションの種類
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  マージ レプリケーションでは、サーバーとクライアントという 2 つのサブスクリプションの種類がオファーされます。 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の以前のバージョンでは、これらはグローバルとローカルと呼ばれていました。 サブスクライバーはサーバー サブスクリプションによって次の操作を実行できます。  
  
-   他のサブスクライバーにデータを再パブリッシュする。  
  
-   代わりの同期パートナーを提供する。  
  
-   設定された優先度に応じて競合を解決する。  
  
 ほとんどのサブスクライバーは、この機能を必要とせず、クライアント サブスクリプションを使用できます。 クライアント サブスクリプションは競合の検出と解決ができますが、サブスクライバーには優先度が割り当てられていません。変更によって競合が発生した場合は、変更をパブリッシャーに最初に送信したサブスクライバーが優先されます。  
  
> [!NOTE]  
>  サブスクリプションの種類は、作成後に変更することはできません。  
  
## <a name="options"></a>オプション  
 **[サブスクリプションのプロパティ]**  
 **[サブスクリプションの種類]** 列のドロップダウン リスト ボックスで、各サブスクライバーに対して、 **[クライアント]** または **[サーバー]** を選択します。 サブスクライバーでサーバー サブスクリプションを使用する場合は、 **[競合解決の優先度]** 列に 0 ～ 99.99 の範囲の数値を入力します。数字が大きいほどサブスクライバーに対する優先度が高くなります。  
  
## <a name="see-also"></a>参照  
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [ssSDSFull](../../relational-databases/replication/create-a-push-subscription.md)   
 [パブリケーションのサブスクライブ](../../relational-databases/replication/subscribe-to-publications.md)  
  
  
