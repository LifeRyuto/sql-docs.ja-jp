---
title: データ マイニングのストアド プロシージャ (Analysis Services - データ マイニング) |Microsoft Docs
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2984927575e6dcd3c8d6c530a94061b1dc0b6c17
ms.sourcegitcommit: 603d5ef9b45c2f111d36d11864dc032917e4a321
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/08/2019
ms.locfileid: "65449943"
---
# <a name="data-mining-stored-procedures-analysis-services---data-mining"></a>データ マイニングのストアド プロシージャ (Analysis Services - データ マイニング)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]以降の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、任意の管理言語で記述できるストアド プロシージャがサポートされています。 サポートされているマネージド言語には、 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET、C#、および Managed C++ があります。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]では、 **CALL** ステートメントを使用してストアド プロシージャを直接呼び出すか、データ マイニング拡張機能 (DMX) クエリの一部としてストアド プロシージャを呼び出すことができます。  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ストアド プロシージャの呼び出し方法の詳細については、「 [ストアド プロシージャの呼び出し](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/calling-stored-procedures.md)」を参照してください。  
  
 プログラミングの詳細については、次を参照してください。[データ マイニングのプログラミング](../../analysis-services/data-mining/data-mining-programming.md)します。  
  
 データ マイニング オブジェクトのプログラミング方法の詳細については、MSDN ライブラリの「[SQL Server データ マイニングのプログラミング](http://go.microsoft.com/fwlink/?LinkId=93735)」を参照してください。  
  
> [!NOTE]  
>  マイニング モデルにクエリを実行する場合、特に新しいデータ マイニング ソリューションをテストする場合は、データ マイニング エンジンで内部的に使用されるシステム ストアド プロシージャを呼び出すと便利です。 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を使用して [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバーでトレースを作成した後、データ マイニング モデルを作成、参照、およびクエリすることで、これらのシステム ストアド プロシージャの名前を表示できます。 ただし、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] では、異なるバージョン間でのシステム ストアド プロシージャの互換性を保証していないため、実稼働システムではシステム ストアド プロシージャを呼び出さないでください。 代わりに、互換性を維持するために、DMX または XML/A を使用して独自のクエリを作成してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [SystemGetCrossValidationResults &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/systemgetcrossvalidationresults-analysis-services-data-mining.md)  
  
-   [SystemGetClusterCrossValidationResults &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/systemgetclustercrossvalidationresults-analysis-services-data-mining.md)  
  
-   [SystemGetAccuracyResults &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/systemgetaccuracyresults-analysis-services-data-mining.md)  
  
-   [SystemGetClusterAccuracyResults &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/systemgetclusteraccuracyresults-analysis-services-data-mining.md)  
  
## <a name="see-also"></a>参照  
 [相互検証 &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/cross-validation-analysis-services-data-mining.md)   
 [[相互検証] タブ &#40;[マイニング精度チャート] ビュー&#41;](http://msdn.microsoft.com/library/bd215a68-1ad7-4046-9c44-ec8e2be13a64)   
 [ストアド プロシージャの呼び出し](../../relational-databases/native-client-odbc-stored-procedures/calling-a-stored-procedure.md)  
  
  
