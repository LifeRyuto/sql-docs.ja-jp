---
title: ProtocolDLL プロパティ (ServerNetworkProtocol)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- ProtocolDLL Property (ServerNetworkProtocol Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- ProtocolDLL property
ms.assetid: ac386558-392e-46f3-97f8-382f267b7fca
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3cbf2d7968f1e0af97cf28604768b01fb27511cf
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "73659443"
---
# <a name="protocoldll-property-servernetworkprotocol-class"></a>ProtocolDLL プロパティ (ServerNetworkProtocol クラス)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  サーバー ネットワーク プロトコルに必要な .dll ファイルの名前を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.ProtocolDLL [= value]  
```  
  
## <a name="parts"></a>要素  
 *素材*  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)]の[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]インスタンスによって使用されるネットワークプロトコルを表す[servernetworkprotocol クラス](../../../relational-databases/wmi-provider-configuration-classes/servernetworkprotocol-class/servernetworkprotocol-class.md)オブジェクト。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 サーバー ネットワーク プロトコルに必要なプロトコル .dll ファイルを指定する文字列値。  
  
## <a name="remarks"></a>解説  
  
## <a name="see-also"></a>参照  
 [サーバーのネットワーク プロトコルと Net-Library の構成](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
