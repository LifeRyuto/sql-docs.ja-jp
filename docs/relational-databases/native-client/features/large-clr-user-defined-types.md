---
title: 大きな CLR ユーザー定義型 |Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.reviewer: ''
ms.prod: sql
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- large CLR user-defined types
ms.assetid: b65eb61d-ccf6-49c0-98e7-9a4ef4b2f790
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0176ba03151b084cb26eda03969b1e83afb1820d
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56020274"
---
# <a name="large-clr-user-defined-types"></a>大きな CLR ユーザー定義型
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  SQL Server 2005 では、共通言語ランタイム (CLR) のユーザー定義型 (UDT) のサイズは 8,000 バイトに制限されていました。 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 以降では、この制限が解除されます。 CLR UDT はラージ オブジェクト (LOB) 型と同様に扱われるようになりました。 つまり、8,000 バイト以下の UDT は SQL Server 2005 の場合と同じように動作しますが、8,000 バイトを超える UDT もサポートされるようになり、そのサイズは "無制限" として報告されます。  
  
 詳細については、[Large CLR User-Defined 型&#40;OLE DB&#41; ](../../../relational-databases/native-client/ole-db/large-clr-user-defined-types-ole-db.md)と[Large CLR User-Defined 型&#40;ODBC&#41;](../../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md)を参照してください。  
  
## <a name="use-cases"></a>ユース ケース  
 ODBC の場合、大きな UDT のサポートには、UDT 値を実行時データ パラメーターとして個別に送信する機能が含まれています。 これは、SQLPutData を使用して行います。  
  
 OLE DB の場合、大きな UDT のサポートには、ISequentialStream バインドを使用したサーバーとの間の UDT 値のストリームの送受信機能が含まれています。  
  
 8,000 バイト以下の UDT は SQL Server 2005 の場合と同じように動作します。 OLE DB、ISequentialStream バインドを使用して、小さな Udt をストリーミングすることもできます。  
  
 場合によっては、ネイティブ コードで CLR UDT のコンテンツを認識する必要がありますが、マネージド オブジェクトのインスタンスを作成する必要はありません。 この場合は、カスタムのシリアル化を使用して、サーバーの UDT 値をクライアントで認識される形式に変換することができます。  
  
 既存のデータ アクセス コードを使用するアプリケーションの場合は、クライアント側で CLR UDT の動作を利用できます。そのためには、ネイティブ API を使用して UDT を取得し、混合モードのアプリケーションで C++ CLI 相互運用機能を使用して UDT のインスタンスを作成します。  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client の機能](../../../relational-databases/native-client/features/sql-server-native-client-features.md)  
  
  
