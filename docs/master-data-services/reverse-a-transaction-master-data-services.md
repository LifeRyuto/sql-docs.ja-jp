---
title: トランザクションを破棄する
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- transactions [Master Data Services], reversing
ms.assetid: 6f7c3f07-0f64-4283-8c9c-93facd00a046
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 870341b6ae6a3ffbda345aa7a0abc4a2fe253ac5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "73728930"
---
# <a name="reverse-a-transaction-master-data-services"></a>トランザクションを破棄する (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、管理者は、アクションを元に戻す必要があるときにトランザクションを破棄できます。 トランザクションの例としては、属性値の変更、階層の移動、メンバーの削除などがあります。 このページには、トランザクション ログの種類が "属性" であるエンティティのトランザクションのみを表示します。 エクスプローラー ページに移動して、トランザクション ログの種類が "メンバー" であるエンティティの履歴を表示します。  
  
## <a name="prerequisites"></a>前提条件  
  
-   [**バージョン管理**] 機能領域にアクセスするためのアクセス許可が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「 [管理者 (マスター データ サービス)](../master-data-services/administrators-master-data-services.md)にアクセスすることなくグループに対してユーザーの追加または削除を行うことができます。  
  
### <a name="to-reverse-a-transaction"></a>トランザクションを破棄するには  
  
1.  
  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] ホーム ページで、 **[バージョン管理]** をクリックします。  
  
2.  メニュー バーの **[トランザクション]** をクリックします。  
  
3.  
  **[トランザクション]** ページで、 **[モデル]** ボックスの一覧からモデルを選択します。  
  
4.  
  **[バージョン]** ボックスの一覧からバージョンを選択します。  
  
5.  破棄するトランザクションのグリッド内の行をクリックします。  
  
6.  
  **[トランザクションの破棄]** をクリックします。  
  
7.  確認のダイアログ ボックスで **[OK]** をクリックします。 破棄されたトランザクションを記録するために、別のトランザクションがグリッドに追加されます。  
  
## <a name="see-also"></a>参照  
 [トランザクション &#40;マスターデータサービス&#41;](../master-data-services/transactions-master-data-services.md)   
 [メンバーまたはコレクションを再アクティブ化する &#40;マスターデータサービス&#41;](../master-data-services/reactivate-a-member-or-collection-master-data-services.md)  
 [メンバー リビジョン履歴のロールバック](../master-data-services/rollback-member-revision-history-master-data-services.md)
  
  
