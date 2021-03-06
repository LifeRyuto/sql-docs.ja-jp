---
title: DCOM を使用するためのクライアントへのビジネスオブジェクトの登録 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- business objects in RDS [ADO]
ms.assetid: 75a21910-607f-463a-ae18-a17130dafb7e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 31af4a68ec830a5fd514173c831ce3863fef7443
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67922354"
---
# <a name="registering-business-objects-on-the-client-for-use-with-dcom"></a>DCOM で使用するためにクライアントにビジネス オブジェクトを登録する
カスタムビジネスオブジェクトでは、クライアント側がプログラム名 (ProgId) を DCOM 経由で使用できる識別子 (CLSID) にマップできるようにする必要があります。 このため、DCOM オブジェクトの ProgID は、クライアント側のレジストリにあり、サーバー側ビジネスオブジェクトのクラス ID にマップされている必要があります。 その他のサポートされているプロトコル (HTTP、HTTPS、およびインプロセス) では、これは必要ありません。  
  
> [!IMPORTANT]
>  Windows 8 と windows Server 2012 以降では、RDS サーバーコンポーネントが Windows オペレーティングシステムに含まれなくなりました (詳細については、「Windows 8 および[Windows server 2012 の互換性に関するクックブック](https://www.microsoft.com/download/details.aspx?id=27416)」を参照してください)。 RDS クライアントコンポーネントは、今後のバージョンの Windows では削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションは、 [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)に移行する必要があります。  
  
 たとえば、"{00112233-4455-6677-8899-00AABBCCDDEE}" など、特定のクラス ID を持つ MyBObj という名前のサーバー側ビジネスオブジェクトを公開する場合は、次のエントリがクライアント側レジストリに追加されていることを確認します。  
  
```console
[HKEY_CLASSES_ROOT]  
\MyBObj\Clsid\(Default) "{00112233-4455-6677-8899-00AABBCCDDEE}"  
```


