---
title: 'クイック スタート: 接続し、SQL Server のクエリ'
titleSuffix: Azure Data Studio
description: このクイック スタートは、Azure Data Studio を使用して、SQL Server に接続し、クエリを実行する方法を示しています。
ms.custom: seodec18, sqlfreshmay19
ms.date: 05/14/2019
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: quickstart
author: yualan
ms.author: alayu
manager: jroth
ms.openlocfilehash: af00a85aa1515ae5d43e6842fede00880bf9a573
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66800762"
---
# <a name="quickstart-connect-and-query-sql-server-using-includename-sosincludesname-sos-shortmd"></a>クイック スタート: 接続し、クエリを使用して SQL Server [!INCLUDE[name-sos](../includes/name-sos-short.md)]
このクイック スタートでは、[!INCLUDE[name-sos](../includes/name-sos-short.md)] を使用して SQL Server に接続し、TRANSACT-SQL (T-SQL) ステートメントを使用して、[!INCLUDE[name-sos](../includes/name-sos-short.md)] チュートリアルで使用する *TutorialDB* を作成します。

## <a name="prerequisites"></a>前提条件

このクイック スタートを完了させるためには、[!INCLUDE[name-sos](../includes/name-sos-short.md)] および SQL Server へのアクセスが必要です。

- [[!INCLUDE[name-sos](../includes/name-sos-short.md)]のインストール](download.md)。

SQL Server へのアクセスを持っていない場合は、次のリンクからプラットフォームを選択してください (SQL ログインとパスワードを覚えておくようにしてください)。
- [Windows - SQL Server 2017 Developer Edition のダウンロード](https://www.microsoft.com/sql-server/sql-server-downloads)
- [macOS - Docker で SQL Server 2017 をダウンロードする](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker)
- [Linux - SQL Server 2017 Developer Edition のダウンロード](https://docs.microsoft.com/sql/linux/sql-server-linux-overview#install) - *データを作成しクエリを問い合わせる* ための手順に従うだけです。


## <a name="connect-to-a-sql-server"></a>SQL Server に接続する

   
1. **[!INCLUDE[name-sos](../includes/name-sos-short.md)]** を実行します。
1. 初めて実行する[!INCLUDE[name-sos](../includes/name-sos-short.md)]、**ようこそ**ページを開く必要があります。 表示されない場合、**ようこそ**] ページで、[**ヘルプ** > **ようこそ**。 選択**新しい接続**を開く、**接続**ウィンドウ。
   
   ![新しい接続のアイコン](media/quickstart-sql-server/new-connection-icon.png)

1. この記事では *SQL ログイン*を使用しますが、*Windows 認証*はサポートされています。 次のように、フィールドに入力します。
 
    - **サーバー名:** localhost
    - **認証の種類:** SQL ログイン  
    - **ユーザー名:** SQL Server のユーザー名  
    - **パスワード:** SQL Server のパスワード  
    - **データベース名:** このフィールドを空白のままにします 
    - **サーバー グループ:** \<Default\>  

   ![新しい接続 画面](media/quickstart-sql-server/new-connection-screen.png)



## <a name="create-a-database"></a>データベースの作成

次の手順で **TutorialDB** という名前のデータベースを作成します。

1. サーバーで、右クリック**localhost**、選び**新しいクエリ。**
1. クエリ ウィンドウには、次のスニペットを貼り付けます。 

   ```sql
   USE master
   GO
   IF NOT EXISTS (
      SELECT name
      FROM sys.databases
      WHERE name = N'TutorialDB'
   )
      CREATE DATABASE [TutorialDB];
   GO
   IF SERVERPROPERTY('ProductVersion') > '12'
       ALTER DATABASE [TutorialDB] SET QUERY_STORE=ON;
   GO
   ```
1. クエリを実行するには、次のようにクリックします。**実行**します。

クエリが完了すると、新しい**TutorialDB**データベースの一覧に表示されます。 表示されない場合を右クリックし、**データベース**ノード**更新**します。


## <a name="create-a-table"></a>テーブルの作成

クエリ エディターの接続状態を*マスター*でテーブルを作成するデータベースが、 *TutorialDB*データベース。 

1. 接続コンテキストを変更する**TutorialDB**:

   ![コンテキストの変更](media/quickstart-sql-server/change-context.png)



1. クエリ ウィンドウに次のスニペットを貼り付けて、をクリックして**実行**:

   > [!NOTE]
   > これには、追加したり、エディターで上記のクエリを上書きできます。 クリックする**実行**が選択されている、クエリを実行します。 何も選択されている場合は、クリックして**実行**エディター内のすべてのクエリを実行します。

   ```sql
   -- Create a new table called 'Customers' in schema 'dbo'
   -- Drop the table if it already exists
   IF OBJECT_ID('dbo.Customers', 'U') IS NOT NULL
      DROP TABLE dbo.Customers;
   GO
   -- Create the table in the specified schema
   CREATE TABLE dbo.Customers
   (
       CustomerId  int NOT NULL PRIMARY KEY, -- primary key column
       Name        nvarchar(50) NOT NULL,
       Location    nvarchar(50) NOT NULL,
       Email       nvarchar(50) NOT NULL
   );
   GO
   ```

クエリが完了すると、新しい**顧客**テーブルのテーブルの一覧に表示されます。 右クリックする必要があります、 **TutorialDB > テーブル**ノード**更新**します。

## <a name="insert-rows"></a>行を挿入する

- クエリ ウィンドウに次のスニペットを貼り付けて、をクリックして**実行**:

   ```sql
   -- Insert rows into table 'Customers'
   INSERT INTO dbo.Customers
      ([CustomerId], [Name], [Location], [Email])
   VALUES
      ( 1, N'Orlando', N'Australia', N''),
      ( 2, N'Keith', N'India', N'keith0@adventure-works.com'),
      ( 3, N'Donna', N'Germany', N'donna0@adventure-works.com'),
      ( 4, N'Janet', N'United States', N'janet1@adventure-works.com')
   GO
   ```



## <a name="view-the-data-returned-by-a-query"></a>クエリによって返されるデータを表示します。
1. クエリ ウィンドウに次のスニペットを貼り付けて、をクリックして**実行**:

   ```sql
   -- Select rows from table 'Customers'
   SELECT * FROM dbo.Customers;
   ```

1. クエリの結果が表示されます。

   ![結果を選択します。](media/quickstart-sql-server/select-results.png)


## <a name="next-steps"></a>次の手順
これで SQL Server とクエリの実行に正常に接続した、試し、[コード エディターのチュートリアル](tutorial-sql-editor.md)します。


