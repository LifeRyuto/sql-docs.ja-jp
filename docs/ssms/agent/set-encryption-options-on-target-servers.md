---
title: 対象サーバーでの暗号化オプションの設定 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, encryption
- target servers [SQL Server], encryption
- multiserver environments [SQL Server], setting encryption options on target servers
ms.assetid: 1a9fd539-e166-4ea8-9f21-ac400ca74dee
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: dd6e43157f8b822f62b915a5f09079ee8368cf25
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2018
ms.locfileid: "51699840"
---
# <a name="set-encryption-options-on-target-servers"></a>対象サーバーでの暗号化オプションの設定
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) では現在、すべてではありませんがほとんどの SQL Server エージェントの機能がサポートされています。 詳細については、「[Azure SQL Database Managed Instance と SQL Server の T-SQL の相違点](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)」を参照してください。

マスター サーバーと一部またはすべてのターゲット サーバーの間で SSL (Secure Sockets Layer) 暗号通信の証明書を使用できない場合、これらの間のチャネルを暗号化するには、必要なセキュリティ レベルを使用するようにターゲット サーバーを構成します。  
  
マスター サーバーとターゲット サーバーの間の特定の通信チャネルに求められる適切なセキュリティ レベルを構成するには、ターゲット サーバーの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのレジストリ サブキー **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\**\<*instance_name*>**\SQLServerAgent\MsxEncryptChannelOptions(REG_DWORD)** を、次のいずれかの値に設定します。 \<*instance_name*> の値は **MSSQL.**_n_ です。 たとえば、 **MSSQL.1** や **MSSQL.3**となります。  
  
|ReplTest1|[説明]|  
|---------|---------------|  
|**0**|このターゲット サーバーとマスター サーバーの間の暗号化を無効にします。 ターゲット サーバーとマスター サーバー間のチャネルのセキュリティを別の手段で保護する場合にこのオプションを選択します。|  
|**1**|このターゲット サーバーとマスター サーバーの間のみ暗号化を有効にしますが、証明書の検証は必要ありません。|  
|**2**|このターゲット サーバーとマスター サーバーの間で、完全な SSL 暗号化と証明書の検証を有効にします。 この設定が既定値です。 別の値を選択する具体的な理由がある場合を除いて、この値を変更しないことをお勧めします。|  
  
**1** または **2** を指定する場合、マスター サーバーと対象サーバーの両方で SSL を有効にしている必要があります。 **2** を指定する場合、マスター サーバーには適切に署名された証明書も必要になります。  
  
> [!CAUTION]  
> [!INCLUDE[ssNoteRegistry](../../includes/ssnoteregistry-md.md)]  
  
## <a name="see-also"></a>参照  
[データベース エンジンへの暗号化接続を有効にする方法 (SQL Server 構成マネージャー)](https://msdn.microsoft.com/e1e55519-97ec-4404-81ef-881da3b42006)  
  
