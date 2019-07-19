---
title: 既定のデータ モデルと配置プロパティを Analysis Services の構成 |Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 938ef21a83a6e08336c9e9c53a95e3886ab24dab
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68163087"
---
# <a name="configure-default-data-modeling-and-deployment-properties"></a>既定のデータ モデルと配置プロパティの構成 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  この記事は、既定の互換性レベルを構成する方法を説明します、展開とした新しい各テーブル モデル プロジェクトに対して事前定義するワークスペース データベース プロパティ設定の作成で[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]します。 新しいプロジェクトの作成後も、これらのプロパティを特定の要件に応じて変更できます。  
  
#### <a name="to-configure-the-default-compatibility-level-property-setting-for-new-model-projects"></a>新しいモデル プロジェクトの既定の互換性レベル プロパティの設定を構成するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、 **[ツール]** メニューをクリックし、 **[オプション]** をクリックします。  
  
2.  **[オプション]** ダイアログ ボックスで、 **[Analysis Services Tabular Designers]** を展開し、 **[互換性レベル]** をクリックします。  
  
3.  次のプロパティ設定を構成します。  
  
    |プロパティ|既定の設定|説明|  
    |--------------|---------------------|-----------------|  
    |**新しいプロジェクトの既定の互換性レベル**|SQL Server 2016 (1200)|この設定では、新しいテーブル モデル プロジェクトを作成するときに使用する既定の互換性レベルを指定します。 SP1 が適用されていない Analysis Services インスタンスに配置する場合は SQL Server 2012 (1100) を、配置インスタンスに SP1 が適用されている場合は SQL Server 2012 SP1 以上を選択できます。 詳細については、「 [Analysis Services でのテーブル モデルの互換性レベル](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)」を参照してください。|  
    |**互換性レベルのオプション**|すべてをオン|新しいテーブル モデル プロジェクトと、別の Analysis Services インスタンスに配置するときの互換性レベル オプションを指定します。|  
  
#### <a name="to-configure-the-default-deployment-server-property-setting-for-new-model-projects"></a>新しいモデル プロジェクトの既定の配置サーバー プロパティの設定を構成するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、 **[ツール]** メニューをクリックし、 **[オプション]** をクリックします。  
  
2.  **[オプション]** ダイアログ ボックスで、 **[Analysis Services Tabular Designers]** を展開し、 **[配置]** をクリックします。  
  
3.  次のプロパティ設定を構成します。  
  
    |プロパティ|既定の設定|説明|  
    |--------------|---------------------|-----------------|  
    |**[既定の配置サーバー]**|localhost|この設定は、モデルの配置時に使用される既定のサーバーを指定します。 下矢印をクリックして、使用できるローカル ネットワークの Analysis Services サーバーを参照するか、リモート サーバーの名前を入力することもできます。|  
  
    > [!NOTE]  
    >  既定の配置サーバー プロパティの設定を変更しても、変更前に作成された既存のプロジェクトに影響しません。  
  
###  <a name="bkmk_conf_default"></a> 新しいモデル プロジェクトの既定のワークスペース データベース プロパティの設定を構成するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、 **[ツール]** メニューをクリックし、 **[オプション]** をクリックします。  
  
2.  **[オプション]** ダイアログ ボックスで、 **[Analysis Services Tabular Designers]** を展開し、 **[ワークスペース データベース]** をクリックします。  
  
3.  次のプロパティ設定を構成します。  
  
    |プロパティ|既定の設定|説明|  
    |--------------|---------------------|-----------------|  
    |**[既定のワークスペース サーバー]**|**localhost**|このプロパティは、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]でモデルが作成されるときにワークスペース データベースをホストするのに使用される既定のサーバーを指定します。 ローカル コンピューターで実行されている Analysis Services の使用可能なすべてのインスタンスが、このボックスの一覧に表示されます。<br /><br /> <br /><br /> 注:常にローカル Analysis Services サーバーをワークスペース サーバーとして指定することをお勧めします。 リモート サーバー上のワークスペース データベースでは、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] からのデータのインポートはサポートされておらず、データはローカルにバックアップされず、クエリ中にユーザー インターフェイスで遅延が発生する場合があります。|  
    |**[モデルが閉じられた後のワークスペース データベースの保有期間]**|**ディスクにワークスペース データベースを保持するが、メモリからアンロードする**|モデルが閉じられた後でワークスペース データベースを保持する方法を指定します。 ワークスペース データベースには、モデル メタデータ、モデルにインポートされたデータ、および権限借用の資格情報 (暗号化) が含まれます。 場合によっては、ワークスペース データベースは非常に大きくなり、大量のメモリを消費することがあります。 既定では、ワークスペース データベースはメモリから削除されます。 この設定を変更するときには、使用可能なメモリ リソースと、モデルに対する作業を行う頻度を考慮することが重要です。 このプロパティの設定には、以下のオプションがあります。<br /><br /> **メモリにワークスペースを保持** - モデルを閉じた後もワークスペースをメモリ内に保持するように指定します。 このオプションはより多くのメモリを消費しますが、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]でモデルを開くときのリソース消費が少なくて済み、ワークスペースの読み込みも高速になります。<br /><br /> **ディスクにワークスペース データベースを保持するが、メモリからアンロードする** - モデルを閉じた後、ディスクにワークスペース データベースを保持しますが、メモリ内に保持されないように指定します。 このオプションはメモリの消費量は比較的少なくて済みますが、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]でモデルを開くときのリソース消費が増え、ワークスペース データベースをメモリ内に保持した場合と比べて、モデルの読み込みにも時間がかかるようになります。 メモリ内のリソースが制限されている場合、またはリモートのワークスペース データベースで作業する場合に、このオプションを使用します。<br /><br /> **ワークスペースの削除** - モデルを閉じた後、メモリからワークスペース データベースを削除し、ディスク上にもワークスペース データベースを保持しないように指定します。 このオプションはメモリとストレージ領域の消費量が比較的少なくて済みますが、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]でモデルを開くときのリソース消費が増え、ワークスペース データベースをメモリ内やディスク上に保持した場合と比べて、モデルの読み込みにも時間がかかるようになります。 このオプションは、モデルに対する作業の頻度が低い場合に使用してください。|  
    |**[データ バックアップ]**|**[データのバックアップをディスク上に保持する]**|モデル データのバックアップをバックアップ ファイルに保存するかどうかを指定します。 このプロパティの設定には、以下のオプションがあります。<br /><br /> **データのバックアップをディスク上に保持する** - モデル データのバックアップをディスク上に保持するように指定します。 モデルを保存すると、バックアップ (ABF) ファイルにもデータが保存されます。 このオプションを選択すると、モデルの保存と読み込みが低速化する可能性があります。<br /><br /> **データのバックアップをディスク上に保持しない** - モデル データのバックアップをディスク上に保持しないように指定します。 保存時間とモデルの読み込み時間が最小限で済みます。|  
  
> [!NOTE]  
>  既定のモデル プロパティを変更しても、変更前に作成された既存のモデルのプロパティに影響しません。  
  
## <a name="see-also"></a>関連項目  
 [プロジェクトのプロパティ](../../analysis-services/tabular-models/project-properties-ssas-tabular.md)   
 [モデルのプロパティ](../../analysis-services/tabular-models/model-properties-ssas-tabular.md)   
 [互換性レベル](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)  
  
  
