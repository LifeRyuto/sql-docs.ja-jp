---
title: ストアド プロシージャの定義 |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 54b14cd5ee54edab4508c06c55e5815bfeab934f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68209383"
---
# <a name="defining-stored-procedures"></a>ストアド プロシージャの定義
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  外部ルーチンを呼び出すストアド プロシージャを使用する[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]します。 ストアド プロシージャによって呼び出される外部ルーチンは、C、C++、C#、Visual Basic、Visual Basic .NET などの共通言語ランタイム (CLR) 言語でも書き込むことができます。 ストアド プロシージャを作成すると、他のストアド プロシージャ、計算されるメジャー、クライアント アプリケーションなどの多くのコンテキストから呼び出すことができます。 ストアド プロシージャを使用すると、共通コードを開発し、1 つの場所に格納できるようにすることによって、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースの開発および実装が簡単になります。 ストアド プロシージャを使用して、アプリケーションに、MDX のネイティブ機能によって提供されていないビジネス機能を追加できます。  
  
 このセクションでは、ストアド プロシージャの理解、デザイン、および実装に必要な情報を提供します。  
  
|トピック|説明|  
|-----------|-----------------|  
|[ストアド プロシージャのデザイン](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/designing-stored-procedures.md)|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で使用するアセンブリをデザインする方法を説明します。|  
|[ストアド プロシージャの作成](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/creating-stored-procedures.md)|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のアセンブリを構成する方法を説明します。|  
|[ストアド プロシージャを呼び出す](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/calling-stored-procedures.md)|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] でアセンブリを使用する方法の詳細について説明します。|  
|[ストアド プロシージャのクエリ コンテキストへのアクセス](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/accessing-query-context-in-stored-procedures.md)|スコープ、およびアセンブリを持つコンテキスト情報にアクセスする方法を説明します。|  
|[ストアド プロシージャのセキュリティの設定](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/setting-security-for-stored-procedures.md)|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のアセンブリのセキュリティを構成する方法を説明します。|  
|[デバッグ系のストアド プロシージャ](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/debugging-stored-procedures.md)|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のアセンブリをデバッグする方法を説明します。|  
  
## <a name="see-also"></a>関連項目  
 [多次元モデルのアセンブリの管理](../../analysis-services/multidimensional-models/multidimensional-model-assemblies-management.md)  
  
  
