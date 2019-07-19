---
title: Msmerge_conflict _&lt;パブリケーション&gt;_&lt;記事&gt;(TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_conflict_publication_article_TSQL
- MSmerge_conflict_publication_article
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_conflict_publication_article system table
ms.assetid: dc4490b4-02d8-4dfc-98f5-0cf8de8e11be
author: stevestein
ms.author: sstein
ms.openlocfilehash: dfae18a55ddb8b1c95aad25e27f006b28fde79af
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67895113"
---
# <a name="msmergeconflictltpublicationgtltarticlegt-transact-sql"></a>Msmerge_conflict _&lt;パブリケーション&gt;_&lt;記事&gt;(TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **Msmerge_conflict _*パブリケーション*_ * 記事*** テーブルには、競合がある行のデータ集約を実現するために元に戻された行変更に関する情報が含まれています。 競合テーブルの名前はパブリケーションとアーティクルの名前に付加されます、パブリケーションでレプリケートされた各テーブルに対して競合テーブルが存在します。 このアーティクル固有の競合テーブルは、競合ログで使用するデータベースに保存されます。通常、これはパブリケーション データベースですが、集中型でない競合ログの場合はサブスクリプション データベースの場合もあります。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|***article_column_name***|**variable**|レプリケートされたテーブルの列。 このシステム テーブルにはテーブル アーティクルの列ごとに 1 行のデータが格納されます。|  
|**rowguid**|**uniqueidentifier**|競合する行の行の識別子です。|  
|**ModifiedDate**|**datetime**|競合が発生した時刻。|  
|**origin_datasource_id**|**uniqueidentifier**|行変更が取り消された、または競合が失われたサブスクリプション。|  
  
## <a name="see-also"></a>関連項目  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
