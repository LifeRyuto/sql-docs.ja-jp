---
title: SSL 暗号化を使用する |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8e566243-2f93-4b21-8065-3c8336649309
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 98c9cd99d8fd8a54c96a9301ac3a050b54614c17
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68003968"
---
# <a name="using-ssl-encryption"></a>SSL 暗号化の使用

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

SSL (Secure Sockets Layer) 暗号化により、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスとクライアント アプリケーションの間で、暗号化されたデータをネットワーク経由で送信できるようになります。  
  
SSL は、ネットワークやその他のインターネット通信において、重要な情報や機密情報の傍受を防ぐ安全な通信チャネルを確立するためのプロトコルです。 SSL を使用すると、クライアントとサーバーは互いの ID を認証することができます。 参加者の認証が完了すると、SSL は安全なメッセージ送信のための暗号化された接続を参加者間で提供します。  
  
[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] は、接続プロパティで指定されたユーザーと、サーバーおよびクライアントの設定に基づいて、特定の接続上で暗号化を有効および無効にするためのインフラストラクチャを提供します。 ユーザーは、証明書ストアの場所とパスワード、証明書の検証に使用するホスト名、および通信チャネルを暗号化するタイミングを指定できます。  
  
SSL 暗号化を有効にすると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスとアプリケーションの間でネットワークを経由して転送されるデータのセキュリティが強化されます。 ただし、暗号化を有効にすると、パフォーマンスが低下します。  
  
このセクションの各トピックでは、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] が SSL 暗号化をサポートするしくみについて説明します。これには、新しい接続プロパティと、クライアント側でトラスト ストアを構成する方法についての説明が含まれます。  
  
> [!NOTE]  
> SSL 証明書を検証するには、 **hostNameInCertificate**接続プロパティをお勧めします。  

## <a name="in-this-section"></a>このセクションの内容  

| トピック                                                                                                        | [説明]                                                                                                                                           |
| ------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| [SSL のサポートについて](../../connect/jdbc/understanding-ssl-support.md)                                 | [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] が SSL 暗号化をサポートするしくみについて説明します。                                              |
| [SSL 暗号化を使用した接続](../../connect/jdbc/connecting-with-ssl-encryption.md)                       | 新しい SSL 固有の接続プロパティを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに接続する方法について説明します。 |
| [SSL 暗号化のためのクライアントの構成](../../connect/jdbc/configuring-the-client-for-ssl-encryption.md) | クライアント側で既定のトラスト ストアを構成する方法と、クライアント コンピューターのトラスト ストアにプライベート証明書をインポートする方法について説明します。   |
  
## <a name="see-also"></a>参照

[JDBC ドライバー アプリケーションのセキュリティ保護](../../connect/jdbc/securing-jdbc-driver-applications.md)  
