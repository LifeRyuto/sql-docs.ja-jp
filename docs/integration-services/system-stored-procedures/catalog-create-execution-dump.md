---
title: catalog.create_execution_dump | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 91319b0b-5536-4ab4-a403-9559ed9dd177
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 52641812a754ccc5aa810fe63fdb8dd3a1b6c031
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/20/2019
ms.locfileid: "58290338"
---
# <a name="catalogcreateexecutiondump"></a>catalog.create_execution_dump
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  実行中のパッケージを一時停止させ、ダンプ ファイルを作成します。 ファイルは *\<ドライブ>*:\Program Files\Microsoft SQL Server\130\Shared\ErrorDumps フォルダーに格納されます。  
  
## <a name="syntax"></a>構文  
  
```sql  
catalog.create_execution_dump [ @execution_id = ] execution_id  
  
```  
  
## <a name="arguments"></a>引数  
 [ @execution_id = ] *execution_id*  
 実行中のパッケージの実行 ID です。 *execution_id* は **bigint** です。  
  
## <a name="example"></a>例  
 次の例では、実行 ID が 88 の実行中のパッケージにダンプ ファイルの作成を指示しています。  
  
```sql
EXEC create_execution_dump @execution_id = 88  
```  
  
## <a name="return-codes"></a>リターン コード  
 成功した場合は 0 を返します。  
  
 ストアド プロシージャが失敗した場合は、エラーをスローします。  
  
## <a name="result-set"></a>結果セット  
 なし  
  
## <a name="permissions"></a>アクセス許可  
 このストアド プロシージャでは、ユーザーが**ssis_admin** データベース ロールのメンバーである必要があります。  
  
## <a name="errors-and-warnings"></a>エラーおよび警告  
 ストアド プロシージャが失敗する原因となる条件を以下に示します。  
  
-   無効な実行 ID が指定されている。  
  
-   パッケージが既に完了済みである。  
  
-   パッケージが現在、ダンプ ファイルを作成中である。  
  
## <a name="see-also"></a>参照  
 [パッケージ実行用のダンプ ファイルを生成する](../../integration-services/troubleshooting/generating-dump-files-for-package-execution.md)  
  
  
