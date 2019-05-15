---
title: URL アクセスを使用してレポートをエクスポートする | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
helpviewer_keywords:
- formats [Reporting Services], URL rendering
- URL access [Reporting Services], rendering formats
ms.assetid: 6a3b7fc3-3d91-4d12-8371-42ea12e74517
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 7a6d6d9dd46e6c54dc9be72e30a19498bf39391c
ms.sourcegitcommit: e4794943ea6d2580174d42275185e58166984f8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/09/2019
ms.locfileid: "65504004"
---
# <a name="export-a-report-using-url-access"></a>URL アクセスを使用してレポートをエクスポートする
  *rs:Format* URL パラメーターを使用すると、レポートを表示する形式を必要に応じて指定できます。  HTML4.0 および HTM5 (表示拡張機能) の場合は、ブラウザーにレンダリングされます。他の形式の場合は、レポート出力をローカル ファイルに保存するよう促すメッセージが表示されます。  
  
 たとえば、ネイティブ モードのレポート サーバーから直接レポートの PDF コピーを取得するには、次の URL を使用します。  
  
```  
https://myrshost/ReportServer?/myreport&rs:Format=PDF  
```  

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
  
 また、SharePoint 統合モードのレポート サーバーから取得するには、次の URL を使用します。  
  
```  
https://myspsite/subsite/_vti_bin/reportserver?https://myspsite/subsite/myrereport.rdl&rs:Format=PDF  
```  
 
::: moniker-end
 
 たとえば、ブラウザーで次の URL コマンドを実行すると、レポート サーバーの名前付きインスタンスから PPTX レポートがエクスポートされます。  
  
```  
https://servername/ReportServer_THESQLINSTANCE/Pages/ReportViewer.aspx?%2freportfolder%2freport+name+with+spaces&rs:Format=pptx  
```  
  
 このパラメーターの有効値は、アクセス先レポート サーバーにインストールされているレポート表示拡張機能によって異なります。 一般的な拡張機能は HTML4.0、MHTML、IMAGE、EXCELOPENXML (xlsx)、WORDOPENXML (docx)、CSV、PDF、XML、および NULL です。 指定した表示拡張機能がレポート サーバーにインストールされていない場合は、レポートが表示されず、エラーが生成されてブラウザーに表示されます。  
  
 *Format* パラメーターを URL の一部として含めない場合は、レポート サーバーがブラウザーを検出し、適切な HTML 形式でレポートを表示します。  
  
## <a name="see-also"></a>参照  
 [URL アクセス &#40;SSRS&#41;](../reporting-services/url-access-ssrs.md)   
 [URL アクセス パラメーター リファレンス](../reporting-services/url-access-parameter-reference.md)  
  
  
