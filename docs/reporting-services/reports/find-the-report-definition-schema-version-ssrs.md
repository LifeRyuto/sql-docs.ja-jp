---
title: レポート定義スキーマのバージョンを確認する (SSRS) | Microsoft Docs
ms.date: 05/30/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reports
ms.topic: conceptual
helpviewer_keywords:
- XML schemas [Reporting Services]
- Report Definition Language, XML schema
- schemas [Reporting Services]
ms.assetid: 67954419-1b61-4481-a3b9-23b4ba7a5624
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 67f1311e3f8bde71c52301178bf242d88e62c3a0
ms.sourcegitcommit: dda9a1a7682ade466b8d4f0ca56f3a9ecc1ef44e
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65576416"
---
# <a name="find-the-report-definition-schema-version-ssrs"></a>レポート定義スキーマのバージョンを確認する (SSRS)

レポート定義ファイルでは、rdl ファイルの検証に使用されるレポート定義スキーマのバージョンに対応して、RDL 名前空間が指定されます。 以前の名前空間に対応するレポートが作成済みの場合、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] のレポート デザイナーやレポート ビルダーなどのレポート作成環境で .rdl ファイルを開くと、バックアップ ファイルが自動的に作成され、レポートが現在の名前空間にアップグレードされます。 アップグレードされたレポート定義を保存すると、変換された .rdl ファイルが保存されることになります。 これは、レポート定義をアップグレードする唯一の方法です。 レポート定義そのものはレポート サーバーでアップグレードされません。 コンパイル済みレポートが、レポート サーバーで自動的にアップグレードされます。 詳細については、「 [Upgrade Reports](../../reporting-services/install-windows/upgrade-reports.md)」を参照してください。  
  
### <a name="how-to-identify-the-rdl-schema-version-of-a-report"></a>レポートの RDL スキーマのバージョンを確認する方法  
  
1.  メモ帳や、XML を表示できる XML Notepad 2007 などのアプリケーションでレポートの .rdl ファイルを開きます。  
  
     スキーマ名前空間は XML の Report 要素で指定されます。 たとえば、次の Report 要素では、レポート デザイナーの名前空間とレポート定義の名前空間が指定されています。  
  
    ```  
    <Report xmlns:rd=https://schemas.microsoft.com/SQLServer/reporting/reportdesigner   
    xmlns="https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition">  
    ```  
  
     レポート定義の名前空間は、 `https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition`という URL で指定されています。  
  
### <a name="how-to-identify-the-rdl-schema-version-of-report-designer"></a>レポート デザイナーの RDL スキーマのバージョンを確認する方法  
  
1.  新しいプロジェクトを開きます。 選択したプロジェクトのバージョンにより、RDL スキーマのバージョンが決まります。 SQL Server では、複数のスキーマ バージョンがサポートされています。 詳細については、「[SQL Server データ ツールの配置およびバージョン サポート](../../reporting-services/tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md)」を参照してください。  
  
2.  **[プロジェクト]** メニューの **[新しい項目の追加]** をクリックします。 **[新しい項目の追加]** ダイアログ ボックスが表示されます。  
  
3.  **[テンプレート]** ペインで **[レポート]** をクリックします。  
  
4.  **[名前]** にレポートの名前を入力するか、既定の名前をそのまま使用します。  
  
5.  **[追加]** をクリックします。 レポート デザイナーの [デザイン] ビューに新しい空のレポートが表示されます。  
  
6.  **[表示]** メニューの **[コード]** をクリックします。 レポート定義が XML ファイルとして表示されます。  
  
     スキーマ名前空間は XML の Report 要素で指定されます。 たとえば、次の Report 要素では、レポート デザイナーの名前空間とレポート定義の名前空間が指定されています。  
  
    ```  
    <Report xmlns:rd=https://schemas.microsoft.com/SQLServer/reporting/reportdesigner  
    xmlns="https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition">  
    ```  
  
     レポート定義の名前空間は、 `https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition`  
  
### <a name="how-to-identify-the-rdl-schema-version-on-the-report-server"></a>レポート サーバー上で RDL スキーマのバージョンを確認する方法  
  
-   レポート マネージャーで、レポート サーバーの URL を入力します。 たとえば、次の URL はローカル コンピューターのレポート サーバーを指定しています。  
  
     `https://localhost/reportserver/reportdefinition.xsd`  
  
     .xsd ファイルがブラウザーに表示されます。  
  
     スキーマ名前空間は XML の schema 要素で指定されます。 たとえば、次の schema 要素では、 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]によって内部的に使用される targetNamespace 参照、スキーマ自体 (xsd) の xsd 参照、およびレポート定義参照の 3 つの名前空間が指定されています。  
  
    ```  
    <xsd:schema   
    targetNamespace="https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition"   
    xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
    xmlns="https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition"   
    elementFormDefault="qualified">  
    ```  
  
     レポート定義の名前空間は、 `https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition`  

## <a name="next-steps"></a>次の手順

[レポートのアップグレード](../../reporting-services/install-windows/upgrade-reports.md)   
[レポート定義言語 (Report Definition Language)](../../reporting-services/reports/report-definition-language-ssrs.md)  

その他の質問 [Reporting Services のフォーラムに質問してみてください](https://go.microsoft.com/fwlink/?LinkId=620231)
