---
title: データベースの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- databases [SQL Server], creating
- database creation [SQL Server], SQL Server Management Studio
- creating databases
ms.assetid: 4c4beea2-6cbc-4352-9db6-49ea8130bb64
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d93e6cfa3ce6e958b31c1156cd4fc5fa046ad5ee
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62872333"
---
# <a name="create-a-database"></a>データベースの作成
  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、データベースを作成する方法について説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [前提条件](#Prerequisites)  
  
     [Recommendations (推奨事項)](#Recommendations)  
  
     [セキュリティ](#Security)  
  
-   **以下を使用してデータベースを作成するには:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスには、最大 32,767 個のデータベースを指定できます。  
  
###  <a name="Prerequisites"></a> 前提条件  
  
-   CREATE DATABASE ステートメントは自動コミット モード (既定のトランザクション管理モード) で実行する必要があり、明示的または暗黙的なトランザクション モードでは許可されません。  
  
###  <a name="Recommendations"></a> 推奨事項  
  
-   [Master](master-database.md)データベースは、ユーザーデータベースが作成、変更、または削除されるたびにバックアップする必要があります。  
  
-   データベースを作成する際に、データ ファイルのサイズは、データベースに記述されるデータの最大量を基に可能な限り大きく設定しておきます。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 master データベースの CREATE DATABASE 権限か、CREATE ANY DATABASE 権限または ALTER ANY DATABASE 権限が必要です。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンス上のディスク使用量を管理するため、通常、データベースを作成する権限をいくつかのログイン アカウントに制限します。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-create-a-database"></a>データベースを作成するには  
  
1.  **オブジェクトエクスプローラー**で、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスに接続し、そのインスタンスを展開します。  
  
2.  [**データベース**] を右クリックし、[**新しいデータベース**] をクリックします。  
  
3.  
  **[新しいデータベース]** ダイアログ ボックスで、データベース名を入力します。  
  
4.  すべての既定値をそのまま使用してデータベースを作成するには、 **[OK]** をクリックします。変更する場合は、次に示すオプションの手順を続けて行います。  
  
5.  所有者名を変更するには、参照ボタン **[...]** をクリックし、別の所有者を選択します。  
  
    > [!NOTE]  
    >  
  **以降のバージョンでは、すべてのユーザー データベースでフルテキストが有効になっているため、** [フルテキスト インデックスを使用する] [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]オプションは常にオンに設定され、淡色表示されます。  
  
6.  プライマリ データ ファイルとトランザクション ログ ファイルの既定値を変更するには、 **[データベース ファイル]** グリッドで該当するセルをクリックし、新しい値を入力します。 詳細については、「 [データベースに対するデータ ファイルまたはログ ファイルの追加](add-data-or-log-files-to-a-database.md)」をご覧ください。  
  
7.  データベースの照合順序を変更するには、 **[オプション]** ページをクリックし、[照合順序] ボックスの一覧から照合順序を選択します。  
  
8.  復旧モデルを変更するには、 **[オプション]** ページをクリックし、[復旧モデル] ボックスの一覧から復旧モデルを選択します。  
  
9. データベースのオプションを変更するには、 **[オプション]** ページをクリックし、データベースのオプションを変更します。 各オプションの詳細については、「[ALTER DATABASE の SET オプション &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)」を参照してください。  
  
10. 新しいファイル グループを追加するには、 **[ファイル グループ]** ページをクリックします。 
  **[追加]** をクリックし、ファイル グループを表す新しい値を入力します。  
  
11. 拡張プロパティをデータベースに追加するには、 **[拡張プロパティ]** ページをクリックします。  
  
    1.  
  **[名前]** 列に、拡張プロパティを表す名前を入力します。  
  
    2.  
  **[値]** 列に、拡張プロパティのテキストを入力します。 たとえば、データベースを説明する 1 つ以上のステートメントを入力します。  
  
12. データベースを作成するには、 **[OK]** をクリックします。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-create-a-database"></a>データベースを作成するには  
  
1.  [!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。 この例では、 `Sales`データベースを作成します。 PRIMARY キーワードが使用されていないので、最初のファイル (`Sales`_`dat`) がプライマリ ファイルになります。 
  `Sales`
  \_
  `dat` ファイルの SIZE パラメーターに MB も KB も指定されていないため、ファイルは MB を使用し、メガバイト単位で割り当てられます。 
  `Sales`
  \_
  `log` ファイルは、 `MB` パラメーターに `SIZE` サフィックスが明示的に指定されているため、メガバイト単位で割り当てられます。  
  
```sql  
USE master ;  
GO  
CREATE DATABASE Sales  
ON   
( NAME = Sales_dat,  
    FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\saledat.mdf',  
    SIZE = 10,  
    MAXSIZE = 50,  
    FILEGROWTH = 5 )  
LOG ON  
( NAME = Sales_log,  
    FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\salelog.ldf',  
    SIZE = 5MB,  
    MAXSIZE = 25MB,  
    FILEGROWTH = 5MB ) ;  
GO  
```  
  
 詳細については、「[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [データベースファイルとファイルグループ](database-files-and-filegroups.md)   
 [データベースのデタッチとアタッチ &#40;SQL Server&#41;](database-detach-and-attach-sql-server.md)   
 [ALTER DATABASE &#40;Transact-sql&#41;](/sql/t-sql/statements/alter-database-transact-sql)   
 [データベースに対するデータ ファイルまたはログ ファイルの追加](add-data-or-log-files-to-a-database.md)  
  
  
