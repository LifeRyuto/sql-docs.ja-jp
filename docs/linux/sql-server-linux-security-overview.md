---
title: Linux 上の SQL Server のセキュリティの制限
description: この記事では、Linux の制限の SQL Server について説明します。
author: VanMSFT
ms.author: vanto
ms.date: 01/30/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 64da74cc-14bf-4636-a55e-8cc1fce2aaff
ms.openlocfilehash: 9f54197c8613293b36c1eb1ec362a8ed4db835e4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68065126"
---
# <a name="security-limitations-for-sql-server-on-linux"></a>Linux 上の SQL Server のセキュリティの制限

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

現在、Linux 上の SQL Server には、次の制限があります。

* 標準のパスワード ポリシーが提供されます。 MUST_CHANGE が、唯一のオプションを構成することがあります。  
* 拡張キー管理はサポートされていません。 
* Azure Key Vault に格納されているキーを使用することはサポートされていません。
* SQL Server では、接続を暗号化するため、独自の自己署名証明書を生成します。 SQL Server は、TLS 証明書に指定されたユーザーを使用するように構成できます。 

SQL Server で使用できるセキュリティ機能の詳細については、次を参照してください。、 [SQL Server データベース エンジンと Azure SQL Database のセキュリティ センター](../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)します。

## <a name="next-steps"></a>次の手順

セキュリティの一般的なタスクは、次を参照してください。 [Linux 上の SQL Server のセキュリティ機能の概要](sql-server-linux-security-get-started.md)します。 TCP を変更するスクリプトのポート番号、SQL Server ディレクトリ、およびトレース フラグまたは照合順序の構成を参照してください[mssql-conf での Linux 上の SQL Server の構成](sql-server-linux-configure-mssql-conf.md)します。
