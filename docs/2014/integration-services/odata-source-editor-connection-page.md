---
title: '[OData ソースエディター] ([接続] ページ)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- Sql12.dts.designer.odatasource.connection.f1
ms.assetid: 20bcd347-4547-4fad-b182-9571030101df
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 0e36c0a3449566db9a2acee360243c77ee548f92
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66057316"
---
# <a name="odata-source-editor-connection-page"></a>[OData ソース エディター] ([接続] ページ)
  **[ODBC ソース エディター]** ダイアログ ボックスの **[接続]** ページを使用すると、OData ソースに対応する ODBC 接続マネージャーを選択できます。 また、このページで、コレクションまたはリソースのパスと、どのデータを OData ソースから取得する必要があるかを示すクエリ オプションを指定することができます。 OData ソースの詳細については、「 [OData ソース](data-flow/odata-source.md)」を参照してください。  
  
## <a name="static-options"></a>静的オプション  
 **OData 接続マネージャー**  
 既存の接続マネージャーを一覧から選択するか、 **[新規作成]** をクリックして新しい接続を作成します。  
  
 **[新規作成]**  
 新しい接続マネージャーを作成するには、 **[OData 接続マネージャー エディター]** ダイアログ ボックスを使用します。  
  
 **コレクションまたはリソースのパスを使用します。**  
 ソースからデータを選択する方法を指定します。  
  
|オプション|[説明]|  
|------------|-----------------|  
|コレクション|コレクション名を使用して、Odata ソースからデータを取得します。|  
|リソースのパス|リソースのパスを使用して、Odata ソースからデータを取得します。|  
  
 **クエリ オプション**  
 クエリのオプションを指定します。  例: $top=5  
  
 **フィード URL**  
 このダイアログ ボックスで選択したオプションに基づいて、読み取り専用のフィード URL を表示します。  
  
 **プレビュー**  
 **[プレビュー]** ダイアログ ボックスを使用して、結果をプレビューします。 **プレビュー** では、最大で 20 行を表示できます。  
  
## <a name="dynamic-options"></a>動的オプション  
  
### <a name="use-collection-or-resource-path--collection"></a>コレクション、またはリソースのパス = Collection を使用します。  
 **コレクション**  
 ドロップダウン リストからコレクションを選択します。  
  
### <a name="use-collection-or-resource-path--resource-path"></a>コレクションまたはリソースのパス = Resource Path を使用します。  
 **Resource path**  
 リソースのパスを入力します。 次に例を示します。Employees  
  
## <a name="see-also"></a>参照  
 [OData ソースエディター &#40;列のページ&#41;](../../2014/integration-services/odata-source-editor-columns-page.md)   
 [OData ソースエディター &#40;エラー出力ページ&#41;](../../2014/integration-services/odata-source-editor-error-output-page.md)   
 [OData 接続マネージャー](connection-manager/odata-connection-manager.md)  
  
  
