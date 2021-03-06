---
title: プロジェクトオプションの設定 (DB2ToSQL) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: f325a606-97ac-48bc-b344-b55f5e086a48
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: d384433e5a2653291fac4d990bb3660b31c13855
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68060032"
---
# <a name="setting-project-options-db2tosql"></a>プロジェクトオプションの設定 (DB2ToSQL)
SSMA プロジェクトごとに、プロジェクトレベルのオプションを設定できます。 これらのオプションは、オブジェクトの変換、オブジェクトの読み込み、ユーザーインターフェイス、およびデータ移行の設定を指定します。 オブジェクトを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に変換または移行する前[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に、構成オプションがプロジェクトに適していることを確認してください。  
  
SSMA では、すべてのプロジェクトの既定のオプションを構成できます。 これらのオプションは、作成するすべての新しいプロジェクトに適用されます。 その後、各プロジェクトのオプションをカスタマイズできます。  
  
## <a name="configuration-options-and-modes"></a>構成オプションとモード  
SSMA には、次の5つのプロジェクト設定があります。  
  
-   プロジェクト情報  
  
-   全般 (変換、移行、オブジェクトの読み込み)  
  
-   Synchronization  
  
-   GUI  
  
-   型マッピング  
  
また、これらの設定を構成するための4つのモードもあります。  
  
-   Default  
  
-   Optimistic  
  
-   完全  
  
-   Custom  
  
ほとんどのユーザーには、既定のモードを使用することをお勧めします。 オプティミスティックモードでは、現在の DB2 構文が多く保持されるため、読みやすくなります。 ただし、現在の構文を維持するのは正確ではない可能性があります。 DB2 構文を同等[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の構文に変換する必要がある場合、フルモードでは最も完全な変換が実行されますが、結果のコードが読みにくくなる可能性があります。 カスタムモードでは、オプションを設定します。  
  
各モードでの設定と設定の適用方法の詳細については、次のトピックを参照してください。  
  
-   [プロジェクト設定 &#40;変換&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-conversion-db2tosql.md)  
  
-   [プロジェクト設定 &#40;移行&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-migration-db2tosql.md)  
  
-   [プロジェクト設定&#40;同期&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-synchronization-db2tosql.md)  
  
-   [プロジェクト設定 &#40;GUI&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-gui-db2tosql.md)  
  
-   [プロジェクト設定 &#40;型マッピング&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-type-mapping-db2tosql.md)  
  
## <a name="setting-project-options"></a>プロジェクト オプションの設定  
SSMA では、すべてのプロジェクトの既定の設定を構成できます。 これらの設定は、SSMA 構成ファイルに保存され、作成した新しいプロジェクトに適用されます。  
  
**既定のプロジェクトオプションを設定するには**  
  
1.  [**ツール**] メニューの [**既定のプロジェクト設定**] をクリックします。  
  
2.  [**既定のプロジェクト設定**] ダイアログボックスで、次のいずれかの手順を実行します。  
  
    -   [移行**先のバージョン**] ドロップダウンから [設定の表示または変更が必要な移行プロジェクトの種類] を選択し、左側のウィンドウの下部にある [**全般**] をクリックしてから、[変換] または [移行] を選択します。  
  
    -   定義済みのモードを選択するには、[**モード**] ボックスの一覧で [**既定**]、[**オプティミスティック**]、または [**完全**] を選択します。  
  
    -   カスタム設定を指定するには、新しい設定または値を選択または入力します。  
  
3.  
  **[OK]** をクリックして設定を保存します。  
  
また、現在のプロジェクトの設定をカスタマイズすることもできます。 これらの設定は、現在のプロジェクトファイルに保存されます。  
  
**現在のプロジェクトの設定をカスタマイズするには**  
  
1.  [**ツール**] メニューの [**プロジェクトの設定**] をクリックします。  
  
2.  [**プロジェクトの設定**] ダイアログボックスで、次のいずれかの手順を実行します。  
  
    -   定義済みのモードを選択するには、[**モード**] ボックスの一覧で [**既定**]、[**オプティミスティック**]、または [**完全**] を選択します。  
  
    -   カスタムモードを指定するには、[**モード**] ボックスで [**カスタム**] を選択し、適切なプロジェクト設定を選択します。  
  
3.  
  **[OK]** をクリックして設定を保存します。  
  
## <a name="next-steps"></a>次の手順  
移行の次のステップは、プロジェクトのニーズによって異なります。  
  
-   ソースとターゲットのデータ型のマッピングをカスタマイズするには、「 [DB2 と SQL Server のデータ型 &#40;DB2ToSQL&#41;にマッピング](../../ssma/db2/mapping-db2-and-sql-server-data-types-db2tosql.md)する」を参照してください。  
  
-   それ以外の場合は、DB2 データベースオブジェクト定義を[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]オブジェクト定義に変換できます。 詳細については、「 [DB2 スキーマ &#40;DB2ToSQL&#41;の変換](../../ssma/db2/converting-db2-schemas-db2tosql.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
[DB2 と SQL Server のデータ型のマッピング &#40;DB2ToSQL&#41;](../../ssma/db2/mapping-db2-and-sql-server-data-types-db2tosql.md)  
  
