---
title: SQLRUserGroup - SQL Server Machine Learning サービスのログインを作成します。
description: ループバック接続は暗黙の認証を使用して、ログイン作成 SQL Server の SQLRUserGroup のワーカー アカウントは id の変換、呼び出し元のユーザーに、サーバーにログインできるようにします。
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/25/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 7dafb4c9edfe830a354da61b72d330d800349781
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962352"
---
# <a name="create-a-login-for-sqlrusergroup"></a>SQLRUserGroup のログインｎ作成
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

作成、 [SQL Server のログイン](https://docs.microsoft.com/sql/relational-databases/security/authentication-access/create-a-login)の[SQLRUserGroup](../concepts/security.md#sqlrusergroup)ときに、[ループバック接続をループ](../../advanced-analytics/concepts/security.md#implied-authentication)、スクリプトを指定します、*信頼関係接続*、オブジェクトの実行に使用される id に、コードが含まれている Windows ユーザー アカウントです。

接続がある信頼された`Trusted_Connection=True`接続文字列にします。 SQL Server では、信頼関係接続を指定する要求を受信したときに、現在の Windows ユーザーの id が、ログインを持つかどうかをチェックします。 ワーカー アカウントとして実行すると、外部プロセス用 (から MSSQLSERVER01 など**SQLRUserGroup**)、それらのアカウントでは、既定では、ログインはありませんので、要求は失敗します。

接続エラーを回避するには、ログインを作成して**SQLServerRUserGroup**します。 Id と外部プロセスの詳細については、次を参照してください。[機能拡張フレームワークのセキュリティの概要](../concepts/security.md)します。

> [!Note]
> 必ず**SQLRUserGroup** 「ローカル ログオンを許可」権限します。 既定では、すべての新しいローカル ユーザーにこの権限が与えられますが、一部の組織の厳しいグループ ポリシーには、この権限が無効にする場合があります。

## <a name="create-a-login"></a>ログインを作成します

1. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]のオブジェクト エクスプローラーで、 **[セキュリティ]** を展開し、 **[ログイン]** を右クリックして、 **[新しいログイン]** を選択します。

2. **ログイン - 新規**ダイアログ ボックスで、**検索**します。 (何も入力しないでボックスで、まだ。)
    
     ![Machine learning の新しいログインの追加の検索 をクリックして](media/implied-auth-login1.png "machine learning の新しいログインを追加する検索をクリックします。")

3. **ユーザーまたはグループ**ボックスで、、**オブジェクトの種類**ボタンをクリックします。

     ![Machine learning の新しいログインを追加するオブジェクトの種類を検索](media/implied-auth-login2.png "machine learning の新しいログインを追加するオブジェクトの種類の検索")

4. **オブジェクトの種類**ダイアログ ボックスで、**グループ**します。 その他のすべてのチェック ボックスをオフにします。

     ![オブジェクトの種類 ダイアログ ボックスでグループを選択します](media/implied-auth-login3.png "オブジェクトの種類] ダイアログ ボックスで [グループの選択。")

4. クリックして**詳細**を検索する場所がクリックして、現在のコンピューターであることを確認**検索開始**します。

     ![グループの一覧を取得するには、今すぐ検索](media/implied-auth-login4.png "クリックして検索開始のグループの一覧を取得するには")

5. 以降の 1 つが表示されるまで、サーバー上のグループ アカウントの一覧をスクロール`SQLRUserGroup`します。
    
    + スタート パッド サービスに関連付けられているグループの名前、_既定のインスタンス_は常に**SQLRUserGroup**R または Python をインストールするかどうかに関係なく、します。 このアカウントの既定のインスタンスのみを選択します。
    + 使用する場合、_名前付きインスタンス_、インスタンス名の既定の worker グループの名前、名前に追加されます`SQLRUserGroup`します。 たとえば場合は、インスタンスは、"MLTEST"という名前は、このインスタンスの既定のユーザー グループ名は**SQLRUserGroupMLTest**します。
 
    ![サーバーのグループの例](media/implied-auth-login5.png "サーバー上のグループの例")
   
5. クリックして**OK**高度な検索 ダイアログ ボックスを閉じます。

    > [!IMPORTANT]
    > インスタンスの正しいアカウントを選択したことを確認します。 各インスタンスには、独自のスタート パッド サービスだけとそのサービスに対して作成されたグループを使用できます。 インスタンスは、スタート パッド サービスまたはワーカー アカウントを共有できません。

6. をクリックして**OK**を閉じるにはもう一度、 **[ユーザーまたはグループ**] ダイアログ ボックス。

7. **ログイン - 新規**ダイアログ ボックスで、をクリックして**OK**。 既定では、ログインは **Public** ロールに割り当てられ、データベース エンジンに接続するためのアクセス許可を与えられます。

## <a name="next-steps"></a>次の手順

+ [セキュリティの概要](../concepts/security.md)
+ [機能拡張フレームワーク](../concepts/extensibility-framework.md)
