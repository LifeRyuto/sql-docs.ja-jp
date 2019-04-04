---
title: Linux 上の SQL Server のセキュリティの制限 |Microsoft Docs
description: この記事では、Linux の制限の SQL Server について説明します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 01/30/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 64da74cc-14bf-4636-a55e-8cc1fce2aaff
ms.openlocfilehash: 9c58592568ca841df270190970fb76fefe43d96d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47711720"
---
# <a name="security-limitations-for-sql-server-on-linux"></a>Linux 上の SQL Server のセキュリティの制限

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

現在、Linux 上の SQL Server には、次の制限があります。

* 標準のパスワード ポリシーが提供されます。 MUST_CHANGE が、唯一のオプションを構成することがあります。  
* 拡張キー管理はサポートされていません。 
* Azure Key Vault に格納されているキーを使用することはサポートされていません。
* SQL Server では、接続を暗号化するため、独自の自己署名証明書を生成します。 SQL Server は、TLS 証明書に指定されたユーザーを使用するように構成できます。 

SQL Server で使用できるセキュリティ機能の詳細については、、 [SQL Server データベース エンジンと Azure SQL Database のセキュリティ センター](../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)を参照してください。

## <a name="next-steps"></a>次の手順

セキュリティの一般的なタスクは、[Linux 上の SQL Server のセキュリティ機能の概要](sql-server-linux-security-get-started.md)を参照してください。 TCP を変更するスクリプトのポート番号、SQL Server ディレクトリ、およびトレース フラグまたは照合順序の構成を参照してください[mssql-conf での Linux 上の SQL Server の構成](sql-server-linux-configure-mssql-conf.md)します。
