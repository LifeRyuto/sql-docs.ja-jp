---
title: Oracle Database への接続 (SSAS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connoracledb.f1
ms.assetid: 9bd177fb-8539-46cd-bf96-189ade52c2a1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8bc5a08d96dbef0bae412b75c9592e4893e12a0f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66087023"
---
# <a name="connect-to-an-oracle-database-ssas"></a>[Oracle データベースへの接続] (SSAS)
  
  **テーブルのインポート ウィザード** のこのページを使用すると、Oracle データベースに接続するための設定を指定できます。 
  [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]からウィザードにアクセスするには、 **[モデル]** メニューの **[データ ソースからのインポート]** をクリックします。  
  
 データ ソースに接続するには、適切なプロバイダーがコンピューターにインストールされている必要があります。  
  
> [!NOTE]  
>  このページでデータベースを選択する際には、現在のユーザーの資格情報が使用されます。 ただし、[権限借用情報] ページで指定されたユーザーに、選択したデータベースの読み取り権限がないと、インポートは成功しません。  
  
## <a name="uielement-list"></a>UI 要素の一覧  
 **[接続の表示名]**  
 このデータ ソース接続の一意の名前を入力します。 これは必須フィールドです。  
  
 **サーバー名**  
 接続するサーバー インスタンスの名前を入力または選択します。  
  
 **ユーザー名**  
 データベース接続に使用するユーザー名を指定します。  
  
 このユーザー名は、データ ソースの接続文字列を構築するときに使用されます。 [テーブルのプロパティ] ウィンドウおよびインポート ウィザードでデータのプレビューまたはフィルター処理を行う際も、これらの資格情報が使用されます。 データをインポートまたは更新する際には、これらの資格情報は使用されず、代わりに [権限借用情報] ページで指定された Windows の資格情報が使用されます。  
  
 **パスワード**  
 データベース接続に使用するパスワードを指定します。  
  
 **[パスワードを保存する]**  
 
  **[パスワード]** ボックスに入力したパスワードを保存するかどうかを指定します。  
  
 **詳細設定**  
 **[詳細プロパティの設定**] ダイアログボックスを使用して、追加の接続プロパティを設定します。 詳細については、「[[詳細プロパティの設定] (SSAS)](set-advanced-properties-ssas.md)」を参照してください。  
  
 **接続のテスト**  
 現在の設定を使用して、データ ソースに対する接続の確立を試みます。 接続が正常に確立されたかどうかを示すメッセージが表示されます。  
  
  
