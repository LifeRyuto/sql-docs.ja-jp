---
title: パッケージをプログラムで保存 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- programmatically saving a package
- saving a package programmatically
ms.assetid: 4204f817-d5df-475a-9338-d7f01305d566
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 993c9bcaeb92f7ec4eabc11beaf444e97622821f
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/20/2019
ms.locfileid: "58271169"
---
# <a name="saving-a-package-programmatically"></a>パッケージをプログラムで保存
  プログラムにより新しいパッケージを構築したり、既存のパッケージを変更した後には、通常は変更を保存します。  
  
 このトピックでパッケージを保存するために使うすべてのメソッドには、**Microsoft.SqlServer.ManagedDTS** アセンブリへの参照が必要です。 新しいプロジェクトに参照を追加した後、**using** または **Imports** ステートメントを使って <xref:Microsoft.SqlServer.Dts.Runtime> 名前空間をインポートします。  
  
## <a name="saving-a-package-programmatically"></a>パッケージをプログラムで保存  
 プログラムによりパッケージを保存するには、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <xref:Microsoft.SqlServer.Dts.Runtime.Application> クラスの次のいずれかのメソッドを呼び出します。  
  
|ストレージの場所|呼び出すメソッド|  
|----------------------|--------------------|  
|ファイル|<xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToXml%2A>|  
|[SSIS パッケージ ストア]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToSqlServer%2A><br /><br /> 内の複数の<br /><br /> <xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToSqlServerAs%2A>|  
  
> [!IMPORTANT]  
>  SSIS パッケージ ストアを操作するための <xref:Microsoft.SqlServer.Dts.Runtime.Application> クラスのメソッドは、"." またはローカル サーバーのサーバー名のみをサポートします。 "(local)" や "localhost" は使用できません。  
  
## <a name="see-also"></a>参照  
 [パッケージを保存する](../../integration-services/save-packages.md)  
  
  
