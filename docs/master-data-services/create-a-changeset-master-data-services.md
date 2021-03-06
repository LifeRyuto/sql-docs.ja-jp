---
title: 変更セットを作成する
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: cfad6f1c-9125-4896-b5f5-a4b9f9593cc4
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 859eb2c829b7d6f35aa39cb2301a4a380c0d039e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "73729624"
---
# <a name="create-a-changeset-master-data-services"></a>変更セットを作成する (マスター データ サービス)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  変更セットは、マスター データに対する保留中の変更のコレクションです。 エンティティに変更の承認が必要な場合、保留中の変更は、変更セットに保存してから、管理者の承認を得るために送信する必要があります。  
  
## <a name="prerequisites"></a>前提条件  
  
-   [エクスプローラー] 機能領域にアクセスする権限が必要です。 詳細については、「[機能領域のアクセス許可 &#40;マスターデータサービス](../master-data-services/functional-area-permissions-master-data-services.md)」を参照してください&#41;  
  
-   少なくとも、エンティティまたはその属性のいずれかに対する読み取りアクセス権が必要です。  
  
## <a name="to-create-a-local-changeset"></a>ローカルの変更セットを作成するには  
  
1.  
  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] のホーム ページで、モデルとバージョンを選択し、 **[エクスプローラー]** をクリックします。  
  
2.  
  **[エンティティ]** メニューでエンティティをクリックします。  
  
3.  右側のウィンドウで **[変更セット]** を選択し、 **[作成]** をクリックします。  
  
4.  変更セットの名前を入力し、 **[保存]** をクリックします。  
  
     変更セットの名前は、モデル内で一意である必要があります。  
  
## <a name="to-create-a-changeset-for-approval"></a>承認のための変更セットを作成するには  
  
1.  
  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] のホーム ページで、モデルとバージョンを選択し、 **[エクスプローラー]** をクリックします。  
  
2.  
  **[エンティティ]** メニューでエンティティをクリックします。  
  
3.  エンティティに変更を加え、**[OK]** をクリックします。  
  
4.  **[変更セットの選択**] ダイアログボックスが表示されます。  
  
5.  
  **[新規]** をクリックし、変更セットの名前を入力して、 **[保存]** をクリックします。 変更セットの名前は、モデル内で一意である必要があります。  
  
6.  既存の変更セットを使用するには、 **[既存]** をクリックし、一覧から変更セットを選択します。 オープンまたは拒否の状態の変更セットのみを使用できます。  
  
## <a name="next-steps"></a>次の手順  
 [変更セットの適用および更新 &#40;マスターデータサービス&#41;](../master-data-services/apply-and-update-a-changeset-master-data-services.md)  
  
## <a name="see-also"></a>参照  
 [変更セット &#40;マスターデータサービスのコミットまたは送信&#41;](../master-data-services/commit-or-submit-a-changeset-master-data-services.md)   
 [変更セット &#40;マスターデータサービスを承認または拒否する&#41;](../master-data-services/approve-or-reject-a-changeset-master-data-services.md)  
  
  
