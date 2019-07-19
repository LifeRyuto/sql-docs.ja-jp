---
title: sp_prepexec (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cursor_prepexec
- sp_cursor_prepexec_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_prepexec
ms.assetid: f9141850-a62b-43bf-8e46-b2f92b75ca56
author: stevestein
ms.author: sstein
ms.openlocfilehash: 163bbe741b09ffe9163b124c4223a845b8b8cd8f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68056362"
---
# <a name="spprepexec-transact-sql"></a>sp_prepexec (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  パラメーター化された実行を準備して[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメント。 sp_prepexec は、sp_prepare と sp_execute の機能を組み合わせたものです。 これは、ID によって呼び出される、表形式データ ストリーム (TDS) パケットで 13 を =。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_prepexec handle OUTPUT, params , stmt  
    [ , bound param ] [ ,...n]]  
```  
  
## <a name="arguments"></a>引数  
 *handle*  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-生成された*処理*識別子。 *処理*必須のパラメーターには、 **int**値を返します。  
  
 *params*  
 パラメーター化されたステートメントを指定します。 *Params*変数の定義は、ステートメント内のパラメーター マーカーの代わりに使用します。 *params*が必要なパラメーターです、 **ntext**、 **nchar**、または**nvarchar**値を入力します。 ステートメントがパラメーター化されていない場合は、NULL 値を入力します。  
  
 *stmt*  
 カーソル結果セットを定義します。 *Stmt*パラメーターは必須でありの呼び出し、 **ntext**、 **nchar**または**nvarchar**値を入力します。  
  
 *bound_param*  
 追加パラメーターをオプションで使用することを示します。 *bound_param*を使用する追加パラメーターを指定する任意のデータ型の入力値を呼び出します。  
  
## <a name="examples"></a>使用例  
 次の例では、準備して、単純なステートメントを実行します。  
  
```  
Declare @P1 int;  
EXEC sp_prepexec @P1 output,   
    N'@P1 nvarchar(128), @P2 nvarchar(100)',  
    N'SELECT database_id, name  
      FROM sys.databases  
      WHERE name=@P1 AND state_desc = @P2',   
@P1 = 'tempdb', @P2 = 'ONLINE';   
EXEC sp_unprepare @P1;  
```  
  
## <a name="see-also"></a>関連項目  
 [sp_prepare &#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/sp-prepare-transact-sql.md)   
 [sp_execute &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-execute-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
