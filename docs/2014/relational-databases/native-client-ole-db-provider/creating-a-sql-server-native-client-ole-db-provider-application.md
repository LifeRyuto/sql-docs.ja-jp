---
title: SQL Server Native Client OLE DB プロバイダーアプリケーションの作成 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, application creation
- applications [SQL Server Native Client]
- OLE DB, creating applications
ms.assetid: f3ae6815-f32d-4913-a1a2-2ba2f20cfd88
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0e422ac6535900a287ae610a85241dc67172c4f7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63209760"
---
# <a name="creating-a-sql-server-native-client-ole-db-provider-application"></a>SQL Server Native Client OLE DB プロバイダー アプリケーションの作成
  Native Client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB プロバイダーアプリケーションを作成するには、次の手順を実行します。  
  
1.  データ ソースへの接続の確立。  
  
2.  コマンドの実行。  
  
3.  結果を処理しています。  
  
> [!NOTE]  
>  可能な場合は、Windows 認証を使用します。 Windows 認証が使用できない場合は、実行時に資格情報を入力するようユーザーに求めます。 資格情報をファイルに保存するのは避けてください。 資格情報を保存する必要がある場合は、[Win32 CryptoAPI](https://go.microsoft.com/fwlink/?LinkId=9504) を使用して暗号化してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [データ ソースへの接続の確立](establishing-a-connection-to-a-data-source.md)  
  
-   [コマンドの実行](executing-a-command.md)  
  
-   [結果の処理](processing-results.md)  
  
-   [OLE DB プロパティについて](about-ole-db-properties.md)  
  
-   [SQL Server Native Client の OLE DB での OUTPUT 句の使用](using-the-output-clause-with-ole-db-in-sql-server-native-client.md)  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
