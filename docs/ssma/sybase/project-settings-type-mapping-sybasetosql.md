---
title: プロジェクトの設定 (型のマッピング) (SybaseToSQL) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 2698fb3a-f9e6-4e04-94e0-dad289d7ed0a
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: d7b16bdf3717fa14f91af41663cbd65365eac52a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68028660"
---
# <a name="project-settings-type-mapping-sybasetosql"></a>プロジェクトの設定 (型のマッピング) (SybaseToSQL)
[**プロジェクトの設定**] ダイアログボックスの [型マッピング] ページには、Ssma が Sybase Adaptive Server ENTERPRISE (ASE) データ型[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をデータ型に変換する方法をカスタマイズする設定が含まれています。  
  
[型マッピング] ページは、[**プロジェクトの設定**] ダイアログボックスと [**既定のプロジェクトの設定**] ダイアログボックスで使用できます。  
  
-   すべての今後の SSMA プロジェクトに対して型マッピング設定を指定するには、[**ツール**] メニューの [**既定のプロジェクト設定**] を選択し、[移行先の**バージョン**] ドロップダウンから表示または変更する設定が必要な [移行プロジェクトの種類] を選択して、左側のウィンドウの下部にある [**型マッピング**] を選択します。  
  
-   現在のプロジェクトの設定を指定するには、[**ツール**] メニューの [**プロジェクトの設定**] をクリックし、左側のウィンドウの下部にある [**型マッピング**] を選択します。  
  
## <a name="options"></a>オプション  
**ソースの種類**  
マップされた ASE データ型。  
  
**ターゲットの種類**  
指定さ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]れた ASE データ型のターゲットデータ型。  
  
既定の SSMA for Sybase の型マッピングについては、次のセクションの表を参照してください。  
  
**追加**  
[マッピング] ボックスの一覧にデータ型を追加する場合にクリックします。  
  
**[編集]**  
[マッピング] ボックスの一覧で選択したデータ型を編集する場合にクリックします。  
  
**Remove**  
クリックすると、選択したデータ型マッピングが [マッピング] ボックスの一覧から削除されます。  
  
**既定値にリセット**  
クリックすると、[型マッピング] の一覧が SSMA の既定値にリセットされます。  
  
## <a name="default-type-mapping"></a>既定の型マッピング  
次の表に、ASE と[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型の既定の型マッピングを示します。  
  
|ASE データ型|SQL Server データ型|  
|-----------------|------------------------|  
|**bigint**|**bigint**|  
|**binary**|**binary**|  
|**バイナリ [\*..8000]**|**binary [\*]**|  
|**バイナリ [8001..\*]**|**varbinary(max)**|  
|**bit**|**bit**|  
|**char**|**char**|  
|**文字の変化**|**varchar**|  
|**char varying [\*..8000]**|**varchar [\*]**|  
|**文字の変化 [8001.\*.]**|**varchar(max)**|  
|**char [\*..8000]**|**char [\*]**|  
|**char [8001..\*;]**|**varchar(max)**|  
|**記号**|**char**|  
|**文字の変化**|**varchar**|  
|**文字の変化\*(..8000]**|**varchar [\*]**|  
|**文字の変化 [8001.\*.]**|**varchar(max)**|  
|**文字 [\*..8000]**|**char [\*]**|  
|**文字 [8001..\*]**|**varchar(max)**|  
|**date**|**date**|  
|**DATETIME**|**datetime2 [3]**|  
|**alpha**|**decimal**|  
|**dec [\*..\*]**|**decimal [\*]**|  
|**dec [\*..\*][\*..\*]**|**decimal [\*] [\*]**|  
|**decimal**|**decimal**|  
|**decimal [\*..\*]**|**decimal [\*]**|  
|**decimal [\*..\*][\*..\*]**|**decimal [\*] [\*]**|  
|**倍精度**|**float [53]**|  
|**float**|**float [53]**|  
|**float [\*..最大**|**float [24]**|  
|**float [16..\*]**|**float [53]**|  
|**絵**|**絵**|  
|**int**|**int**|  
|**整数 (integer)**|**int**|  
|**longsysname**|**nvarchar [255]**|  
|**money**|**money**|  
|**national char**|**nchar**|  
|**national char [\*..4000]**|**nchar [\*]**|  
|**各国語文字の変化**|**nvarchar**|  
|**national char varying [\*..4000]**|**nvarchar [\*]**|  
|**national char varying [4001..\*]**|**nvarchar(max)**|  
|**national char [4001..\*]**|**nvarchar(max)**|  
|**national character**|**nchar**|  
|**national character [\*..4000]**|**nchar [\*]**|  
|**national 文字 [4001..\*]**|**nvarchar(max)**|  
|**各国語文字の変化**|**nvarchar**|  
|**各国語文字の\*変化 [..4000]**|**nvarchar [\*]**|  
|**各国語文字のさまざまな [\*4001..]**|**nvarchar(max)**|  
|**national varchar**|**nvarchar**|  
|**national varchar [\*..4000]**|**nvarchar [\*]**|  
|**national varchar [4001..\*]**|**nvarchar(max)**|  
|**nchar**|**nchar**|  
|**nchar の変化**|**nvarchar**|  
|**nchar の変化\*[..4000]**|**nvarchar [\*]**|  
|**nchar の変化 [4001.\*.]**|**nvarchar(max)**|  
|**nchar [\*..4000]**|**nchar [\*]**|  
|**nchar [4001..\*]**|**nvarchar(max)**|  
|**番号**|**番号**|  
|**数値 [\*..\*]**|**数値 [\*]**|  
|**数値 [\*..\*][\*..\*]**|**数値 [\*] [\*]**|  
|**nvarchar**|**nvarchar**|  
|**nvarchar [\*..4000]**|**nvarchar [\*]**|  
|**nvarchar [4001..\*]**|**nvarchar(max)**|  
|**本当の**|**float [24]**|  
|**smalldatetime**|**smalldatetime**|  
|**smallint**|**smallint**|  
|**smallmoney**|**smallmoney**|  
|**sysname**|**nvarchar [128]**|  
|**sysname [\*..\*]**|**nvarchar [255]**|  
|**本文**|**本文**|  
|**time**|**時刻 [3]**|  
|**timestamp**|**rowversion**|  
|**tinyint**|**tinyint**|  
|**ユニホーム**|**nchar**|  
|**多様**|**nvarchar**|  
|**さまざまな変更 [\*..4000]**|**nvarchar [\*]**|  
|**さまざまなバリエーション [4001..\*]**|**nvarchar(max)**|  
|**[\*..4000]**|**nchar [\*]**|  
|**このようにして、[\*4001..]**|**nvarchar(max)**|  
|**unitext**|**nvarchar(max)**|  
|**univarchar**|**nvarchar**|  
|**univarchar [\*..4000]**|**nvarchar [\*]**|  
|**univarchar [4001..\*]**|**nvarchar(max)**|  
|**符号なし bigint**|**数値 [20] [0]**|  
|**unsigned int**|**bigint**|  
|**unsigned smallint**|**int**|  
|**unsigned tinyint**|**tinyint**|  
|**varbinary**|**varbinary**|  
|**varbinary [\*..8000]**|**varbinary [\*]**|  
|**varbinary [8001..\*]**|**varbinary(max)**|  
|**varchar**|**varchar**|  
|**varchar [\*..8000]**|**varchar [\*]**|  
|**varchar [8001..\*]**|**varchar(max)**|  
  
