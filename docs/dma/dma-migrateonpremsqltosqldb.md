---
title: オンプレミスの SQL Server または Azure Vm 上の SQL Server を Azure SQL Database を使用して移行 Data Migration Assistant |Microsoft Docs
description: Data Migration Assistant を使用して Azure SQL Database に、オンプレミスの SQL Server を移行する方法について説明します
ms.custom: ''
ms.date: 03/12/2019
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, on-premises SQL Server
ms.assetid: ''
author: HJToland3
ms.author: rajpo
manager: jroth
ms.openlocfilehash: 592b581ae4981e42bea2f6bf6f9135018917b002
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66794354"
---
# <a name="migrate-on-premises-sql-server-or-sql-server-on-azure-vms-to-azure-sql-database-using-the-data-migration-assistant"></a>Data Migration Assistant を使用して Azure SQL Database へのオンプレミスの SQL Server または Azure Vm 上の SQL Server を移行します。

Data Migration Assistant は、Azure Vm または Azure SQL Database で SQL Server オンプレミスと以降のバージョンの SQL Server へのアップグレードまたは SQL Server への移行のシームレスな評価を提供します。

Data Migration Assistant を使用して Azure SQL Database に移行する SQL Server をオンプレミスの詳細な手順を説明します。   

## <a name="create-a-new-migration-project"></a>新しい移行プロジェクトを作成します。

1. 左側のウィンドウで次のように選択します。**新規**(+) を選び、**移行**プロジェクトの種類。

2. ソースの種類を設定**SQL Server**と型をターゲット サーバー **Azure SQL Database**します。

3. **[作成]** を選択します。

   ![移行プロジェクトを作成します。](../dma/media/NewCreate1.png)

## <a name="specify-the-source-server-and-database"></a>移行元サーバーとデータベースを指定します。

1. ソースの下で**ソース サーバーへの接続**の**サーバー名**テキスト ボックスに、ソース SQL Server インスタンスの名前を入力します。

2. 選択、**認証の種類**ソース SQL Server のインスタンスによってサポートされています。

   > [!NOTE]
   > Recommedned を選択して、接続を暗号化することは、**接続を暗号化**下のチェック ボックス**接続 poperties**します。

    ![移行元サーバーを選択します。](../dma/media/select-source-server.png)

3. **[接続]** を選択します。

4. Azure SQL Database に移行する 1 つのソース データベースを選択します。

   > [!NOTE]
   > データベースとビューを評価し、適用したい場合は、移行を選択する前に修正プログラムをお勧めします、**移行する前にデータベースを評価するでしょうか。** チェック ボックスをオンします。

    ![ソース データベースを選択します。](../dma/media/select-source-database.png)

5. **[次へ]** を選択します。

## <a name="specify-the-target-server-and-database"></a>ターゲット サーバーとデータベースを指定します。

1. ターゲットには、**ターゲット サーバーへの接続**の**サーバー名**テキスト ボックスに、Azure SQL Database インスタンスの名前を入力します。 

2. 選択、**認証の種類**ターゲット Azure SQL Database インスタンスによってサポートされています。

   > [!NOTE]
   > Recommedned を選択して、接続を暗号化することは、**接続を暗号化**下のチェック ボックス**接続 poperties**します。

     ![ターゲット サーバーの選択](../dma/media/select-target-server.png)

3. **[接続]** を選択します。

4. 移行する先の 1 つのターゲット データベースを選択します。

   > [!NOTE]
   > Windows ユーザーを移行する場合、**ターゲット外部ユーザーのドメイン名**テキスト ボックスに、ターゲット外部ユーザーのドメイン名が正しく指定されていることを確認します。

    ![ターゲット データベースを選択します。](../dma/media/select-target-database.png)

5. **[次へ]** を選択します。

## <a name="select-schema-objects"></a>スキーマ オブジェクトを選択します。

1.  Azure SQL Database に移行するソース データベースからスキーマ オブジェクトを選択します。

    ![スキーマ オブジェクトを選択します。](../dma/media/select-schema-objects.png)

       > [!NOTE]
       > いくつかのオブジェクトに変換できません-が自動修正の機会が表示されます。 左側のウィンドウでこれらのオブジェクトをクリックすると、右側のウィンドウで修正案が表示されます。 修正プログラムを確認し、適用、オブジェクトのすべての変更を無視するかを選択します。 適用することに注意してください。 または、1 つのオブジェクトのすべての変更を無視しても、他のデータベース オブジェクトへの変更は影響しません。 変換または自動的に修正できないステートメントはターゲット データベースに再現し、コメントされています。

    ![推奨される修正プログラム](../dma/media/suggested-fix.png)

2. 選択**一般的な SQL スクリプト**します。
 
3. 生成されたスクリプトを確認します。

    ![生成されるスクリプト](../dma/media/generated-script.png)

## <a name="deploy-schema"></a>スキーマを配置します。

1. 選択**Deploy schema**します。

2. スキーマの展開の結果を確認します。
 
    ![スキーマのデプロイの結果](../dma/media/schema-deployment-results.png)

3. 選択**データ移行**データ移行プロセスを開始します。
 
4. テーブルに移行するデータを選択します。

    ![移行するテーブルの選択](../dma/media/select-tables-to-migrate.png) 

5. 選択**データ移行を開始**します。
 
最後の画面には、全体的な状態が表示されます。

   ![移行の状態](../dma/media/migration-status.png) 

## <a name="see-also"></a>関連項目

- [Data Migration Assistant (DMA)](../dma/dma-overview.md)
- [Data Migration Assistant:構成設定](../dma/dma-configurationsettings.md)
- [Data Migration Assistant:ベスト プラクティス](../dma/dma-bestpractices.md)
