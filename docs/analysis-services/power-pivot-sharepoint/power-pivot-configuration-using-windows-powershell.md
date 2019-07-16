---
title: Power Pivot の構成の Windows PowerShell を使用して |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ppvt-sharepoint
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e290e0e15797a8b84a6d52c945a5fd78458515fc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68208204"
---
# <a name="power-pivot-configuration-using-windows-powershell"></a>Windows PowerShell を使用した Power Pivot の構成
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] には、 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]のインストールを構成するために使用できる Windows PowerShell コマンドレットが含まれています。 PowerShell によりインストールを完全に構成するには、SharePoint コマンドレットと [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint コマンドレットの両方を使用する必要があります。 構成の大部分は [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ツールのいずれかを使用して実行することができます。 ツールの詳細については、「 [Power Pivot Configuration Tools](../../analysis-services/power-pivot-sharepoint/power-pivot-configuration-tools.md)」を参照してください。  
  
> [!IMPORTANT]  
>  SharePoint 2010 ファームの場合、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint または [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] データベース サーバーを使用する SharePoint ファームを構成する前に、SharePoint 2010 SP1 をインストールする必要があります。 サービス パックをインストールしていない場合は、サーバーの構成を始める前にインストールしてください。  
  
## <a name="benefits-of-configuring-power-pivot-for-sharepoint-using-powershell"></a>PowerShell を使用して Power Pivot for SharePoint を構成する利点  
 Windows  PowerShell スクリプト (.ps1) ファイルを作成して構成タスクを自動化できます。 この方法は、任意のサーバーで実行できるスクリプト化されたインストール手順および構成手順が必要な場合に推奨されます。 このようなスクリプトは、ハードウェア障害が発生したときにサーバーを再構築するディザスター リカバリー計画の一環として必要になる場合があります。  
  
## <a name="view-a-list-of-the-power-pivot-cmdlets-on-a-server"></a>サーバーで Power Pivot コマンドレットの一覧を表示する  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] コマンドレットの内容との例については、「 [Power Pivot for SharePoint 用 PowerShell リファレンス](../../analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint.md)」を参照してください。  
  
 PowerShell を使用して [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] コマンドレットの一覧を表示するには:  
  
1.  **[管理者として実行]** オプションを使用して SharePoint 管理シェルを開きます。  
  
2.  次のコマンドを入力します。  
  
    ```  
    Get-help *powerpivot*  
    ```  
  
     コマンドレット名に [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] を含むコマンドレットの一覧が表示されます。 たとえば、 `Get-PowerPivotServiceApplication`があります。 使用できるコマンドレットの数は、使用している Analysis Services のバージョンによって異なります。  
  
    -   SharePoint モードで構成された SQL Server 2012 SP1 Analysis Services サーバーおよび SharePoint 2013 では、10 個のコマンドレットを使用できます。 2012 SP1 バージョンで使用される新しいアーキテクチャでは、分析サーバーを SharePoint ファームの外部で実行できるため、必要な管理 Windows PowerShell コマンドレットが少なくて済みます。  
  
    -   SharePoint モードで構成された SQL Server 2012 Analysis Services サーバーおよび SharePoint 2010 では、17 個のコマンドレットを使用できます。  
  
     一覧にコマンドが返されないかのようなエラー メッセージを参照してください"`get-help could not find *powerpivot* in a help file in this session.`"を有効にする方法については、このトピックでは、次のセクションを参照してください、[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]サーバーでコマンドレット。  
  
     すべてのコマンドレットに、オンライン ヘルプが用意されています。 **New-PowerPivotServiceApplication** コマンドレットのオンライン ヘルプを表示する方法を次の例に示します。  
  
    ```  
    Get-help new-powerpivotserviceapplication -full  
    ```  
  
     また、例のみを表示するには、次の構文を使用します。  
  
    ```  
    Get-help new-powerpivotserviceapplication -example  
    ```  
  
## <a name="enable-power-pivot-cmdlets-on-a-server"></a>サーバーで Power Pivot コマンドレットを有効にする  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] コマンドレットは、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint のインストールとファーム ソリューションの配置が完了した後で利用できるようになります。 ソリューションは、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 構成ツールを実行すると配置されます。 コマンドレットの使用を有効にするには、次の手順を実行します。  
  
1.  **[管理者として実行]** オプションを使用して SharePoint 管理シェルを開きます。  
  
2.  最初のコマンドレットを実行します。  
  
    ```  
    Add-SPSolution -LiteralPath "C:\Program Files\Microsoft SQL Server\110\Tools\PowerPivotTools\ConfigurationTool\Resources\PowerPivotFarm.wsp"  
    ```  
  
     コマンドレットにより、ソリューション名、ソリューション ID、および Deployed=False が返されます。 次の手順では、ソリューションを配置します。  
  
3.  2 番目のコマンドレットを実行してソリューションを配置します。  
  
    ```  
    Install-SPSolution -Identity PowerPivotFarm.wsp -GACDeployment -Force  
    ```  
  
4.  ウィンドウを閉じます。 **[管理者として実行]** を使用してもう一度ウィンドウを開きます。  
  
## <a name="related-content"></a>関連コンテンツ  
 [サーバーの全体管理での Power Pivot サーバーの管理と構成](../../analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration.md)  
  
 [Power Pivot Configuration Tools](../../analysis-services/power-pivot-sharepoint/power-pivot-configuration-tools.md)  
  
 [Power Pivot for SharePoint 用 PowerShell リファレンス](../../analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint.md)  
  
  
