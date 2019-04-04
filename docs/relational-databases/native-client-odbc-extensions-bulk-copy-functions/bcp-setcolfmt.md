---
title: bcp_setcolfmt |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- bcp_setcolfmt
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_setcolfmt function
ms.assetid: afb47987-39e7-4079-ad66-e0abf4d4c72b
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9fd6ac6c5dccd9f33e2e8389f5847a5ac73b795d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47694200"
---
# <a name="bcpsetcolfmt"></a>bcp_setcolfmt
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  **Bcp_setcolfmt**関数は、 [bcp_colfmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md)します。 列の照合順序を指定するときに、 **bcp_setcolfmt**関数を使用する必要があります。 [bcp_setbulkmode](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-setbulkmode.md) 1 つ以上の列の形式を指定するために使用できます。  
  
 この関数では、一括コピー操作で列の形式を柔軟に指定できます。 個別の列形式属性を設定する場合に、この関数を使用します。 呼び出しごとに**bcp_setcolfmt** 1 つの列形式属性を設定します。  
  
 **Bcp_setcolfmt**関数は、ユーザー ファイル内のデータのソースまたはターゲットの形式を指定します。 ソースの形式として使用すると**bcp_setcolfmt**内のテーブルに一括コピーでデータのデータ ソースとして使用される既存のデータ ファイルの形式を指定します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 指定された列の形式を使用して、データ ファイルを作成する先の形式として使用するときに**bcp_setcolfmt**します。  
  
## <a name="syntax"></a>構文  
  
```  
  
RETCODE bcp_setcolfmt (  
        HDBC hdbc,  
        INT field,  
        INT property,  
        void* pValue,  
        INT cbValue);  
```  
  
## <a name="arguments"></a>引数  
 *hdbc*  
 一括コピーが有効な ODBC 接続ハンドルです。  
  
 *field*  
 プロパティを設定する列の序数です。  
  
 *property*  
 プロパティ定数のいずれかを指定します。 次の表に、プロパティ定数を示します。  
  
|プロパティ|値|説明|  
|--------------|-----------|-----------------|  
|BCP_FMT_TYPE|BYTE|ユーザー ファイル内にある列のデータ型です。 データベース テーブル内の対応する列のデータ型と異なる場合は、一括コピーでは可能な限りデータを変換します。<br /><br /> BCP_FMT_TYPE パラメーターは、ODBC C データ型の列挙子ではなく、sqlncli.h 内の SQL Server データ型トークンで列挙されます。 たとえば、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 固有の SQLCHARACTER 型を使用して、ODBC の SQL_C_CHAR 型の文字列を指定できます。<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータ型に対して既定のデータ表現を指定するには、このパラメーターに 0 を設定します。<br /><br /> SQL server が BCP_FMT_TYPE SQLDECIMAL または SQLNUMERIC を基になる列がない場合、ファイルへの一括コピーの**10 進**または**数値**の既定の有効桁数と小数点を使用します。 それ以外の場合、ソース列がある場合**decimal**または**数値**、有効桁数と基になる列の小数点以下桁数を使用します。|  
|BCP_FMT_INDICATOR_LEN|INT|インジケーター (プレフィックス) のバイト単位の長さです。<br /><br /> これは、列データ内にある長さのインジケーターや NULL インジケーターのバイト単位の長さです。 インジケーターの長さの有効値は、0 (インジケーターを使用しない)、1、2、または 4 です。<br /><br /> 一括コピーのインジケーターの既定の使用方法を指定するには、このパラメーターに SQL_VARLEN_DATA を設定します。<br /><br /> インジケーターは、メモリ内ではすべてのデータの直前に、データ ファイル内ではインジケーターを適用するデータの直前に配置します。<br /><br /> 複数の方法 (インジケーターと列の最大長、インジケーターとターミネータ シーケンスなど) を使用してデータ ファイルの列長を指定すると、一括コピーではコピーするデータの量が最も少なくなる方法が使用されます。<br /><br /> ユーザーの操作でデータの形式が調整されずに一括コピーで生成されたデータ ファイルには、列データの長さが異なる場合や、列の値に NULL が許容される場合にインジケーターが含まれます。|  
|BCP_FMT_DATA_LEN|DBINT|データ (列長) のバイト単位の長さです。<br /><br /> これは、ユーザー ファイル内にある列データのバイト単位の最大長です。長さのインジケーターやターミネータの長さは含まれません。<br /><br /> BCP_FMT_DATA_LEN を SQL_NULL_DATA に設定すると、データ ファイルの列に含まれるすべての値が NULL に設定されます。<br /><br /> また、BCP_FMT_DATA_LEN を SQL_VARLEN_DATA に設定すると、各列のデータの長さがシステムによって決定されます。 これは、列によっては、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からコピーされるデータの前に長さのインジケーターや NULL インジケーターを生成したり、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にコピーするデータにインジケーターが必要になる場合があることを意味します。<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の文字データ型やバイナリ データ型の場合は、BCP_FMT_DATA_LEN に SQL_VARLEN_DATA、SQL_NULL_DATA、0、正の値のいずれかを指定できます。 BCP_FMT_DATA_LEN が SQL_VARLEN_DATA の場合、システムは、長さのインジケーター (存在する場合) またはターミネータ シーケンスを使用してデータの長さを決定します。 長さのインジケーターとターミネータ シーケンスの両方を指定した場合、一括コピーはコピーするデータ量が少なくなる方法を使用します。 BCP_FMT_DATA_LEN が SQL_VARLEN_DATA の場合、データ型は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 文字型またはバイナリ型になります。長さのインジケーターとターミネータ シーケンスをどちらも指定しなかった場合は、システムからエラー メッセージが返されます。<br /><br /> BCP_FMT_DATA_LEN が 0 または正の値の場合、システムは最大データ長として BCP_FMT_DATA_LEN を使用します。 ただし、BCP_FMT_DATA_LEN に正の値を指定し、長さのインジケーターとターミネータ シーケンスを指定した場合、システムはコピーするデータ量が少なくなる方法を使用してデータ長を決定します。<br /><br /> BCP_FMT_DATA_LEN の値はデータのバイト数を表します。 文字データが Unicode ワイド文字で表されている場合、BCP_FMT_DATA_LEN パラメーター値が正の値のときは、各文字のサイズ (バイト数) に文字数を掛けた数を表します。|  
|BCP_FMT_TERMINATOR|LPCBYTE|この列で使用されるターミネータ シーケンス (ANSI または Unicode) を指すポインターです。 このパラメーターは主に文字データ型に対して有効です。これは、他のすべての型は固定長であったり、バイト数を正確に記録するために長さのインジケーターが必要になる (バイナリ データの場合) ためです。<br /><br /> 抽出されるデータが途中で終了されないようにしたり、ユーザー ファイル内のデータが途中で終了していないことを示すには、このパラメーターに NULL を設定します。<br /><br /> 複数の方法 (ターミネータと長さのインジケーター、ターミネータと列の最大長など) を使用してユーザー ファイルの列長を指定すると、一括コピーはコピーするデータの量が最も少なくなる方法を使用します。<br /><br /> 一括コピー API では、必要に応じて Unicode から MBCS への文字変換が実行されます。 このため、ターミネータのバイト文字列とそのバイト文字列の長さの両方を正しく設定するように注意する必要があります。|  
|BCP_FMT_SERVER_COL|INT|データベース内での列の序数位置。|  
|BCP_FMT_COLLATION|LPCSTR|照合順序名。|  
  
 *pValue*  
 関連付ける値へのポインター、*プロパティ*します。 このポインターにより、列形式のプロパティを個別に設定できます。  
  
 *cbvalue*  
 プロパティ バッファーのバイト単位の長さです。  
  
## <a name="returns"></a>戻り値  
 SUCCEED または FAIL。  
  
## <a name="remarks"></a>コメント  
 この関数は、 **bcp_colfmt**関数。 すべての機能**bcp_colfmt**で提供される**bcp_setcolfmt**関数。 さらに、列の照合順序もサポートされます。 列形式属性は、次に示した順番で設定することをお勧めします。  
  
 BCP_FMT_SERVER_COL  
  
 BCP_FMT_DATA_LEN  
  
 BCP_FMT_TYPE  
  
 **Bcp_setcolfmt**関数では、一括コピーのユーザー ファイルの形式を指定することができます。 次に、一括コピーに使用するフォーマットの内容を示します。  
  
-   ユーザー ファイルの列からデータベース列へのマッピング  
  
-   ユーザー ファイルの各列のデータ型  
  
-   各列の省略可能なインジケーターの長さ  
  
-   ユーザー ファイルの各列におけるデータの最大長  
  
-   各列の省略可能なターミネータ バイト シーケンス  
  
-   省略可能なターミネータ バイト シーケンスの長さ  
  
 呼び出しごとに**bcp_setcolfmt**のユーザー ファイルの 1 つの列の形式を指定します。 たとえば、5 つの列のユーザーのデータ ファイル内の 3 つの列の既定の設定を変更するにまず[bcp_columns](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md)**(5)** を呼び出して**bcp_setcolfmt**の 5 回これらの呼び出しの 3 つのカスタム形式を設定します。 残りの 2 つの呼び出しでは、BCP_FMT_TYPE を 0 に設定し、BCP_FMT_INDICATOR_LENGTH、BCP_FMT_DATA_LEN を設定し、 *cbValue* 0、SQL_VARLEN_DATA、0 とそれぞれします。 このプロシージャでは、5 つの列すべてをコピーします。それらの列のうち 3 つはカスタマイズされた形式でコピーされ、2 つは既定の形式でコピーされます。  
  
 **Bcp_columns**関数を呼び出す前に呼び出す必要があります**bcp_setcolfmt**します。  
  
 呼び出す必要があります**bcp_setcolfmt**ユーザー ファイル内の各列の各プロパティに 1 回です。  
  
 ユーザー ファイル内のすべてのデータを SQL Server テーブルにコピーする必要はありません。 列をスキップするには、列のデータの形式を指定する際に BCP_FMT_SERVER_COL パラメーターを 0 に設定します。 列をスキップする場合でも、その列の型を指定する必要があります。  
  
 [Bcp_writefmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-writefmt.md)形式指定を保存する関数を使用できます。  
  
## <a name="bcpsetcolfmt-support-for-enhanced-date-and-time-features"></a>bcp_setcolfmt による機能強化された日付と時刻のサポート  
 日付/時刻型の BCP_FMT_TYPE プロパティと共に使用される型がで指定されている[強化された日付と時刻型向けの一括コピーの変更&#40;OLE DB および ODBC&#41;](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)します。  
  
 詳細については、[日付と時刻の強化&#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)を参照してください。  
  
## <a name="see-also"></a>参照  
 [一括コピー関数](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
