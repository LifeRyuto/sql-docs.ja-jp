---
title: ナレッジ ベースの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 51eff161-6ecd-4ee4-8187-1dd8ef4814bd
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 01d0b016f6b7e1ea3c83cd42f52facb56f825b77
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "65481165"
---
# <a name="building-a-knowledge-base"></a>ナレッジ ベースの作成
  
  [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) のナレッジ ベースはデータに関するナレッジのリポジトリです。ナレッジ ベースを使用して、データを理解し、その整合性を維持できます。 ナレッジ ベースはドメインで構成され、各ドメインはデータ フィールド内のデータを表します。 ナレッジ ベースは、DQS でデータベース上のデータのクレンジングと重複除去を実行するのに使用されます。 データ クレンジング用にナレッジ ベースを準備するには、データ サンプルのコンピューター支援型分析を実行し、ドメインの値を対話形式で管理します。 DQS を使用して、ナレッジのインポート、ルールおよび関係の作成、データ値の直接変更、既定のデータベースの利用を行うことができます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 ナレッジ ベースで次の操作を実行できます。  
  
|||  
|-|-|  
|ナレッジ ベースを既存のナレッジ ベースまたは .dqs データ ファイルから新規に作成します。|[ナレッジ ベースの作成](../../2014/data-quality-services/create-a-knowledge-base.md)|  
|既存のナレッジ ベースを開き、ナレッジ検出やドメイン管理の実行、または照合ポリシーの追加を行います。|[ナレッジ ベースを開く](../../2014/data-quality-services/open-a-knowledge-base.md)|  
|ナレッジ ベースでの管理操作 (ナレッジ ベースを開く、ナレッジ ベースのロックの解除、ナレッジ ベースでの作業内容の破棄、ナレッジ ベース名の変更、ナレッジ ベースの削除、ナレッジ ベースのプロパティの表示など) を実行します。|[ナレッジ ベースの管理](../../2014/data-quality-services/manage-a-knowledge-base.md)|  
|ナレッジ検出を通じたナレッジ ベースへのナレッジの追加、ドメイン値の管理、照合ポリシーの追加、ナレッジ、ドメイン、値のインポート、または既定のナレッジ ベースの DQS データの使用を行います。|[ナレッジ ベースへのナレッジの追加](../../2014/data-quality-services/adding-knowledge-to-a-knowledge-base.md)|  
|データ品質基準のデータ サンプルを分析します。|[ナレッジ検出の実行](../../2014/data-quality-services/perform-knowledge-discovery.md)|  
  
## <a name="related-tasks"></a>Related Tasks  
  
|タスクの説明|トピック|  
|----------------------|-----------|  
|ナレッジをナレッジ ベースにインポートするか、ナレッジ ベースからナレッジをエクスポートします。|[ナレッジのインポートとエクスポート](../../2014/data-quality-services/importing-and-exporting-knowledge.md)|  
|単一ドメインを作成し、ナレッジをドメインに追加します。|[ドメインの管理](../../2014/data-quality-services/managing-a-domain.md)|  
|複合ドメインを作成し、ナレッジをドメインに追加します。|[複合ドメインの管理](../../2014/data-quality-services/managing-a-composite-domain.md)|  
  
  
