---
title: azdata app template リファレンス
description: azdata app template コマンドのリファレンス記事です。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.metadata: seo-lt-2019
ms.date: 12/13/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: da1b98649eeb48d5ae2d6ca05e61da53f519e944
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "75251050"
---
# <a name="azdata-app-template"></a>azdata app template

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]  

以下の記事では、`app template` ツールの `azdata` コマンドに関するリファレンスを提供します。 `azdata` の他のコマンドに関する詳細については、[azdata のリファレンス](reference-azdata.md)に関するページをご覧ください

## <a name="commands"></a>コマンド
|     |     |
| --- | --- |
[`azdata app template list`](#azdata-app-template-list) | サポートされているテンプレートを取得します。
[`azdata app template pull`](#azdata-app-template-pull) | サポートされているテンプレートをダウンロードします。
## <a name="azdata-app-template-list"></a>azdata app template list
指定した [URL] github リポジトリにある、サポートされているテンプレートを取得します。
```bash
azdata app template list [--url -u]
```
### <a name="examples"></a>例
既定のテンプレート リポジトリの場所にあるすべてのテンプレートを取得します。
```bash
azdata app template list
```
別のリポジトリの場所にあるすべてのテンプレートを取得します。
```bash
azdata app template list --url https://github.com/diffrent/templates.git
```
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--url -u`
別のテンプレート リポジトリの場所を指定します。 既定値: https://github.com/Microsoft/SQLBDC-AppDeploy.git
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
すべてのデバッグ ログを表示するようにログの詳細レベルを上げます。
#### `--help -h`
このヘルプ メッセージを表示して終了します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv。  既定値: json。
#### `--query -q`
JMESPath クエリ文字列。 詳細と例については、[http://jmespath.org/](http://jmespath.org/) を参照してください。
#### `--verbose`
ログの詳細レベルを上げます。 詳細なデバッグ ログを表示するには --debug を使います。
## <a name="azdata-app-template-pull"></a>azdata app template pull
指定した [URL] github リポジトリにある、サポートされているテンプレートをダウンロードします。
```bash
azdata app template pull [--name -n] 
                         [--url -u]  
                         [--destination -d]
```
### <a name="examples"></a>例
既定のテンプレート リポジトリの場所にあるすべてのテンプレートをダウンロードします。
```bash
azdata app template pull
```
別のリポジトリの場所にあるすべてのテンプレートをダウンロードします。
```bash
azdata app template list --url https://github.com/diffrent/templates.git
```
名前を指定して個々のテンプレートをダウンロードします。
```bash
azdata app template pull --name ssis            
```
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--name -n`
テンプレート名。 サポートされているテンプレート名の完全な一覧を表示するには、`azdata app template list` を実行します
#### `--url -u`
別のテンプレート リポジトリの場所を指定します。 既定値: https://github.com/Microsoft/SQLBDC-AppDeploy.git
#### `--destination -d`
アプリケーション スケルトン テンプレートを配置する場所。
`./templates`
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
すべてのデバッグ ログを表示するようにログの詳細レベルを上げます。
#### `--help -h`
このヘルプ メッセージを表示して終了します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv。  既定値: json。
#### `--query -q`
JMESPath クエリ文字列。 詳細と例については、[http://jmespath.org/](http://jmespath.org/) を参照してください。
#### `--verbose`
ログの詳細レベルを上げます。 詳細なデバッグ ログを表示するには --debug を使います。

## <a name="next-steps"></a>次のステップ

`azdata` の他のコマンドに関する詳細については、[azdata のリファレンス](reference-azdata.md)に関するページをご覧ください。 `azdata` ツールのインストール方法の詳細については、[SQL Server 2019 ビッグ データ クラスターを管理する azdata のインストール](deploy-install-azdata.md)に関するページを参照してください。
