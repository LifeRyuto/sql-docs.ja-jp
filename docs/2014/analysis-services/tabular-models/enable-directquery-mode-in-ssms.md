---
title: テーブルモデルデータベースに対するメモリ内または DirectQuery アクセスの構成 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a5d439a9-5be1-4145-90e8-90777d80e98b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 55a1a296e6a7b2a2155dea590be9321b22e73451
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66067192"
---
# <a name="configure-in-memory-or-directquery-access-for-a-tabular-model-database"></a>テーブル モデルのデータベースの In-Memory または DirectQuery アクセスの構成
  このトピックでは、既に配置されたテーブル モデルの接続プロパティを変更し、モデルを直接クエリ モードで使用できるようにする方法について説明します。  
  
 これらのプロパティ、および最も一般的なシナリオの構成の詳細については、「 [SSAS のデプロイシナリオ &#40;SSAS 表形式&#41;](../directquery-deployment-scenarios-ssas-tabular.md)」を参照してください。  
  
## <a name="requirements"></a>必要条件  
 テーブル モデルで直接クエリ モードを使用できるようにする操作は、複数の手順から成るプロセスです。 前提条件は、以下のとおりです。  
  
1.  直接クエリ モードで検証エラーが発生するような機能がモデルにないことを確認します。  
  
2.  直接クエリをサポートするように、モデルのストレージ モードを変更します。  
  
3.  ハイブリッド モードと純粋な直接クエリ モードの両方のクエリをサポートするモードでモデルを配置します。  
  
4.  配置されたデータベースの接続文字列を、直接クエリ モードをサポートするように編集します。  
  
 このトピックは、モデルが既に作成および検証済みで、[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] などのクライアントからの直接クエリ アクセスの有効化だけが必要であることを前提としています。  
  
## <a name="procedure"></a>手順  
  
#### <a name="change-the-connection-string-properties-of-the-model"></a>モデルの接続文字列プロパティの変更  
  
1.  SQLServer Management Studio で、モデルを配置するインスタンスを開きます。  
  
2.  オブジェクトエクスプローラーで、モデルデータベースの名前を右クリックし、[**プロパティ**] を選択します。  
  
3.  **Directquerymode**プロパティを見つけます。 リレーショナル データ ソースを使用できるようにするには、このプロパティを次のいずれかの値に設定する必要があります。  
  
    -   **DirectQuery**  
  
    -   **InMemoryWithDirectQuery**  
  
    -   **DirectQueryWithInMemory**  
  
  
