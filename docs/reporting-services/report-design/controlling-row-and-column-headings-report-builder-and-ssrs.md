---
title: 行見出しと列見出しの制御 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.date: 05/24/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 4be6e836-158e-4bc9-8870-7f394d7c7e11
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 5ed08231f0bfd3cf7b505e3064883393470047e5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "65581575"
---
# <a name="controlling-row-and-column-headings-report-builder-and-ssrs"></a>行見出しと列見出しの制御 (レポート ビルダーおよび SSRS)
  テーブル、マトリックス、一覧のいずれのデータ領域も、上下または左右に、複数のページにわたって続く場合があります。 行見出しや列見出しを各ページに繰り返し表示するかどうかは、適宜指定することが可能です。 また、Web ポータルやレポート プレビューなどの対話的なレンダラーでは、行見出しまたは列見出しを固定することにより、レポートを上下左右にスクロールしても、見出しが隠れないようにすることができます。 通常、テーブルまたはマトリックスでは、先頭行には、列データのラベルとしての列見出しが、先頭列には、行データのラベルとしての行見出しが表示されます。 入れ子構造のグループの場合は、グループ ラベルを含んでいる、先頭から数行分の行見出しまたは列見出しをひとまとめにして、繰り返し表示することもできます。 既定では、一覧データ領域に見出しは含まれません。  
  
 見出しを繰り返し表示するかどうか (または固定するかどうか) の制御方法は、次の条件に依存します。  
  
-   各ページの上部に繰り返し表示される列見出しの場合  
  
    -   テーブルまたはマトリックスに、水平方向に展開された列グループ領域が存在するかどうか。  
  
    -   列グループに関連付けられているすべての行をひとまとめにして制御するかどうか。  
  
-   各ページの側面に繰り返し表示される行見出しの場合  
  
    -   テーブルまたはマトリックスに、垂直方向に展開された行グループ領域が存在するかどうか。 行見出しは、行グループ ヘッダーを持った行グループでのみサポートされます。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="understanding-rows-and-columns-in-a-tablix-data-region"></a>Tablix データ領域の行と列について  
 テーブルまたはマトリックスは、基になる Tablix データ領域のテンプレートです。 Tablix データ領域は、最大 4 つの領域で構成されます。行グループ領域 (レポートの上下方向に展開される行を制御する領域)、列グループ領域 (レポートの左右方向に展開される列を制御する領域)、本体 (データが表示される領域)、およびコーナーです。 実際にヘッダーの繰り返しまたは固定を制御するときに、どこでプロパティを設定すればよいかを適切に判断するためには、Tablix データ領域には次の 2 つの表現があることを理解しておくと役に立ちます。  
  
-   **レポート定義** Tablix データ領域定義内のそれぞれの行または列は、特定の行グループまたは列グループの Tablix メンバーにあたります。 Tablix メンバーには静的なものと動的なものがあります。 静的 Tablix メンバーは、ラベルまたは小計を格納し、グループごとに 1 回繰り返されます。 動的 Tablix メンバーは、グループの値を格納し、グループの固有の値 (グループ インスタンス) につき 1 回繰り返されます。  
  
-   **デザイン画面** デザイン画面では、Tablix データ領域の 4 つの領域が点線で区画されます。 Tablix データ領域の各セルは、行と列で構成されます。 行と列はグループに関連付けられます (詳細グループを含む)。 特定の Tablix データ領域を選択すると、行と列のハンドルおよびハイライト バーによって、グループのメンバーシップが示されます。 行グループ領域または列グループ領域のセルは、Tablix メンバーのグループ ヘッダーを表します。 単一の行または列を、複数のグループに関連付けることもできます。  
  
     詳細については、「[Tablix データ領域 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/tablix-data-region-report-builder-and-ssrs.md)」と「[Tablix データ領域のセル、行、および列 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md)」を参照してください。  
  
 行グループ領域または列グループ領域を持つ Tablix データ領域では、それに関連付けられている行および列を、Tablix データ領域のプロパティを設定することによって制御します。 それ以外の場合は、選択した Tablix メンバーのプロパティ ペインで、必要なプロパティを設定することにより、行および列を制御することになります。 段階的な手順については、「[複数のページへの行および列ヘッダーの表示 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/display-row-and-column-headers-on-multiple-pages-report-builder-and-ssrs.md)」と「[レポートのスクロール時にヘッダーを表示したままにする (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/keep-headers-visible-when-scrolling-through-a-report-report-builder-and-ssrs.md)」を参照してください。  
  
##  <a name="Top"></a> 使用例  
 Tablix データ領域に表示される内容として最も一般的な例としては、マトリックス、グループを持たないテーブル、行グループと行グループ ヘッダーを持つテーブル、行グループはあるが行グループ ヘッダーは持たないテーブルなどがあります。 ヘッダーの繰り返しまたは固定を制御するには、制御の対象となる行または列が、その行グループ領域または列グループ領域でグループ ヘッダーに関連付けられているかどうかを見極める必要があります。  
  
 次のセクションでは、Tablix データ領域の一般的なレイアウトの例を紹介します。  
  
-   [マトリックス](#Matrix)  
  
-   [グループを持たないテーブル](#TableNoGroups)  
  
-   [行グループおよび行グループ領域を持つテーブル](#TableRowGroupsGroupHeader)  
  
-   [行グループはあるが行グループ領域を持たないテーブル](#TableRowGroupsNoGroupHeader)  
  
###  <a name="Matrix"></a> マトリックス  
 既定では、単純なマトリックスには、行グループと列グループが 1 つずつ含まれています。 次の図は、Category (カテゴリ) に基づく行グループと、Geography (地理) に基づく列グループを持つマトリックスを示しています。  
  
 ![Matrix、Category 行および Geography 列グループ](../../reporting-services/report-design/media/rs-basicmatrixdesign.gif "Matrix、Category 行および Geography 列グループ")  
  
 点線は 4 つの Tablix 領域を示しています。 行グループ領域の先頭列には、カテゴリ ラベルを制御する行グループ ヘッダーがあります。 同様に、列グループ領域の先頭行には、地理ラベルを制御する列グループ ヘッダーがあります。 プレビューでマトリックスがページの横方向に展開されると、先頭行には、列見出しが次の図のように表示されます。  
  
 ![グループが展開されているマトリックス形式表示のプレビュー](../../reporting-services/report-design/media/rs-basicmatrixpreview.gif "グループが展開されているマトリックス形式表示のプレビュー")  
  
 先頭行の列見出しを繰り返し表示するか固定するには、Tablix データ領域の列ヘッダーのプロパティを設定します。 入れ子になった列グループの列ヘッダーは自動的に追加されます。  
  
 先頭列の行見出しを繰り返し表示するか固定するには、Tablix データ領域の行ヘッダーのプロパティを設定します。 入れ子になった行グループの行ヘッダーは自動的に追加されます。  
  
 [トップに戻る](#Top)  
  
###  <a name="TableNoGroups"></a> 行グループを持たないテーブル  
 既定では、グループを持たない単純なテーブルには、詳細グループが含まれます。 次の図は、カテゴリ、注文番号、および売上データを表示するテーブルを示したものです。  
  
 ![デザイン、1 つの静的行と 1 つの動的行があるテーブル](../../reporting-services/report-design/media/rs-tableheaderstaticdesign.gif "デザイン、1 つの静的行と 1 つの動的行があるテーブル")  
  
 テーブルが Tablix 本体領域だけで構成されているため点線はありません。 先頭行は、列ヘッダーの表示に使用されており、グループに関連付けられていない静的な Tablix メンバーを表します。 2 つ目の行は、詳細データの表示に使用されており、詳細グループに関連付けられた動的な Tablix メンバーを表します。 次の図に、このテーブルのプレビューを示します。  
  
 ![プレビュー、1 つの静的行と 1 つの動的行があるテーブル](../../reporting-services/report-design/media/rs-tableheaderstaticpreview.gif "プレビュー、1 つの静的行と 1 つの動的行があるテーブル")  
  
 列見出しを繰り返し表示するか固定するには、Tablix データ領域定義に属する静的な行の Tablix メンバーのプロパティを設定します。 静的な行を選択するには、グループ化ペインの詳細設定モードを使用する必要があります。 次の図に、行グループ ペインを示します。  
  
 ![行グループ、1 つの静的行と 1 つの動的行があるテーブル](../../reporting-services/report-design/media/rs-tableheaderstaticgroupingpanedefault.gif "行グループ、1 つの静的行と 1 つの動的行があるテーブル")  
  
 次の図は、テーブルの行グループに対応する静的および動的な Tablix メンバーを詳細設定モードで表示したところです。  
  
 ![行グループ、既定のテーブル用の詳細設定](../../reporting-services/report-design/media/rs-tableheaderstaticgroupingpaneadvanced.gif "行グループ、既定のテーブル用の詳細設定")  
  
 Tablix メンバーの列見出しを繰り返し表示するか固定するには、(**Static**) というラベルの付いた静的行を選択します。 選択した Tablix メンバーのプロパティがプロパティ ペインに表示されます。 この Tablix メンバーのプロパティを設定することにより、先頭行を繰り返し表示するか、常に表示した状態にするかを制御できます。  
  
 [トップに戻る](#Top)  
  
###  <a name="TableRowGroupsGroupHeader"></a> 行グループおよび行グループ領域を持つテーブル  
 単純なテーブルに行グループを追加した場合、デザイン画面のテーブルに行グループ領域が追加されます。 次の図は、Category に基づいた行グループを持つテーブルを示しています。  
  
 ![デザイン、1 つの行グループと詳細があるテーブル](../../reporting-services/report-design/media/rs-tableheaderdynamicwithgroupheadercelldesign.gif "デザイン、1 つの行グループと詳細があるテーブル")  
  
 点線は、Tablix 行グループ領域および Tablix 本体領域を表します。 行グループ領域に、行グループ ヘッダーはありますが、列グループ ヘッダーはありません。 次の図に、このテーブルのプレビューを示します。  
  
 ![プレビュー、1 つの行グループと詳細があるテーブル](../../reporting-services/report-design/media/rs-tableheaderdynamicwithgroupheadercellpreview.gif "プレビュー、1 つの行グループと詳細があるテーブル")  
  
 列見出しを繰り返し表示するか固定するには、前の例と同じアプローチを使用します。 次の図は、行グループ ペインの既定のビューを示しています。  
  
 ![行グループ、既定で動的メンバー](../../reporting-services/report-design/media/rs-tableheaderdynamicgroupingpanedefault.gif "行グループ、既定で動的メンバー")  
  
 Tablix メンバーを表示するには、次の図のように、行グループ ペインの **詳細設定** モードを使用します。  
  
 ![行グループ、詳細設定モードで静的メンバー](../../reporting-services/report-design/media/rs-tableheaderdynamicwithgroupheadercelladvanced.gif "行グループ、詳細設定モードで静的メンバー")  
  
 **Static**、(**Static**)、Category、(**Details**) という一連の Tablix メンバーが並んでいます。 かっこ () 付きの Tablix メンバーは、対応するグループ ヘッダーがないことを表します。 列見出しを繰り返し表示するか固定するには、一番上の静的な Tablix メンバーを選択し、プロパティ ペインでプロパティを設定します。  
  
 [トップに戻る](#Top)  
  
###  <a name="TableRowGroupsNoGroupHeader"></a> 行グループはあるが行グループ領域を持たないテーブル  
 テーブルに行グループがあるにもかかわらず、行グループ領域が存在しない場合があります。 その原因として、次の 2 点が考えられます。  
  
-   当初は、行グループと行グループ領域を持つテーブルとして作成したが、後でその行グループ領域から列を削除した (列だけを削除し、グループを削除しなかった)。 たとえば、テーブルを単純なグリッド形式に変更しようとした場合などに起こります。  
  
-   以前の (Tablix データ領域が導入される前の) RDL バージョン用に作成されたレポートをアップグレードした。  
  
 次の図は、行グループはあるが行グループ領域を持たないテーブルをデザイン画面で表示したところです。  
  
 ![デザイン、行グループを持ち、グループ ヘッダーは持たないテーブル](../../reporting-services/report-design/media/rs-tableheaderdynamicwithnogroupheadercelldesign.gif "デザイン、行グループを持ち、グループ ヘッダーは持たないテーブル")  
  
 このテーブルには、3 つの行があります。 先頭行には、列ヘッダーが表示されます。 2 つ目の行には、グループの値と小計が表示されます。 3 つ目の行には、詳細データが表示されます。 Tablix 本体領域しか存在しないため点線は表示されません。 次の図に、このテーブルのプレビューを示します。  
  
 ![プレビュー、行グループを持ち、グループ ヘッダーは持たないテーブル](../../reporting-services/report-design/media/rs-tableheaderdynamicwithnogroupheadercellpreview.gif "プレビュー、行グループを持ち、グループ ヘッダーは持たないテーブル")  
  
 行を繰り返し表示するか固定するかを制御するには、各行の Tablix メンバーのプロパティを設定する必要があります。 既定のモードでは、この例とその前の例 (行グループとグループ ヘッダーを持つテーブルの例) との間に差はありません。 次の図は、このテーブルの既定のモードでのグループ化ペインを示しています。  
  
 ![行グループ、既定で動的メンバー](../../reporting-services/report-design/media/rs-tableheaderdynamicgroupingpanedefault.gif "行グループ、既定で動的メンバー")  
  
 しかし、詳細設定モードで見ると、このレイアウト構造が異なる Tablix メンバーで構成されていることがわかります。 次の図は、このテーブルの詳細設定モードでのグループ化ペインを示しています。  
  
 ![行グループ、詳細設定、グループ ヘッダーなし](../../reporting-services/report-design/media/rs-tableheaderdynamicwithnogroupheadercelladvanced.gif "行グループ、詳細設定、グループ ヘッダーなし")  
  
 [行グループ] ペインには、(**Static**)、(Category)、(**Static**)、および (**Details**) の各 Tablix メンバーが一覧表示されます。 列見出しを繰り返し表示するか固定するには、一番上の (**Static**) という Tablix メンバーを選択し、プロパティ ペインでプロパティを設定します。  
  
 [トップに戻る](#Top)  
  
## <a name="renderer-support-for-repeating-or-freezing-headers"></a>ヘッダーの繰り返し表示と固定表示をサポートするレンダラー  
 ヘッダーの繰り返しまたは固定に対応しているかどうかは、レンダラーによって異なります。  
  
 物理ページが使用されるレンダラー (PDF、画像、印刷) では、次の機能がサポートされます。  
  
-   Tablix データ領域が複数のページにわたって横方向に展開された場合に、行ヘッダーを繰り返し表示する。  
  
-   Tablix データ領域が複数のページにわたって下方向に展開された場合に、列ヘッダーを繰り返し表示する。  
  
 加えて、ソフト改ページが使用されるレンダラー (Web ポータル、レポート プレビュー、またはレポート ビューアー コントロール) では、次の機能がサポートされます。  
  
-   レポートを横方向にスクロールしたときに行ヘッダーを表示したままにする。  
  
-   レポートを下方向にスクロールしたときに列ヘッダーを表示したままにする。  
  
 詳しくは、「[レンダリングの動作 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/rendering-behaviors-report-builder-and-ssrs.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [データのフィルター、グループ化、および並べ替え (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [テーブル、マトリックス、および一覧 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)   
 [Reporting Services の改ページ &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/pagination-in-reporting-services-report-builder-and-ssrs.md)   
 [レポートのエクスポート &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-builder/export-reports-report-builder-and-ssrs.md)  
  
  
