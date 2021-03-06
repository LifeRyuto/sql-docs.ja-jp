---
title: カスタマイズファイルを理解する |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- customization file in RDS [ADO]
ms.assetid: 136f74bf-8d86-4a41-be66-c86cbcf81548
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 81a73044c1ab413fb2b49286814f3e6b3951c6c9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67921968"
---
# <a name="understanding-the-customization-file"></a>カスタマイズ ファイルの概要
カスタマイズファイルの各セクションヘッダーは、型とパラメーターを含む角かっこ (**[]**) で構成されています。 4つのセクションの種類は、**接続**、 **sql**、 **userlist**、または**ログ**のリテラル文字列によって示されます。 パラメーターは、リテラル文字列、既定値、ユーザー指定の識別子、または nothing です。  
  
> [!IMPORTANT]
>  Windows 8 と windows Server 2012 以降では、RDS サーバーコンポーネントが Windows オペレーティングシステムに含まれなくなりました (詳細については、「Windows 8 および[Windows server 2012 の互換性に関するクックブック](https://www.microsoft.com/download/details.aspx?id=27416)」を参照してください)。 RDS クライアントコンポーネントは、今後のバージョンの Windows では削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションは、 [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)に移行する必要があります。  
  
 したがって、各セクションは、次のセクションヘッダーのいずれかでマークされます。  
  
```console
  
[ connect default ] [ connect    
identifier   
] [ sql  default ] [ sql    
identifier   
] [ userlist    
identifier   
] [ logs ]  
  
```  
  
 セクションヘッダーには、次の部分があります。  
  
|要素|[説明]|  
|----------|-----------------|  
|**関連付け**|接続文字列を変更するリテラル文字列。|  
|**sql**|コマンド文字列を変更するリテラル文字列。|  
|**userlist**|特定のユーザーのアクセス権を変更するリテラル文字列。|  
|**ログアウト**|操作エラーを記録するログファイルを指定するリテラル文字列。|  
|**標準**|識別子が指定されていない場合、または見つからない場合に使用されるリテラル文字列。|  
|*識別子 (identifier)*|**接続**文字列または**コマンド**文字列内の文字列に一致する文字列。<br /><br /> -このセクションは、セクションヘッダーに**connect**が含まれており、識別子文字列が接続文字列で見つかった場合に使用します。<br />-このセクションは、セクションヘッダーに**sql**が含まれており、識別子文字列がコマンド文字列で見つかった場合に使用します。<br />-セクションヘッダーに**userlist**が含まれており、識別子文字列が**connect**セクション識別子と一致する場合は、このセクションを使用します。|  
  
 **DataFactory**は、クライアントパラメーターを渡すハンドラーを呼び出します。 ハンドラーは、適切なセクションヘッダー内の識別子と一致する文字列全体をクライアントパラメーターで検索します。 一致が見つかった場合は、そのセクションの内容がクライアントパラメーターに適用されます。  
  
 特定のセクションは、次の状況で使用されます。  
  
-   接続**セクションは**、クライアント接続文字列キーワード "**Data Source =**_value_" の値部分が**connect**セクション識別子と一致する場合に使用されます。 
  
-   Sql**セクション**は、クライアントのコマンド文字列に**sql**セクション識別子と一致する文字列が含まれている場合に使用されます。  
  
-   一致する識別子がない場合は、既定のパラメーターを使用した**connect**または**sql**セクションが使用されます。  
  
-   **Userlist** section 識別子が**connect**セクション識別子と一致する場合、 **userlist**セクションが使用されます。 一致するものがある場合は、 **userlist**セクションの内容が**connect**セクションによって管理される接続に適用されます。  
  
-   接続またはコマンド文字列内の文字列が**connect**または**sql**セクションヘッダーの識別子と一致せず、既定のパラメーターを持つ**connect**または**sql** section ヘッダーがない場合、クライアント文字列は変更なしで使用されます。  
  
-   **ログ**セクションは、 **DataFactory**が操作中のときに常に使用されます。  
  
## <a name="see-also"></a>参照  
 [カスタマイズファイルの接続セクション](../../../ado/guide/remote-data-service/customization-file-connect-section.md)   
 [カスタマイズファイルログセクション](../../../ado/guide/remote-data-service/customization-file-logs-section.md)   
 [カスタマイズファイル SQL セクション](../../../ado/guide/remote-data-service/customization-file-sql-section.md)   
 [カスタマイズファイルの UserList セクション](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)   
 [DataFactory のカスタマイズ](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [必要なクライアント設定](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [独自のカスタム ハンドラーの記述](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)

