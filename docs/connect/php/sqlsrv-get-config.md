---
title: sqlsrv_get_config |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- sqlsrv_get_config
apitype: NA
helpviewer_keywords:
- API Reference, sqlsrv_get_config
- sqlsrv_get_config
ms.assetid: ce2befc2-af98-45bb-8d41-60f1674dccfc
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 615acc0ce9e7601b46690f1e2f87b92166a8c2c8
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66802240"
---
# <a name="sqlsrvgetconfig"></a>sqlsrv_get_config
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

指定された構成設定の現在の値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
sqlsrv_get_config( string $setting )  
```  
  
#### <a name="parameters"></a>パラメーター  
*$setting*: 値を返す構成設定。 構成可能な設定の一覧については、「 [sqlsrv_configure](../../connect/php/sqlsrv-configure.md)」を参照してください。  
  
## <a name="return-value"></a>戻り値  
*$setting* パラメーターで指定された設定の値。 無効な設定を指定した場合は、 **false** が返されて、エラーがエラー コレクションに追加されます。  
  
## <a name="remarks"></a>Remarks  
**false** が **sqlsrv_get_config** によって返された場合は、[sqlsrv_errors](../../connect/php/sqlsrv-errors.md) を呼び出して、エラーが発生したかどうか、または **false** が *$setting* パラメーターで指定した設定の値かどうかを、判定する必要があります。  
  
## <a name="see-also"></a>参照  
[SQLSRV ドライバー API リファレンス](../../connect/php/sqlsrv-driver-api-reference.md)  

[sqlsrv_configure](../../connect/php/sqlsrv-configure.md)  

[sqlsrv_errors](../../connect/php/sqlsrv-errors.md)  
  
