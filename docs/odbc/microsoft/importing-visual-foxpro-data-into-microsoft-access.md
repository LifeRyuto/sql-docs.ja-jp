---
title: Visual FoxPro データを Microsoft Access にインポートする |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- importing data [ODBC]
- FoxPro ODBC driver [ODBC], Access
- Visual FoxPro data [ODBC], Access
- Visual FoxPro ODBC driver [ODBC], Access
- Visual FoxPro data [ODBC], importing
ms.assetid: a3591295-0a76-4e3c-b4fa-8bd4f1cde705
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 557b5505b9eb6a15080a7d0495df2e63aefd2d76
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68085543"
---
# <a name="importing-visual-foxpro-data-into-microsoft-access"></a>Visual FoxPro データの Microsoft Access へのインポート
[インポート] オプションを使用して、Visual FoxPro データベースに格納されているデータを Microsoft Access データベースにインポートできます。  
  
### <a name="to-import-visual-foxpro-data-into-a-microsoft-access-database"></a>Visual FoxPro データを Microsoft Access データベースにインポートするには  
  
1.  Microsoft Access データベースを開きます。  
  
2.  [ファイル] メニューの [外部データの取り込み]、[インポート] の順に選択します。  
  
3.  [インポート] ダイアログボックスの [ファイルの種類] ボックスの一覧で、[ODBC データベース] を選択します。  
  
4.  [SQL データソース] ダイアログボックスで、クエリを実行する FoxPro データに接続する Visual FoxPro データソースを選択し、[OK] をクリックします。  
  
5.  [オブジェクトのインポート] ダイアログボックスで、インポートする1つ以上のテーブルを選択し、[OK] をクリックします。 インポートした Visual FoxPro テーブルの名前は、Microsoft Access データベースの [テーブル] タブに表示されます。  
  
 これで、Microsoft Access を使用して、インポートした Visual FoxPro テーブルのデータを操作できるようになりました。 インポートするデータは、Visual FoxPro に格納されているデータのスナップショットです。インポートされたデータに加えた変更は、Visual FoxPro データソースには返されません。  
  
 Visual FoxPro データソースのデータを変更するために Microsoft Access で行った変更が必要な場合は、「 [Microsoft access からの Visual Foxpro データのクエリと更新](../../odbc/microsoft/querying-and-updating-visual-foxpro-data-from-microsoft-access.md)」を参照してください。
