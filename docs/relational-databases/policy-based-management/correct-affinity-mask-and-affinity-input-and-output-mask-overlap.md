---
title: affinity mask と affinity I/O mask の重複の修正 | Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 1a0da6df-57ff-4f3f-aae9-2fbc4897508c
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 96473ebbee3a0cd946c1ecbe3ebaae2b05ce4b3f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63007580"
---
# <a name="correct-affinity-mask-and-affinity-input-and-output-mask-overlap"></a>affinity mask と affinity I/O mask の重複の修正
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  このルールでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに、affinity mask オプションと affinity I/O mask オプションの両方が割り当てられたプロセッサが 1 つ以上あるかどうかを確認します。 複数のプロセッサが搭載されたコンピューターでは、affinity mask オプションと affinity I/O mask オプションを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で使用される CPU を指定します。 affinity mask と affinity I/O mask の両方で CPU を有効にすると、プロセッサが過剰に使用されるため、パフォーマンスが低下する可能性があります。  
  
## <a name="best-practices-recommendations"></a>ベスト プラクティスと推奨事項  
 affinity mask オプションと affinity I/O mask オプションのいずれかを指定している場合は、両方を指定する必要がありますが、有効にするのは一度に 1 つの CPU だけにしてください。  
  
 affinity mask オプションと affinity I/O mask オプションの両方で同じ CPU を有効にしないようにしてください。 各 CPU に対応するビットは、次のいずれかの状態に設定します。  
  
-   affinity mask オプションと affinity I/O mask オプションの両方で 0  
  
-   affinity mask オプションでは 0、affinity I/O mask オプションでは 1  
  
-   affinity mask オプションでは 1、affinity I/O mask オプションでは 0  
  
## <a name="for-more-information"></a>詳細情報  
 [affinity mask サーバー構成オプション](../../database-engine/configure-windows/affinity-mask-server-configuration-option.md)  
  
 [affinity Input-Output mask サーバー構成オプション](../../database-engine/configure-windows/affinity-input-output-mask-server-configuration-option.md)  
  
 [affinity64 mask サーバー構成オプション](../../database-engine/configure-windows/affinity64-mask-server-configuration-option.md)  
  
 [affinity64 Input-Output mask サーバー構成オプション](../../database-engine/configure-windows/affinity64-input-output-mask-server-configuration-option.md)  
  
## <a name="see-also"></a>参照  
 [ポリシー ベースの管理を使用したベスト プラクティスの監視と実行](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
