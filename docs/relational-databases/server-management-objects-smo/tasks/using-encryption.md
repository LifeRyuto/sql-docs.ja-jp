---
title: 暗号化を使用して |Microsoft Docs
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- database master key [SMO]
- cryptography [SMO]
- cryptography [SQL Server], SMO
- encryption keys [SMO]
- encryption [SQL Server], SMO
- encryption [SMO]
- certificates [SMO]
- service master key [SMO]
ms.assetid: 405e0ed7-50a9-430e-a343-471f54b4af76
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 94a9adc1a6c68391fbfb455ca89d2d46a97320a9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47836991"
---
# <a name="using-encryption"></a>暗号化の使用
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  Smo では、サービス マスター _ キーによって表される、<xref:Microsoft.SqlServer.Management.Smo.ServiceMasterKey>オブジェクト。 これによって参照されている、<xref:Microsoft.SqlServer.Management.Smo.Server.ServiceMasterKey%2A>のプロパティ、<xref:Microsoft.SqlServer.Management.Smo.Server>オブジェクト。 使用して再生成することができます、<xref:Microsoft.SqlServer.Management.Smo.ServiceMasterKey.Regenerate%2A>メソッド。  
  
 データベースのマスター _ キーがで表される、<xref:Microsoft.SqlServer.Management.Smo.MasterKey>オブジェクト。 <xref:Microsoft.SqlServer.Management.Smo.MasterKey.IsEncryptedByServer%2A>プロパティは、データベース マスター _ キーがサービス マスター_キーによって暗号化されたかどうかを示します。 master データベース内の暗号化されたコピーは、データベース マスター キーが変更されるたびに自動的に更新されます。  
  
 キーの暗号化を使用してサービスを削除することは、<xref:Microsoft.SqlServer.Management.Smo.MasterKey.DropServiceKeyEncryption%2A>メソッドとパスワードを使用して、データベース マスター _ キーを暗号化します。 この場合、セキュリティで保護された秘密キーにアクセスする前に、データベース マスター キーを明示的に開く必要があります。  
  
 インスタンスにデータベースが関連付けられているときに[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]、データベース マスター_キーのパスワードを入力または、実行する必要があります、<xref:Microsoft.SqlServer.Management.Smo.MasterKey.AddServiceKeyEncryption%2A>暗号化されていないデータベースのマスター _ キーのコピーをサービスでの暗号化に使用できるようにする方法マスター _ キー。 データベース マスター キーを明示的に開く必要性を回避するには、この手順をお勧めします。  
  
 <xref:Microsoft.SqlServer.Management.Smo.MasterKey.Regenerate%2A>メソッドは、データベース マスター _ キーを再生成します。 データベース マスター キーが再生成されると、このデータベース マスター キーで暗号化されたすべてのキーの暗号化が解除され、これらのキーが新しいデータベース マスター キーで暗号化されます。 <xref:Microsoft.SqlServer.Management.Smo.MasterKey.DropServiceKeyEncryption%2A>メソッドは、サービス マスター _ キーによって、データベース マスター _ キーの暗号化を削除します。 <xref:Microsoft.SqlServer.Management.Smo.MasterKey.AddServiceKeyEncryption%2A> は、サービス マスター キーを使用してマスター キーのコピーを暗号化し、現在のデータベースおよび master データベースの両方に格納します。  
  
 SMO では、証明書がによって表される、<xref:Microsoft.SqlServer.Management.Smo.Certificate>オブジェクト。 <xref:Microsoft.SqlServer.Management.Smo.Certificate>オブジェクトが、公開キー、サブジェクト名、有効期間、および発行者に関する情報を指定するプロパティ。 証明書にアクセスする権限は、 **Grant**メソッド、 **Revoke** メソッド、および **Deny** メソッドを使用して制御されます。  
  
## <a name="example"></a>例  
 次のコード例では、アプリケーションを作成するプログラミング環境、プログラミング テンプレート、およびプログラミング言語を選択する必要があります。 詳細については、[Visual C の作成&#35;Visual Studio .NET での SMO プロジェクト](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)を参照してください。  
  
## <a name="adding-a-certificate-in-visual-c"></a>Visual C# での証明書の追加  
 コード例では、暗号化パスワードを持つ簡単な証明書を作成します。 その他のオブジェクトとは異なり、<xref:Microsoft.SqlServer.Management.Smo.Certificate.Create%2A>メソッドが複数のオーバー ロードします。 この例で使用するオーバーロードは、暗号化パスワードを持つ新しい証明書を作成しています。  
  
```csharp  
{  
            //Connect to the local, default instance of SQL Server.   
            {  
                Server srv = new Server();  
  
                //Reference the AdventureWorks2012 database.   
                Database db = srv.Databases["AdventureWorks2012"];  
  
                //Define a Certificate object variable by supplying the parent database and name in the constructor.   
                Certificate c = new Certificate(db, "Test_Certificate");  
  
                //Set the start date, expiry date, and description.   
                System.DateTime dt;  
                DateTime.TryParse("January 01, 2010", out dt);  
                c.StartDate = dt;  
                DateTime.TryParse("January 01, 2015", out dt);  
                c.ExpirationDate = dt;  
                c.Subject = "This is a test certificate.";  
                //Create the certificate on the instance of SQL Server by supplying the certificate password argument.   
                c.Create("pGFD4bb925DGvbd2439587y");  
            }  
        }   
```  
  
## <a name="adding-a-certificate-in-powershell"></a>PowerShell での証明書の追加  
 コード例では、暗号化パスワードを持つ簡単な証明書を作成します。 その他のオブジェクトとは異なり、<xref:Microsoft.SqlServer.Management.Smo.Certificate.Create%2A>メソッドが複数のオーバー ロードします。 この例で使用するオーバーロードは、暗号化パスワードを持つ新しい証明書を作成しています。  
  
```powershell  
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = get-item AdventureWorks2012  
  
#Create a certificate  
  
$c = New-Object -TypeName Microsoft.SqlServer.Management.Smo.Certificate -argumentlist $db, "Test_Certificate"  
$c.StartDate = "January 01, 2010"  
$c.Subject = "This is a test certificate."  
$c.ExpirationDate = "January 01, 2015"  
  
#Create the certificate on the instance of SQL Server by supplying the certificate password argument.  
$c.Create("pGFD4bb925DGvbd2439587y")  
  
```  
  
## <a name="see-also"></a>関連項目  
 [暗号化キーを使用します。](../../../relational-databases/server-management-objects-smo/tasks/using-encryption.md)  
  
  
