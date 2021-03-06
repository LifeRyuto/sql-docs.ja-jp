---
title: MSSQLSERVER_701 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 701 (Database Engine error)
ms.assetid: 3b975000-63a1-43c2-a40f-89d0a8a36bef
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c52c1d38e115e4064e106175bb49d0a3ecb4318d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62913782"
---
# <a name="mssqlserver_701"></a>MSSQLSERVER_701
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|701|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|NOSYSMEM|  
|メッセージ テキスト|システム メモリが不足しているため、このクエリを実行できません。|  
  
## <a name="explanation"></a>説明  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、クエリを実行するために必要なメモリを割り当てることができませんでした。 この原因としては、オペレーティング システムの設定、物理メモリの可用性、現在のワークロードのメモリ制限など、さまざまなことが考えられます。 ほとんどの場合、トランザクションが失敗しても、このエラーは発生しません。  
  
 サーバーに十分なメモリがないので、DBCC ステートメントなどの診断クエリは失敗する可能性があります。  
  
 リソース プール 'default' でクエリ実行のためのメモリ リソースを待機中にタイムアウトが発生しました。  
  
## <a name="user-action"></a>ユーザーの操作  
 リソース ガバナーを使用していない場合は、サーバーの全体的な状態と読み込みを検証するか、リソース プールまたはワークロード グループの設定を確認することをお勧めします。  
  
 メモリ エラーのトラブルシューティングに役立つ一般的な手順の概略を次に示します。  
  
1.  このサーバー上で、他のアプリケーションやサービスによってメモリが消費されていないか確認します。 重要度の低いアプリケーションやサービスのメモリ消費量が少なくなるように、構成を変更します。  
  
2.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **: Buffer Manager** および **SQL Server: Memory Manager** のパフォーマンス モニター カウンターを確認します。  
  
3.  次に示す SQL Server メモリ構成パラメーターを確認します。  
  
    -   **max server memory**  
  
    -   **min server memory**  
  
    -   **min memory per query**  
  
     通常とは異なる設定がないか確認します。 必要に応じて、これらを修正します。 高くなったメモリ要件を把握しておきます。 既定の設定については、SQL Server オンライン ブックの「サーバー構成オプションの設定」を参照してください。  
  
4.  DBCC MEMORYSTATUS 出力を監視し、エラー メッセージが表示された場合にどのように変化するかを調べます。  
  
5.  ワークロード (同時セッション数や現在実行中のクエリ数など) をチェックします。  
  
 次のアクションを実行すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で使用できるメモリを増やせる可能性があります。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外のアプリケーションがリソースを消費している場合は、そのアプリケーションの実行を停止するか、別のサーバーで実行することを検討します。 これにより、外部的なメモリ負荷を軽減できます。  
  
-   **max server memory** を構成した場合は、設定値を大きくします。  
  
 次の DBCC コマンドを実行して、いくつかの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] メモリ キャッシュを解放します。  
  
-   DBCC FREESYSTEMCACHE  
  
-   DBCC FREESESSIONCACHE  
  
-   DBCC FREEPROCCACHE  
  
 問題が解決しない場合は、さらに調査します。ワークロードの軽減が必要になる場合もあります。  
  
  
