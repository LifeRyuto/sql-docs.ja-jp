---
title: メソッドのバッチ処理 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- methods [Reporting Services], batches
- BatchHeader SOAP header
- Web service [Reporting Services], methods
- Report Server Web service, batching
- batches [Reporting Services]
- XML Web service [Reporting Services], methods
- locking [Reporting Services]
- multiple Web service methods
ms.assetid: 86435534-c9fe-4b49-b88c-7fb6d21976b0
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 0def97e31cb34ac9b764b027b622c5ba605d9a7a
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56017133"
---
# <a name="batching-methods"></a>メソッドのバッチ処理
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の SOAP ヘッダーを使用することによって、1 つの操作に複数の Web サービス メソッドを含めることができます。 メソッドは、1 つのデータベース トランザクションのスコープ内で、呼び出された順序で実行されます。  
  
 ロールバックは、複数メソッド バッチ操作の利点の 1 つです。 バッチの実行中にメソッド呼び出しでエラーが発生した場合は、レポート サーバーがバッチの実行を停止し、それ以前の操作をロールバックします。 あるメソッドが、バッチ内の他のメソッド呼び出しの正常終了に依存している場合、この方法は便利です。  
  
 Web サービスは、複数メソッド バッチ操作に対するロック セマンティクスを提供しません。 メッセージがサーバーに送信され、Execute コマンドが呼び出されるまでは、レポート サーバー データベースの行の更新がロックされません。  
  
 データが最後に読み取られてからデータベースが変更されていないことを保証するコンカレンシー制御もありません。 2 台のクライアントが同じアイテムを変更する場合は、アイテムの名前が変更されていないなど、パラメーターが有効なままであれば最後の更新が成功します。  
  
 次の例では、<xref:ReportService2005.ReportingService2005.CreateFolder%2A> メソッドを 3 回呼び出し、これらの呼び出しを 1 つのバッチとして実行します。 <xref:ReportService2005.ReportingService2005.CreateFolder%2A> への呼び出しのいずれかが失敗すると、バッチ全体が取り消されます。  
  
```vb  
Imports System  
Imports System.Web.Services.Protocols  
Imports myNamespace.MyReferenceName  
  
Class Sample  
    Sub Main(args() As String)  
        Dim rs As New ReportingService2005()  
        rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
      ' Set the base Web service URL of the source server  
      rs.Url = "http://<Server Name>/reportserver/ReportService2005.asmx"  
  
        Dim bh As New BatchHeader()  
  
        bh.BatchId = service.CreateBatch()  
        rs.BatchHeaderValue = bh  
        rs.CreateFolder("New Folder1", "/", Nothing)  
        rs.CreateFolder("New Folder2", "/", Nothing)  
        rs.CreateFolder("New Folder3", "/", Nothing)  
  
        Console.WriteLine("Creating folders...")  
        rs.BatchHeaderValue = bh  
        rs.ExecuteBatch()  
        Console.WriteLine("Folders created successfully.")  
  
        rs.BatchHeaderValue = Nothing  
    End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.Web.Services.Protocols;   
using myNamespace.MyReferenceName;  
  
class Sample  
{  
    static void Main(string[] args)  
    {  
        ReportingService2005 rs = new ReportingService2005();  
        rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
      // Set the base Web service URL of the source server  
      rs.Url = "http://<Server Name>/reportserver/ReportService2005.asmx"  
  
        BatchHeader bh = new BatchHeader();  
  
        bh1.BatchID = service.CreateBatch();  
        rs.BatchHeaderValue = bh;  
        rs.CreateFolder("New Folder1", "/", null);  
        rs.CreateFolder("New Folder2", "/", null);  
        rs.CreateFolder("New Folder3", "/", null);  
  
        Console.WriteLine("Creating folders...");  
        rs.BatchHeaderValue = bh1;  
        rs.ExecuteBatch();  
        Console.WriteLine("Folders created successfully.");  
  
        rs.BatchHeaderValue = null;  
    }  
}  
```  
  
## <a name="see-also"></a>参照  
 <xref:ReportService2005.ReportingService2005.CancelBatch%2A>   
 <xref:ReportService2005.ReportingService2005.CreateBatch%2A>   
 [テクニカル リファレンス (SSRS)](../technical-reference-ssrs.md)   
 [Reporting Services SOAP ヘッダーの使用](using-reporting-services-soap-headers.md)  
  
  
