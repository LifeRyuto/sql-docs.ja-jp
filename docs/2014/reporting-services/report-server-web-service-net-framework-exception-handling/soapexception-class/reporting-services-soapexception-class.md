---
title: Reporting Services SoapException クラス | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- exceptions [Reporting Services], SoapException class
- SoapException class
ms.assetid: 2cec49ee-20b1-40eb-a75b-0908d9c05b34
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: ac8b0b7a36cc3ecff37ba0d74167b99458eb5e77
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56027203"
---
# <a name="reporting-services-soapexception-class"></a>Reporting Services SoapException クラス
  発生が予想される [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] のエラーには、対処が必要です。 たとえば、ユーザーにフォルダーの作成を要求するアプリケーションでは、ユーザーが既に存在するフォルダーを作成する可能性があります。 開発者としては、アプリケーションのフォルダー名フィールドとパス フィールドにユーザーが入力する内容を制限することはできません。ただし、既に存在するアイテムをユーザーが誤って作成しようとしたとき、どのように対処するかを指定することは可能です。  
  
 エラー状態を容易に検出できるようにするため、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] は例外のエラー コードを分類し、**SoapException** クラスのプロパティを使用してエラーの分類を返します。 詳細については、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK ドキュメントの「SoapException クラス」を参照してください。  
  
 次の表は、**SoapException** クラスのパブリック プロパティを示しています。  
  
|パブリック プロパティ|説明|  
|---------------------|-----------------|  
|**Actor**|例外の原因となったコード。 値は Web サービス メソッドへの URL です。|  
|**Detail**|アプリケーション固有のエラー情報。 この値は、レポート サーバーによって XML 形式で設定されます。 詳細については、「[Detail プロパティ](detail-property.md)」と「[Detail プロパティを使用したエラー処理](../best-practices/using-the-detail-property-to-handle-specific-errors.md)」を参照してください。|  
|**HelpLink**|エラーに関連付けられたヘルプ ファイルへの URL または URN。 通常、この値は、Web サービスによって [!INCLUDE[msCoName](../../../includes/msconame-md.md)] ヘルプとサポート サイトの URL に設定されます。 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] では発生するエラーのヘルプ リンクが複数サポートされているので、レポート サーバーは、**Detail** プロパティの一部としてヘルプ リンク情報を設定します。 詳細については、「[HelpLink 要素](helplink-element.md)」を参照してください。|  
|**メッセージ**|エラーを説明するローカライズされたメッセージ。 このテキストはアプリケーションの UI に表示される場合があります。|  
  
## <a name="see-also"></a>参照  
 [Reporting Services における例外処理の概要](../introducing-exception-handling-in-reporting-services.md)   
 [SoapException エラー テーブル](soapexception-errors-table.md)  
  
  
