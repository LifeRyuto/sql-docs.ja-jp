---
title: Power Pivot の正常性ルールの構成 |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ppvt-sharepoint
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: aae3b89c52f5d1d8524681a3a4fd2eda9ab73907
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68164232"
---
# <a name="configure-power-pivot-health-rules"></a>Power Pivot の正常性ルールの構成
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] for SharePoint には、サーバーの可用性と構成に関する問題を監視および解決するのに役立つ SharePoint 正常性ルールが含まれています。 [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] for SharePoint に適用される正常性ルールは、[ルール定義の確認] ページに表示されます。  
  
 正常性ルールは、最終的にサービスが中断される可能性があるサーバーの問題を早期に検出します。 [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] for SharePoint には、ユーザーに影響を与える前に問題を特定して解決するのに役立つさまざまなルールが用意されています。 これらのルールの多くは、配置固有の特性に合うようにカスタマイズできます。 たとえば、ディスク領域に関する警告に対処する時間がより多く必要な場合は、警告が早めに発生するように、使用可能なディスク領域の割合を 5% から 10% に引き上げることができます。  
  
 カスタマイズできるのは、リソース消費量やサーバーの可用性をレポートするルールです。 基になるシステムの容量はそれぞれのサーバーや配置のトポロジによって大きく異なるため、そうした項目をカスタマイズすると便利です。 一方、サーバー構成やセキュリティ上の問題を特定するルールはカスタマイズできません。 これらのルールは、すべてのインストール間で一様に適用されるものです。  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2013 &#124; SharePoint 2010|  
  
 **注:** SQL Server Analysis Services インスタンスの正常性ルールの設定を別々 に構成されます、[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)]サービス アプリケーション。 各サービスの正常性ルールを構成するには、このトピックで示されている手順に従ってください。 SharePoint 2013 配置の場合、 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] はサービス アプリケーションを使用するだけです。 そのため、 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] によってインストールされる正常性ルール セットは、SharePoint のバージョンに応じて異なります。 トピックの「バージョン」列を参照してください。[正常性ルールのリファレンス&#40;Power Pivot for SharePoint&#41;](../../analysis-services/power-pivot-sharepoint/health-rules-reference-power-pivot-for-sharepoint.md)、または、インストールされたルールを表示する次の Windows PowerShell コマンドを実行することができます。  
  
```  
Get-SPHealthAnalysisRule | select name, enabled, summary | where {$_.summary -like "*power*"}  | format-table -property * -autosize | out-default  
```  
  
 **このトピックの内容:**  
  
 [Power Pivot の正常性ルールの表示](#bkmk_view)  
  
 [サーバーの安定性を評価する正常性ルールの構成 (SQL Server Analysis Services)](#bkmk_HR_SSAS)  
  
 [アプリケーションの安定性を評価する正常性ルールの構成 (Power Pivot サービス アプリケーション)](#bkmk_evaluate_application_stability)  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Analysis Services インスタンスおよび [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] サービス アプリケーションの構成プロパティを変更するには、サービス アプリケーションの管理者である必要があります。  
  
##  <a name="bkmk_view"></a> Power Pivot の正常性ルールの表示  
  
1.  SharePoint サーバーの全体管理で、 **[監視]** をクリックし、 **[正常性アナライザー]** セクションの **[ルール定義の確認]** をクリックします。  
  
2.  [構成] セクションで、 **[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)]:** というプレフィックスが付いているルールを検索します。 組み込みの SharePoint ルールと区別するために、 [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)]に関連するすべての正常性ルールにはこのプレフィックスが付いています。  
  
 問題が検出されると、 **[問題とソリューションの確認]** ページにこれらのルールが表示されます。  
  
 直ちに調査する必要がある未確認の問題がある場合は、ルール チェックを手動で実行して、問題があるかどうかを調べることができます。  
  
 そうするには、ルールをクリックしてルールの定義を開き、リボンの **[今すぐ実行]** をクリックします。 **[閉じる]** をクリックして **[問題とソリューションの確認]** ページに戻り、レポートを確認します。 ルールによって問題が検出された場合は、警告またはエラーがこのページに報告されます。 場合によっては、エラーまたは警告が表示されるまでに数分かかる場合があります。  
  
##  <a name="bkmk_HR_SSAS"></a> サーバーの安定性を評価する正常性ルールの構成 (SQL Server Analysis Services)  
 Analysis Services インスタンスには、システム レベル (CPU、メモリ、およびキャッシュの目的で使用されるディスク領域) での問題を検出する正常性ルールが含まれています。 特定の正常性ルールをトリガーするしきい値を変更するには、次の手順に従います。  
  
1.  SharePoint サーバーの全体管理で、 **[システム設定]** セクションの **[サーバーのサービスの管理]** をクリックします。  
  
2.  ページの上部で、Analysis Services のインスタンスを持つ SharePoint ファーム内のサーバーを選択します (次の図では、サーバー名は AW-SRV033 です)。 サービスの一覧に **[SQL Server Analysis Services]** が表示されます。  
  
     ![スクリーン ショットのサービスの管理サーバーのページ](../../analysis-services/power-pivot-sharepoint/media/ssas-centraladmin-servicesonserver.gif "スクリーン ショットのサービスの管理サーバー ページ")  
  
3.  **[SQL Server Analysis Services]** をクリックします。  
  
4.  サービスのプロパティのページにある [正常性ルールの設定] で、次の設定を変更します。  
  
     CPU リソースの割り当ての不足 (既定値は 80%)  
     この正常性ルールは、Analysis Services サーバー プロセス (msmdsrv.exe) に使用されている CPU リソースが、データ収集間隔の設定を通じて指定された 4 時間以上にわたって 80% 以上である場合にトリガーされます。  
  
     この構成設定がというルールの定義に対応して、**問題とソリューションの確認**ページ:  **[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)]:Analysis Services には、要求された操作を実行するための十分な CPU リソースがありません。**  
  
     システムの CPU リソースの不足 (既定値は 90%)  
     この正常性ルールは、サーバーの CPU リソースが、データ収集間隔の設定を通じて指定された 4 時間以上にわたって 90% 以上である場合にトリガーされます。 全体的な CPU 使用率は、サーバーの状態の指標として CPU 使用率を監視する、サーバーの状態に基づく負荷分散アルゴリズムの一部として測定されます。  
  
     この構成設定がというルールの定義に対応して、**問題とソリューションの確認**ページ:  **[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)]:全体的な CPU 使用率が高すぎます。**  
  
     メモリ不足のしきい値 (既定値は 5%)  
     SharePoint アプリケーション サーバー上の SQL Server Analysis Services インスタンスには、常に未使用のメモリをいくらか確保しておく必要があります。 サーバーのほとんどの操作はメモリ バインドされているため、サーバーは上限まで実行されない場合に最適に実行されます。 5% の未使用メモリは、Analysis Services に割り当てられているメモリに対する割合として計算されます。 たとえば、メモリの合計が 200 GB で、Analysis Services にその 80% (つまり 160 GB) が割り当てられている場合、5% の未使用メモリは 160 GB の 5% (つまり 8 GB) です。  
  
     この構成設定がというルールの定義に対応して、**問題とソリューションの確認**ページ:  **[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)]:Analysis Services には、要求された操作を実行するための十分なメモリがありません。**  
  
     接続の最大数 (既定値は 100)  
     この正常性ルールは、Analysis Services インスタンスへの接続数が、データ収集間隔の設定を通じて指定された 4 時間以上にわたって 100 以上である場合にトリガーされます。 この既定値は恣意的なものです (サーバーのハードウェアの仕様やユーザーの利用状況に基づいていません)。そのため、使用している環境のサーバー容量およびユーザーの利用状況に応じて、値を増減できます。  
  
     この構成設定がというルールの定義に対応して、**問題とソリューションの確認**ページ:  **[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)]:大量の接続では、現在の負荷を処理するより多くのサーバーをデプロイする必要がありますを示します。**  
  
     ディスク領域の不足 (既定値は 5%)  
     ディスク領域は、データベースへの要求が行われるたびに、 [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] データをキャッシュするために使用されます。 このルールは、ディスク領域が不足している場合に、そのことを通知します。 既定では、バックアップ フォルダーが置かれているディスク ドライブ上のディスク領域が 5% 未満になると、この正常性ルールがトリガーされます。 ディスクの使用については、「 [ディスクの使用領域の構成 &#40;Power Pivot for SharePoint&#41;](../../analysis-services/power-pivot-sharepoint/configure-disk-space-usage-power-pivot-for-sharepoint.md)をクリックします。  
  
     この構成設定がというルールの定義に対応して、**問題とソリューションの確認**ページ:  **[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)]:ディスク領域がドライブに不足している[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)]データがキャッシュされます。**  
  
     データ収集間隔 (時間)  
     正常性ルールのトリガーに使用される数値の計算に使用される、データ収集期間を指定できます。 システムは常に監視されていますが、正常性ルールの警告のトリガーに使用されるしきい値は、事前に定義された間隔に基づいて生成されるデータを使用して計算されます。 既定の間隔は 4 時間です。 サーバーは、ユーザー接続数、ディスク領域の使用状況、CPU およびメモリの使用率などを評価するために、4 時間前から収集されているシステム データと利用状況データを取得します。  
  
##  <a name="bkmk_evaluate_application_stability"></a> アプリケーションの安定性を評価する正常性ルールの構成 (Power Pivot サービス アプリケーション)  
  
1.  サーバーの全体管理で、[アプリケーション構成の管理] の **[サービス アプリケーションの管理]** をクリックします。  
  
2.  [サービス アプリケーション] ページで、 **[既定の [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] サービス アプリケーション]** をクリックします。  
  
     ![サービス アプリケーションのスクリーン ショット ページ](../../analysis-services/power-pivot-sharepoint/media/ssas-centraladmin-app.gif "ページの サービス アプリケーションのスクリーン ショット")  
  
3.  [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] 管理ダッシュボードが表示されます。 **[アクション]** ボックスの一覧の **[サービス アプリケーションの設定の構成]** をクリックして、サービス アプリケーションの設定ページを開きます。  
  
     ![ダッシュ ボードのスクリーン ショットは、アクションの一覧に集中](../../analysis-services/power-pivot-sharepoint/media/ssas-centraladmin-actionslist.gif "ダッシュ ボードのスクリーン ショットは、アクションの一覧に集中")  
  
4.  [正常性ルールの設定] で、次の設定を変更します。  
  
     読み込み対接続の比率 (既定値は 20%)  
     この正常性ルールは、読み込みイベント数が接続イベント数に比べて多い場合にトリガーされます。それにより、サーバーによるデータベースのアンロードが早すぎる可能性があること、またはキャッシュの削減設定が厳しすぎることが通知されます。  
  
     この構成設定がというルールの定義に対応して、**問題とソリューションの確認**ページ:  **[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)]:接続に対する読み込みイベントの比率が高すぎます。**  
  
     データ収集間隔 (既定値は 4 時間)  
     正常性ルールのトリガーに使用される数値の計算に使用される、データ収集期間を指定できます。 システムは常に監視されていますが、正常性ルールの警告のトリガーに使用されるしきい値は、事前に定義された間隔に基づいて生成されるデータを使用して計算されます。 既定の間隔は 4 時間です。 サーバーは、収集に対する読み込みの比率を評価するために、4 時間前から収集されているシステム データと利用状況データを取得します。  
  
     [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] Management Dashboard.xlsx の更新プログラムの確認 (既定値は 5 日)  
     [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] Management Dashboard.xlsx ファイルは、 [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] 管理ダッシュボードのレポートによって使用されるデータ ソースです。 既定のサーバー構成では、SharePoint および [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] システム サービスによって収集された使用状況データを使用して、.xlsx ファイルは毎日更新されます。 ファイルが更新されない場合は、正常性ルールによって問題として報告されます。 既定では、ファイルのタイムスタンプが 5 日間変更されない場合、ルールがトリガーされます。  
  
     使用状況データ コレクションに関する詳細については、「[使用状況データ収集の構成 &#40;PowerPivot for SharePoint)](../../analysis-services/power-pivot-sharepoint/configure-usage-data-collection-for-power-pivot-for-sharepoint.md)」を参照してください。  
  
     この構成設定がというルールの定義に対応して、**問題とソリューションの確認**ページ:  **[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)]:使用状況データが必要な頻度で更新されません。**  
  
## <a name="see-also"></a>関連項目  
 [ディスクの使用領域の構成 &#40;Power Pivot for SharePoint&#41;](../../analysis-services/power-pivot-sharepoint/configure-disk-space-usage-power-pivot-for-sharepoint.md)   
 [Power Pivot 管理ダッシュボードと使用状況データ](../../analysis-services/power-pivot-sharepoint/power-pivot-management-dashboard-and-usage-data.md)  
  
  
