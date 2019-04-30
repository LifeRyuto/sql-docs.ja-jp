---
title: ソース管理
titleSuffix: Azure Data Studio
description: Azure Data Studio でソース管理を構成する方法について説明します
ms.custom: seodec18
ms.date: 09/24/2018
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5fb3c8dea11e570bba4452e181626625e31acbe0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63312044"
---
#  <a name="using-source-control-in-includename-sosincludesname-sos-shortmd"></a>ソース管理での使用 [!INCLUDE[name-sos](../includes/name-sos-short.md)]

[!INCLUDE[name-sos](../includes/name-sos-short.md)] バージョン/ソース管理に Git をサポートしています。


## <a name="git-support-in-includename-sosincludesname-sos-shortmd"></a>Git のサポート [!INCLUDE[name-sos](../includes/name-sos-short.md)]

[!INCLUDE[name-sos](../includes/name-sos-short.md)] Git ソース管理マネージャー (SCM) が付属する必要があります[Git のインストール (バージョン 2.0.0 以降)](https://git-scm.com/download)これらの機能ができるようになります。 



## <a name="open-an-existing-git-repository"></a>既存の Git リポジトリを開く

1. **ファイル**メニューの下にある、**フォルダーを開く.** を選択します。
2. Gitによって追跡されるファイルを含むフォルダーを参照し、**フォルダーの選択**をクリックします。 ローカル リポジトリ内のサブフォルダーは、ここで選択することができます。


## <a name="initialize-a-new-git-repository"></a>新しい git リポジトリを初期化します。

1. **ソース管理**を選択し、gitアイコンを選択します。


   ![ソース管理 git アイコン](media/source-control/source-control.png)

1. Gitリポジトリとして初期化したいフォルダへのパスを入力し、**Enter**を押します。

   ![Git リポジトリを初期化します。](media/source-control/initialize-git-repository.png)

## <a name="working-with-git-repositories"></a>Git リポジトリの操作

[!INCLUDE[name-sos](../includes/name-sos-short.md)] VS Code からその Git 実装を継承しますが、現在 SCM プロバイダーの追加をサポートしていません。 リポジトリを開く、または初期化した後のGitの操作に関する詳細については、次を参照してください。 [VS コードでの Git サポート](https://code.visualstudio.com/docs/editor/versioncontrol#_git-support)


## <a name="additional-resources"></a>その他のリソース
- [Git に関するドキュメント](https://git-scm.com/documentation)
