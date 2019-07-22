---
title: アクティブなリースを保持しているバックアップ BLOB ファイルの削除 | Microsoft Docs
ms.custom: ''
ms.date: 08/17/2017
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 13a8f879-274f-4934-a722-b4677fc9a782
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 68805810e0227e4b4d2544ef714c323f9bff3353
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68068514"
---
# <a name="delete-backup-blob-files-with-active-leases"></a>アクティブなリースを保持しているバックアップ BLOB ファイルを削除する
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Microsoft Azure Storage へのバックアップまたは Microsoft Azure Storage からの復元を実行するときに、SQL Server は BLOB への排他アクセスをロックするために無限リースを取得します。 バックアップまたは復元プロセスが正常に完了すると、リースは解放されます。 バックアップまたは復元に失敗すると、バックアップ プロセスは無効な BLOB のクリーンアップを試みます。 ただし、バックアップの失敗の原因が長期的または持続的なネットワーク接続エラーの場合は、バックアップ プロセスは BLOB にアクセスできず、BLOB は孤立したままになる可能性があります。 つまり、リースが解放されるまで、BLOB を書き込むことも削除することもできません。 このトピックでは、リースを解放 (終了) する方法と BLOB の削除について説明します。 
  
 リースの種類について詳しくは、[こちらの記事](https://go.microsoft.com/fwlink/?LinkId=275664)をご覧ください。  
  
 バックアップ操作が失敗すると、無効なバックアップ ファイルが生成されます。 また、バックアップ BLOB ファイルでは、削除や上書きを防ぐためにアクティブなリースを保持する場合もあります。 そのような BLOB を削除または上書きするには、先にリースを解放 (終了) する必要があります。 バックアップに問題がある場合は、リースをクリーンアップして BLOB を削除することをお勧めします。 記憶域管理タスクの一環として、リースのクリーンアップと BLOB の削除を定期的に行うこともできます。  
  
 復元エラーが発生した場合、後続の復元はブロックされないため、アクティブなリースは問題にならないことがあります。 リースを終了する必要があるのは、BLOB を上書きまたは削除する場合だけです。  
  
## <a name="manage-orphaned-blobs"></a>孤立した BLOB の管理  
 次の手順では、バックアップ動作または復元動作の失敗後にクリーンアップする方法について説明します。 すべての手順は、PowerShell スクリプトを使って実行できます。 次のセクションでは、PowerShell スクリプトの例が示されています。  
  
1.  **リースを保持している BLOB を識別する:** バックアップ プロセスを実行するスクリプトまたはプロセスがあると、スクリプトまたはプロセス内のエラーをキャプチャし、それを使って BLOB をクリーンアップできる場合があります。  また、LeaseStats プロパティと LeastState プロパティを使って、それらのプロパティに対してリースを保持している BLOB を識別することもできます。 BLOB を識別したら、一覧を確認し、BLOB を削除する前にバックアップ ファイルが有効かどうかを確認します。  
  
2.  **リースを終了する:** 承認された要求では、リース ID を指定せずにリースを終了できます。 詳細については、 [こちら](https://go.microsoft.com/fwlink/?LinkID=275664) をご覧ください。  
  
    > [!TIP]  
    >  SQL Server は、復元操作中にリース ID を発行して排他アクセスを確立します。 復元のリース ID は BAC2BAC2BAC2BAC2BAC2BAC2BAC2BAC2 です。  
  
3.  **BLOB を削除する:** アクティブなリースを保持している BLOB を削除するには、最初にリースを終了する必要があります。  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

###  <a name="Code_Example"></a> PowerShell スクリプトの例  
  
> [!IMPORTANT]
>  PowerShell 2.0 を実行している場合、Microsoft WindowsAzure.Storage.dll アセンブリの読み込み中に問題が発生することがあります。 この問題を解決するには、[PowerShell](https://docs.microsoft.com/powershell/) をアップグレードすることをお勧めします。 また、PowerShell 2.0 では次の回避策を使用することもできます。  
> 
>  -   次のスクリプトを使用して実行時に .NET 2.0 アセンブリと .NET 4.0 アセンブリを読み込むように powershell.exe.config ファイルを作成または変更する:  
> 
>     ```  
>     \<?xml version="1.0"?>   
>     <configuration>   
>         <startup useLegacyV2RuntimeActivationPolicy="true">   
>             <supportedRuntime version="v4.0.30319"/>   
>             <supportedRuntime version="v2.0.50727"/>   
>         </startup>   
>     </configuration>  
> 
>     ```  
  
 次に示すスクリプトの例では、アクティブなリースを保持している BLOB を識別し、それを終了しています。 この例は、リリースのリース ID をフィルター選択する方法も示します。  
  
**このスクリプトの実行に関するヒント**  
  
> [!WARNING]  
>  Microsoft Azure BLOB ストレージ サービスへのバックアップをこのスクリプトと同時に実行すると、バックアップは失敗する場合があります。これは、このスクリプトで終了するリースを、同時にバックアップが取得しようとしているためです。 このスクリプトは、保守期間中、バックアップが実行されていないとき、またはバックアップの実行が予期されていないときに実行します。  
  
1.  このスクリプトを実行すると、ストレージ アカウント、ストレージ キー、コンテナー、および Azure ストレージ アセンブリのパスと名前のパラメーターの値を指定するように求められます。 ストレージ アセンブリのパスは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスのインストール ディレクトリです。 ストレージ アセンブリのファイル名は Microsoft.WindowsAzure.Storage.dll です。 次に、入力するプロンプトと値の例を示します。  
  
    ```  
    cmdlet  at command pipeline position 1  
    Supply values for the following parameters:  
    storageAccount: mycloudstorageaccount  
    storageKey: 0BopKY7eEha3gBnistYk+904nf  
    blobContainer: mycontainer   
    storageAssemblyPath: C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn\Microsoft.WindowsAzure.Storage.dll  
    ```  
  
2.  リースがロックされている BLOB がない場合は、次のメッセージが表示されます。  
  
     **ロックされたリースの状態の BLOB はありません**  
  
     リースがロックされている BLOB がある場合は、次のメッセージが表示されます。  
  
     **リースを終了しています**  
  
     **\<BLOB の URL> のリースは復元リースです:このメッセージが表示されるのは、まだアクティブな復元リースを保持している BLOB がある場合のみです。**  
  
     **\<BLOB の URL> のリースは復元リースではありません。\<BLOB の URL>** のリースを終了しています。  
  
```  
param(  
       [Parameter(Mandatory=$true)]  
       [string]$storageAccount,  
       [Parameter(Mandatory=$true)]  
       [string]$storageKey,  
       [Parameter(Mandatory=$true)]  
       [string]$blobContainer,  
       [Parameter(Mandatory=$true)]  
       [string]$storageAssemblyPath  
)  
  
# Well known Restore Lease ID  
$restoreLeaseId = "BAC2BAC2BAC2BAC2BAC2BAC2BAC2BAC2"  
  
# Load the storage assembly without locking the file for the duration of the PowerShell session  
$bytes = [System.IO.File]::ReadAllBytes($storageAssemblyPath)  
[System.Reflection.Assembly]::Load($bytes)  
  
$cred = New-Object 'Microsoft.WindowsAzure.Storage.Auth.StorageCredentials' $storageAccount, $storageKey  
  
$client = New-Object 'Microsoft.WindowsAzure.Storage.Blob.CloudBlobClient' "https://$storageAccount.blob.core.windows.net", $cred  
  
$container = $client.GetContainerReference($blobContainer)  
  
#list all the blobs  
$allBlobs = $container.ListBlobs($null,$true) 
  
$lockedBlobs = @()  
# filter blobs that are have Lease Status as "locked"  
foreach($blob in $allBlobs)  
{  
    $blobProperties = $blob.Properties   
    if($blobProperties.LeaseStatus -eq "Locked")  
    {  
        $lockedBlobs += $blob  
  
    }  
}  
  
if ($lockedBlobs.Count -eq 0)  
    {   
        Write-Host " There are no blobs with locked lease status"  
    }  
if($lockedBlobs.Count -gt 0)  
{  
    write-host "Breaking leases"  
    foreach($blob in $lockedBlobs )   
    {  
        try  
        {  
            $blob.AcquireLease($null, $restoreLeaseId, $null, $null, $null)  
            Write-Host "The lease on $($blob.Uri) is a restore lease"  
        }  
        catch [Microsoft.WindowsAzure.Storage.StorageException]  
        {  
            if($_.Exception.RequestInformation.HttpStatusCode -eq 409)  
            {  
                Write-Host "The lease on $($blob.Uri) is not a restore lease"  
            }  
        }  
  
        Write-Host "Breaking lease on $($blob.Uri)"  
        $blob.BreakLease($(New-TimeSpan), $null, $null, $null) | Out-Null  
    }  
}  
  
```  
  
## <a name="see-also"></a>参照  
 [SQL Server Backup to URL に関するベスト プラクティスとトラブルシューティング](../../relational-databases/backup-restore/sql-server-backup-to-url-best-practices-and-troubleshooting.md)  
  
  
