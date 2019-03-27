---
title: sp_add_operator (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_operator
- sp_add_operator_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_operator
ms.assetid: 817cd98a-4dff-4ed8-a546-f336c144d1e0
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c1a6a9e45b1640a82cd15074373f162a97d9a0a6
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58494082"
---
# <a name="spaddoperator-transact-sql"></a>sp_add_operator (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  警告とジョブで使用するためには、オペレーター (通知受信者) を作成します。  
  
 
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_add_operator [ @name = ] 'name'   
     [ , [ @enabled = ] enabled ]   
     [ , [ @email_address = ] 'email_address' ]   
     [ , [ @pager_address = ] 'pager_address' ]   
     [ , [ @weekday_pager_start_time = ] weekday_pager_start_time ]   
     [ , [ @weekday_pager_end_time = ] weekday_pager_end_time ]   
     [ , [ @saturday_pager_start_time = ] saturday_pager_start_time ]   
     [ , [ @saturday_pager_end_time = ] saturday_pager_end_time ]   
     [ , [ @sunday_pager_start_time = ] sunday_pager_start_time ]   
     [ , [ @sunday_pager_end_time = ] sunday_pager_end_time ]   
     [ , [ @pager_days = ] pager_days ]   
     [ , [ @netsend_address = ] 'netsend_address' ]   
     [ , [ @category_name = ] 'category' ]   
```  
  
## <a name="arguments"></a>引数  
`[ @name = ] 'name'` オペレーター (通知受信者) の名前。 この名前は一意であり、% を含めることはできません (**%**) 文字。 *名前*は**sysname**、既定値はありません。  
  
`[ @enabled = ] enabled` オペレーターの現在の状態を示します。 *有効になっている*は**tinyint**、既定値は**1** (有効)。 場合**0**オペレーターが有効でないと、通知を受信しません。  
  
`[ @email_address = ] 'email_address'` オペレーターの電子メール アドレス。 この文字列はメール システムに直接渡されます。 *email_address*は**nvarchar (100)**、既定値は NULL です。  
  
 実際の電子メール アドレスまたはエイリアスのいずれかを指定する*email_address*します。 例 :  
  
 '**jdoe**'または'**jdoe@xyz.com**'  
  
> [!NOTE]  
>  データベース メールには電子メール アドレスを使用する必要があります。  
  
`[ @pager_address = ] 'pager_address'` オペレーターのポケットベル アドレス。 この文字列はメール システムに直接渡されます。 *pager_address*は**narchar (100)**、既定値は NULL です。  
  
`[ @weekday_pager_start_time = ] weekday_pager_start_time` 時刻を[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェント ポケットベルの通知送信指定したオペレーター、平日、月曜日から金曜日までからです。 *weekday_pager_start_time*は**int**、既定値は**090000**9時 00分 am を 24 時間形式で表したものです。HHMMSS 形式で入力する必要があります。  
  
`[ @weekday_pager_end_time = ] weekday_pager_end_time` 時刻を**SQLServerAgent**サービス不要になったポケットベルの通知送信指定したオペレーター平日に、月曜日から金曜日までからです。 *エージェント*は**int**で表した 180000、既定値を示す 6時 00分 PM を 24 時間形式で表したものです。HHMMSS 形式で入力する必要があります。  
  
`[ @saturday_pager_start_time = ] saturday_pager_start_time` 時刻を**SQLServerAgent**サービスは、毎週土曜日に、指定したオペレーターにポケットベルの通知を送信します。 *エージェント*は**int**で表した 090000、既定値を示す午前 9時 00分 を 24 時間形式で表したものです。HHMMSS 形式で入力する必要があります。  
  
`[ @saturday_pager_end_time = ] saturday_pager_end_time` 時刻を**SQLServerAgent**サービス不要になったポケットベルの通知送信指定したオペレーターに対して毎週土曜日。 *@saturday_pager_end_time*は**int**、既定値は**180000**午後 6 時を示します を 24 時間形式で表したものです。HHMMSS 形式で入力する必要があります。  
  
`[ @sunday_pager_start_time = ] sunday_pager_start_time` 時刻を**SQLServerAgent**サービスが指定したオペレーターに対して毎週日曜日ポケットベルの通知を送信します。 *エージェント*は**int**、既定値は**090000**9時 00分 am を 24 時間形式で表したものです。HHMMSS 形式で入力する必要があります。  
  
`[ @sunday_pager_end_time = ] sunday_pager_end_time` 時刻を**SQLServerAgent**サービス不要になったポケットベルの通知送信指定したオペレーターに対して毎週日曜日。 *エージェント*は**int**、既定値は**180000**午後 6 時を示します を 24 時間形式で表したものです。HHMMSS 形式で入力する必要があります。  
  
`[ @pager_days = ] pager_days` オペレーターがポケットベルの指定した開始/終了時間) する日を示す数です。 *pager_days*は**tinyint**、既定値は**0**ページの受信に使用可能なことはありませんが、演算子をことを示します。 有効な値は**0**を通じて**127**します。 *pager_days*必要となる曜日の個々 の値を加算して計算されます。 たとえば、月曜日から金曜日までからは**2**+**4**+**8**+**16** + **32** = **62**します。 次の表は、各曜日の値を示します。  
  
|値|説明|  
|-----------|-----------------|  
|**1**|日曜日|  
|**2**|月曜日|  
|**4**|火曜日|  
|**8**|水曜日|  
|**16**|木曜日|  
|**32**|金曜日|  
|**64**|土曜日|  
  
`[ @netsend_address = ] 'netsend_address'` ネットワーク メッセージを送信するオペレーターのネットワーク アドレス。 *netsend_address*は**nvarchar (100)**、既定値は NULL です。  
  
`[ @category_name = ] 'category'` この演算子のカテゴリの名前。 *カテゴリ*は**sysname**、既定値は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>コメント  
 **sp_add_operator**から実行する必要があります、 **msdb**データベース。  
  
 通知は、ページングを使用する場合は、電子メール、電子メール、ポケットベルを持つ必要がある電子メール システムでサポートされます。  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] は、ジョブを簡単に管理できるグラフィカルなツールです。ジョブのインフラストラクチャを作成し、管理するには、このツールを使用することをお勧めします。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールが実行できる**sp_add_operator**します。  
  
## <a name="examples"></a>使用例  
 次の例では、`danwi` に対してオペレーター情報を設定します。 オペレーターは有効になっています。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントは、月曜日から金曜日の午前 8 時から午後 5 時まで、 ポケットベルによる通知を送信します。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_operator  
    @name = N'Dan Wilson',  
    @enabled = 1,  
    @email_address = N'danwi',  
    @pager_address = N'5551290AW@pager.Adventure-Works.com',  
    @weekday_pager_start_time = 080000,  
    @weekday_pager_end_time = 170000,  
    @pager_days = 62 ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sp_delete_operator &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-operator-transact-sql.md)   
 [sp_help_operator &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-operator-transact-sql.md)   
 [sp_update_operator &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-operator-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
