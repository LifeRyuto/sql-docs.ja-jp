---
title: 配置スクリプトを作成するために使用する入力ファイルについて |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6b75ec5d7433931a81a0fa6e2c648f85335fbedc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68208975"
---
# <a name="deployment-script-files---input-used-to-create-deployment-script"></a>配置スクリプト ファイル - デプロイ スクリプトを作成する入力の使用
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  ビルドする場合は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]プロジェクト、[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]プロジェクトのファイルが生成されます。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] これらのファイルの出力フォルダーに格納、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]プロジェクト。 既定では、出力は \Bin フォルダーに対して行われます。 次の表は、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] で作成される XML ファイルを示しています。  
  
|File|説明|  
|---------------|-----------------|  
|\<*プロジェクト名*> .asdatabase|多次元形式または 1100 または 1103 表形式モデル プロジェクトの XMLA ファイルまたは表形式 1200 と上位のモデル プロジェクト用の JSON ファイルです。 プロジェクト内のすべての [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトの宣言定義が含まれています。|  
|\<*プロジェクト名*> >.deploymenttargets|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトが作成される [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスおよびデータベースの名前が含まれています。|  
|\<*プロジェクト名*> >.configsettings|データ ソース接続情報やオブジェクト格納場所など、環境に固有の設定が含まれています。 このファイルの設定で設定を上書き、 \<*プロジェクト名*> .asdatabase ファイル。|  
|\<*プロジェクト名*> >.deploymentoptions|配置がトランザクションであるかどうかや、配置したオブジェクトを配置後に処理するかどうかなどの配置オプションが含まれています。|  
  
> [!NOTE]  
>  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] では、プロジェクト ファイルにパスワードは保存されません。  
  
## <a name="modifying-the-input-files"></a>入力ファイルの変更  
 入力ファイル内の値または入力ファイルから取得した値を変更、配置先、構成設定を変更することおよび配置オプションを全体を編集することがなく\<*プロジェクト名前*> .asdatabase ファイル (または既存のスクリプトを生成する場合は、全体のスクリプト ファイル[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]データベース)。 個々のファイルを変更できると、さまざまな目的に合わせてさまざまな配置スクリプトを簡単に作成できます。  
  
 次のトピックでは、さまざまな入力ファイル内の値を変更する方法について説明します。  
  
-   [インストール先の指定](../../analysis-services/multidimensional-models/deployment-script-files-specifying-the-installation-target.md)  
  
-   [パーティションおよびロールの配置オプションの指定](../../analysis-services/multidimensional-models/deployment-script-files-partition-and-role-deployment-options.md)  
  
-   [ソリューションの配置に関する構成設定の指定](../../analysis-services/multidimensional-models/deployment-script-files-solution-deployment-config-settings.md)  
  
-   [処理オプションの指定](../../analysis-services/multidimensional-models/deployment-script-files-specifying-processing-options.md)  
  
## <a name="see-also"></a>関連項目  
 [Analysis Services 配置ウィザードの実行](../../analysis-services/multidimensional-models/running-the-analysis-services-deployment-wizard.md)   
 [Analysis Services 配置スクリプトについて](../../analysis-services/multidimensional-models/understanding-the-analysis-services-deployment-script.md)  
  
  
