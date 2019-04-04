---
title: Blob と OLE オブジェクト |Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- BLOBs, OLE objects
- BLOBs
- storage object [OLE DB]
- SQL Server Native Client OLE DB provider, BLOBs
- large data, OLE objects
ms.assetid: 767fa2f6-9cd2-436f-add5-e760bed29a58
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 48cb02feac227ad224ffed05fe60c1e78c97406c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47742300"
---
# <a name="blobs-and-ole-objects"></a>BLOB と OLE オブジェクト
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーが公開、 **ISequentialStream**コンシューマーへのアクセスをサポートするインターフェイス[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **ntext**、**テキスト**、**イメージ**、 **varchar (max)**、 **nvarchar (max)**、 **varbinary (max)**、し、xml データ型とバイナリ ラージ オブジェクト (Blob). **ISequentialStream** の **Read** メソッドを使用すると、扱いやすい単位で大量のデータを取得できます。  
  
 この機能を示すサンプルについては、[大量のデータを設定&#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/set-large-data-ole-db.md)を参照してください。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーを使用してコンシューマーに実装された**IStorage**データ変更のため、コンシューマーはアクセサーにインターフェイス ポインターを提供するときのインターフェイスにバインドされています。  
  
 大きな値のデータ型、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーが型での想定サイズのチェック**IRowset**や DDL インターフェイス。 持つ列**varchar**、 **nvarchar**、および**varbinary**最大サイズが無制限に設定を持つデータ型は、スキーマ行セットとのインターフェイスを通じて ISLONG と表されます列のデータ型を返します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーが公開、 **varchar (max)**、 **varbinary (max)** と**nvarchar (max)** 型 DBTYPE_STR、DBTYPE_BYTES、および DBTYPE_ としてWSTR それぞれします。  
  
 アプリケーションではこれらの型を使用するには、次のオプションがあります。  
  
-   データ型 DBTYPE_STR、DBTYPE_BYTES、または DBTYPE_WSTR としてバインドします。 バッファーのサイズが十分でない場合、これらのデータ型は以前のリリースでの動作と同様に (以前よりも大きな値を格納できるようになりましたが)、切り捨てが行われます。  
  
-   データ型としてバインドし、DBTYPE_BYREF も指定します。  
  
-   DBTYPE_IUNKNOWN としてバインドし、ストリーミングを使用します。  
  
 DBTYPE_IUNKNOWN にバインドすると、ISequentialStream ストリーム機能が使用されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、DBTYPE_IUNKNOWN をストアド プロシージャがこれらのデータを返すシナリオを容易にする大きな値データ型の DBTYPE_IUNKNOWN として公開される戻り値の型として、出力パラメーターのバインドをサポートしていますクライアント。  
  
## <a name="storage-object-limitations"></a>ストレージ オブジェクトの制限事項  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、1 つ開いているストレージ オブジェクトのみをサポートできます。 複数の **ISequentialStream** インターフェイス ポインターへの参照を取得するために、複数のストレージ オブジェクトを開こうとすると、DBSTATUS_E_CANTCREATE が返されます。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダー、DBPROP_BLOCKINGSTORAGEOBJECTS の読み取り専用プロパティの既定値は VARIANT_TRUE です。 この値は、ストレージ オブジェクトがアクティブである場合に、(ストレージ オブジェクト以外の) 一部のメソッドが失敗して E_UNEXPECTED が返されることを示します。  
  
-   記憶域のコンシューマーに実装されたオブジェクトによって表示されるデータの長さが正常に行う必要があります、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーのストレージ オブジェクトを参照する行アクセサーの作成時にします。 コンシューマー側では、アクセサーの作成に使用する DBBINDING 構造体に長さのインジケーターをバインドする必要があります。  
  
-   コンシューマーを 1 つの大きなデータ値を超える行が含まれています、DBPROP_ACCESSORDER が DBPROPVAL_AO_RANDOM ではない場合は、いずれかを使用する必要があります、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダー カーソルでサポートされている行セットを行のデータを取得またはすべての大きなデータを処理する前に値をその他の行の値を取得しています。 DBPROP_ACCESSORDER が DBPROPVAL_AO_RANDOM の場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、任意の順序でアクセスできるようにバイナリ ラージ オブジェクト (Blob) として、すべての xml データ型をキャッシュします。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [大きなデータの取得](../../relational-databases/native-client-ole-db-blobs/getting-large-data.md)  
  
-   [大きなデータの設定](../../relational-databases/native-client-ole-db-blobs/setting-large-data.md)  
  
-   [BLOB 出力パラメーターのストリーミング サポート](../../relational-databases/native-client-ole-db-blobs/streaming-support-for-blob-output-parameters.md)  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)   
 [大きな値の型の使用](../../relational-databases/native-client/features/using-large-value-types.md)  
  
  
