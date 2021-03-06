---
title: Configuration の Database 要素 (DTA)
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Database element
ms.assetid: e91ba243-6cc9-457a-8f5a-134f3c71ae69
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.openlocfilehash: cb444b56c70d70fda8578459b83939ebcbcf3645
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "75306697"
---
# <a name="database-element-for-configuration-dta"></a>Configuration の Database 要素 (DTA)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

データベース エンジン チューニング アドバイザーで仮想的な構成 ( **Configuration** 要素で指定する構成) を評価するときの対象のデータベースを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
<Server>  
...code removed here...  
    <Database>...</Database>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特徴|[説明]|  
|--------------------|-----------------|  
|**データ型と長さ**|[なし] :|  
|**既定値**|[なし] :|  
|**個数**|**Server** 要素につき 1 回以上の出現が必要です。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|--------------|  
|**親要素**|[Configuration の Server 要素 &#40;DTA&#41;](../../tools/dta/server-element-for-configuration-dta.md)|  
|**子要素**|[Database の Name 要素 &#40;DTA&#41;](../../tools/dta/name-element-for-database-dta.md)<br /><br /> [Database の Schema 要素 &#40;DTA&#41;](../../tools/dta/schema-element-for-database-dta.md)<br /><br /> [Recommendation 要素 &#40;DTA&#41;](../../tools/dta/recommendation-element-dta.md)|  
  
## <a name="remarks"></a>解説  
 この要素は、データベース エンジン チューニング アドバイザー XML スキーマの **DatabaseTypecomplexType** の名前です。 この **Database** 要素を、ルートの親要素が **Server** 要素である (XML 入力ファイルの最上位に発生する) 他の要素と混同しないでください。 詳細については、「[Server の Database 要素 &#40;DTA&#41;](../../tools/dta/database-element-for-server-dta.md)」を参照してください。  
  
## <a name="example"></a>例  
 この **Database** 要素の使用例については、「[ユーザー指定の構成を指定した XML 入力ファイルのサンプル &#40;DTA&#41;](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
