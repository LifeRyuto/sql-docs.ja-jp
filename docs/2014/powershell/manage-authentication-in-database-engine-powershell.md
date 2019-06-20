---
title: データベース エンジン PowerShell での認証の管理 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: ab9212a6-6628-4f08-a38c-d3156e05ddea
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0992e3a956a2b498d92186fa91c0ed4fbddf6102
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62762044"
---
# <a name="manage-authentication-in-database-engine-powershell"></a>データベース エンジン PowerShell での認証の管理
  既定では、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell コンポーネントは、 [!INCLUDE[ssDE](../includes/ssde-md.md)]インスタンスへの接続に Windows 認証を使用します。 SQL Server 認証を使用するには、PowerShell 仮想ドライブを定義するか、`-Username` の `-Password` および `Invoke-Sqlcmd` パラメーターを指定します。  
  
1.  **作業を開始する準備:**[アクセス許可](#Permissions)  
  
2.  **認証を設定するを使用します。**[仮想ドライブ](#SQLAuthVirtDrv)、 [Invoke-sqlcmd](#SQLAuthInvSqlCmd)  
  
##  <a name="Permissions"></a> Permissions  
 [!INCLUDE[ssDE](../includes/ssde-md.md)] のインスタンスで実行できるすべての操作は、そのインスタンスへの接続に使用された認証資格情報に付与されている権限によって制御されます。 既定では、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] プロバイダーとコマンドレットは、それが実行されている Windows アカウントを使用して、 [!INCLUDE[ssDE](../includes/ssde-md.md)]への Windows 認証接続を行います。  
  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証接続を行うには、SQL Server 認証のログイン ID およびパスワードを指定する必要があります。 使用する場合、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]関連付ける必要があります、プロバイダー、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]ログイン資格情報を仮想ドライブをし、使用してディレクトリの変更コマンド (`cd`) そのドライブに接続します。 Windows PowerShell では、セキュリティ資格情報は仮想ドライブにのみ関連付けることができます。  
  
##  <a name="SQLAuthVirtDrv"></a> 仮想ドライブを使用する SQL Server 認証  
 **SQL Server 認証ログインに関連付けられた仮想ドライブを作成するには**  
  
1.  次のような関数を作成します。  
  
    1.  仮想ドライブに与える名前、ログイン ID、および仮想ドライブに関連付けるプロバイダー パスのためのパラメーターを持っている。  
  
    2.  `read-host` を使用して、ユーザーにパスワードの入力を求める。  
  
    3.  `new-object` を使用して、資格情報オブジェクトを作成する。  
  
    4.  `new-psdrive` を使用して、指定された資格情報で仮想ドライブを作成する。  
  
2.  関数を呼び出して、指定された資格情報で仮想ドライブを作成します。  
  
### <a name="example-virtual-drive"></a>例 (仮想ドライブ)  
 次の例は、指定された **認証ログインおよびインスタンスに関連付けられる仮想ドライブを作成するための、** sqldrive [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] という名前の関数を作成します。  
  
 **sqldrive** 関数は、ユーザーにログインのパスワードの入力を求め、入力されるパスワードをマスクします。 その後、ディレクトリ変更コマンドを使用するたびに (`cd`) を使用して仮想ドライブ名を使用して、パスに接続するにすべての操作の実行、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]ドライブを作成したときに指定した認証ログイン資格情報。  
  
```  
## Create a function that specifies the login and prompts for the password.  
  
function sqldrive  
{  
    param( [string]$name, [string]$login = "MyLogin", [string]$root = "SQLSERVER:\SQL\MyComputer\MyInstance" )  
    $pwd = read-host -AsSecureString -Prompt "Password"  
    $cred = new-object System.Management.Automation.PSCredential -argumentlist $login,$pwd  
    New-PSDrive $name -PSProvider SqlServer -Root $root -Credential $cred -Scope 1  
}  
  
## Use the sqldrive function to create a SQLAuth virtual drive.  
sqldrive SQLAuth  
  
## CD to the virtual drive, which invokes the supplied authentication credentials.  
cd SQLAuth  
```  
  
##  <a name="SQLAuthInvSqlCmd"></a> Invoke-Sqlcmd を使用する SQL Server 認証  
 **SQL Server 認証で Invoke-Sqlcmd を使用するには**  
  
1.  `-Username` パラメーターでログイン ID を指定し、`-Password` パラメーターで関連付けられているパスワードを指定します。  
  
### <a name="example-invoke-sqlcmd"></a>例 (Invoke-Sqlcmd)  
 この例では、read-host コマンドレットを使用してユーザーにパスワードの入力を求め、SQL Server 認証を使用して接続します。  
  
```  
## Prompt the user for their password.  
$pwd = read-host -AsSecureString -Prompt "Password"  
  
Invoke-Sqlcmd -Query "SELECT GETDATE() AS TimeOfQuery;" -ServerInstance "MyComputer\MyInstance" -Username "MyLogin" -Password $pwd  
```  
  
## <a name="see-also"></a>関連項目  
 [SQL Server PowerShell](sql-server-powershell.md)   
 [SQL Server PowerShell プロバイダー](sql-server-powershell-provider.md)   
 [Invoke-Sqlcmd コマンドレット](../database-engine/invoke-sqlcmd-cmdlet.md)  
  
  
