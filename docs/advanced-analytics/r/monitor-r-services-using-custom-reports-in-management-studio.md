---
title: Management Studio - SQL Server Machine Learning サービスでカスタム レポートを使用して R Services の監視します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 55fcb4e145481f98b0cba065ddab75e7cfa0a538
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58510289"
---
# <a name="monitor-machine-learning-services-using-custom-reports-in-management-studio"></a>Management Studio でカスタム レポートを使用して Machine Learning Services を監視する
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

機械学習に使用されるインスタンスを管理しやすいようにには、製品チームが、多くの SQL Server Management Studio に追加できるカスタム レポートのサンプルを用意しています。 これらのレポートなどの詳細を表示できます。

- アクティブな R または Python のセッション
- インスタンスの構成設定
- Machine learning ジョブの実行の統計
- R Services の拡張イベント
- 現在のインスタンスにインストールされている R または Python パッケージ

この記事では、インストールしてマシン leaerning を具体的には提供されているカスタム レポートを使用する方法について説明します。 

Management Studio でレポートを一般的な概要については、次を参照してください。 [Management Studio におけるカスタム レポート](../../ssms/object/custom-reports-in-management-studio.md)します。

## <a name="how-to-install-the-reports"></a>レポートのインストール方法

レポートは SQL Server Reporting Services を使用するように設計されていますが、SQL Server Management Studio から直接使用することができます。インスタンスに Reporting Services がインストールされていない場合でも同じです。 

これらのレポートを使用する場合は、次のようにします。

* SQL Server 製品サンプルの GitHub リポジトリから RDL ファイルをダウンロードします。
* SQL Server Management Studio で使用されるカスタム レポート フォルダーにファイルを追加します。
* SQL Server Management Studio でレポートを開きます。


### <a name="step-1-download-the-reports"></a>手順 1. サンプルのダウンロード

1. 含む GitHub リポジトリに開いて[SQL Server 製品サンプル](https://github.com/Microsoft/sql-server-samples)、およびサンプル レポートをダウンロードします。 

    + [SSMS カスタム レポート](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/machine-learning-services/ssms-custom-reports)

    > [!NOTE]
    > レポートは、SQL Server 2017 Machiine Learning サービス、または SQL Server 2016 R Services のいずれかで使用できます。

2. サンプルをダウンロードする場合、GitHub にログインし、サンプルのローカル分岐を作成することもできます。 

### <a name="step-2-copy-the-reports-to-management-studio"></a>手順 2. Management Studio へのレポートのコピー

3. SQL Server Management Studio で使用されるカスタム レポート フォルダーを見つけます。 既定では、カスタム レポートは次のフォルダーに格納されます。
    
   `C:\Users\user_name\Documents\SQL Server Management Studio\Custom Reports`

   ただし、別のフォルダーを指定したり、サブフォルダーを作成したりすることもできます。

4. *.RDL ファイルをカスタム レポート フォルダーにコピーします。


### <a name="step-3-run-the-reports"></a>手順 3. レポートの実行

5. Management Studio で、レポートを実行するインスタンスの **[データベース]** ノードを右クリックします。
6. **[レポート]**、 **[カスタム レポート]** の順にクリックします。
7. **[ファイルを開く]** ダイアログ ボックスで、カスタム レポート フォルダーを見つけます。
8. ダウンロードした RDL ファイルを選択し、 **[開く]** をクリックします。

> [!IMPORTANT]
> 高 DPI または 1080 p を超える解像度のディスプレイ デバイスを持つ一部のコンピューターや、一部のリモート デスクトップ セッションでは、これらのレポートは使用できません。 SSMS のレポート ビューアー コントロールには、レポートのクラッシュの原因となるバグがあります。

## <a name="report-list"></a>レポートの一覧

現在、GitHub の製品サンプル リポジトリには、次のレポートが含まれています。

+ **R Services - Active Sessions**

  このレポートを使用して、SQL Server インスタンスと学習のジョブの実行中のマシンに現在接続されているユーザーが表示されます。 
  
+ **R Services - Configuration**

  このレポートを使用すると、外部スクリプトのランタイムと関連サービスの構成を表示します。 レポートでは、再起動が必要かどうかが示され、必要なネットワーク プロトコルが確認されます。 
  
  暗黙の認証は、計算コンテキストとして SQL Server で実行される機械学習タスクに必要です。 その暗黙の認証が構成されていることを確認するには、レポートは、グループ SQLRUserGroup のデータベース ログインが存在するかどうかを確認します。

 + **R Services - Configure Instance** 

   このレポートは、machine learning を構成する際に対象としています。 検出前のレポートの構成エラーを修正するには、このレポートを実行することもできます。
 
+ **R Services - Execution Statistics**

  このレポートを使用すると、machine learning ジョブの実行の統計情報を表示します。 たとえば、実行された R スクリプトの合計数、並列実行の数、および最も頻繁に使用される RevoScaleR 関数を確認できます。 クリックして**SQL スクリプトの表示**をこのレポートの背後にある完全な T-SQL コードを取得します。

  現在、レポートで監視されるのは、RevoScaleR パッケージ関数の統計のみです。

+ **R Services - Extended Events**

  このレポートを使用すると、外部スクリプトのランタイムに関連するタスクを監視するために使用できる拡張イベントの一覧を表示します。 クリックして**SQL スクリプトの表示**をこのレポートの背後にある完全な T-SQL コードを取得します。

+ **R Services - Packages**

  このレポートを使用すると、SQL Server インスタンスにインストールされている R または Python パッケージの一覧を表示します。

+ **R Services - Resource Usage**

  このレポートを使用すると、外部スクリプトの実行によって CPU、メモリ、および I/O リソースの消費量を確認します。 外部のリソース プールのメモリ設定を表示することもできます。

## <a name="see-also"></a>関連項目

[サービスの監視](managing-and-monitoring-r-solutions.md)

[R Services の拡張イベント](extended-events-for-sql-server-r-services.md)
