---
title: CLR ルーチンのカスタム属性 |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- routines [CLR integration]
- SqlFacet attribute
- SqlTrigger attribute
- SqlProcedure attribute
- custom attributes [CLR integration]
- SqlUserDefinedAggregate attribute
- attributes [CLR integration]
- SqlMethod attribute
- SqlFunction attribute
- common language runtime [SQL Server], attributes
- SqlUserDefinedTypeAttribute attribute
ms.assetid: 95069d22-b05d-4670-b053-15ee2a664e33
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: c59df39f3d4d0df423f48df092e49e53dba1861c
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2018
ms.locfileid: "51664972"
---
# <a name="clr-integration-custom-attributes-for-clr-routines"></a>CLR ルーチン用の CLR 統合のカスタム属性
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  共通言語ランタイム (CLR) のルーチン、ユーザー定義型、および登録されているユーザー定義集計に示されている属性を適用できる[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]します。 属性が適用されない場合、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] は既定値を想定します。 示されている属性が定義されている、 **Microsoft.SqlServer.Server**名前空間。  
  
## <a name="the-sqluserdefinedaggregate-attribute"></a>SqlUserDefinedAggregate 属性  
 **SqlUserDefinedAggregate**属性は、メソッドが、ユーザー定義集計として登録することを示します。 すべてのユーザー定義集計にこのカスタム属性で注釈を付ける必要があります。  
  
 詳細については、[SqlUserDefinedAggregateAttribute](https://go.microsoft.com/fwlink/?LinkId=124626)を参照してください。  
  
## <a name="the-sqlfunction-attribute"></a>SqlFunction 属性  
 **SqlFunction**属性は、適切な関数属性セットを関数として登録する必要があります、メソッドを示します。  
  
 詳細については、[SqlFunctionAttribute](https://go.microsoft.com/fwlink/?LinkId=128019)を参照してください。  
  
## <a name="the-sqlfacet-attribute"></a>SqlFacet 属性  
 **SqlFacet**属性を使用して、ユーザー定義型 (UDT) の式の戻り値の型に関する情報を返します。  
  
 詳細については、[SqlFacetAttribute](https://go.microsoft.com/fwlink/?LinkId=128020)を参照してください。  
  
## <a name="the-sqlprocedure-attribute"></a>SqlProcedure 属性  
 **SqlProcedure**属性は、ストアド プロシージャとして登録する必要があります、メソッドを示します。 この属性は、Visual Studio だけで使用され、指定されたメソッドがストアド プロシージャとして自動的に登録されます。[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では使用されません。  
  
 詳細については、[SqlProcedureAttribute](https://go.microsoft.com/fwlink/?LinkId=128021)を参照してください。  
  
## <a name="the-sqltrigger-attribute"></a>SqlTrigger 属性  
 **SqlTrigger**属性は、トリガーとして登録する必要があります、メソッドを示します。  
  
 詳細については、[SqlTriggerContext](https://go.microsoft.com/fwlink/?LinkId=128022)と[SqlTriggerAttribute](https://go.microsoft.com/fwlink/?LinkId=203898)を参照してください。  
  
## <a name="the-sqluserdefinedtypeattribute"></a>SqlUserDefinedTypeAttribute  
 SqlUserDefinedTypeAttribute をアセンブリのクラス定義に適用できます。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、これにより、このカスタム属性を持つクラス定義にバインドされたユーザー定義型が作成されます。  
  
 詳細については、[SqlUserDefinedTypeAttribute](https://go.microsoft.com/fwlink/?LinkId=128024)を参照してください。  
  
## <a name="the-sqlmethod-attribute"></a>SqlMethod 属性  
 **SqlMethod**属性を使用して、UDT のプロパティまたはメソッドの決定論とデータ アクセス プロパティを指定します。  
  
 詳細については、[SqlMethodAttribute](https://go.microsoft.com/fwlink/?LinkId=128025)を参照してください。  
  
## <a name="see-also"></a>参照  
 [CLR ユーザー定義集計](../../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md)   
 [CLR ユーザー定義関数](../../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md)   
 [CLR ユーザー定義型](../../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)   
 [CLR ストアド プロシージャ](https://msdn.microsoft.com/library/bbdd51b2-a9b4-4916-ba6f-7957ac6c3f33)   
 [CLR トリガー](https://msdn.microsoft.com/library/302a4e4a-3172-42b6-9cc0-4a971ab49c1c)  
  
  
