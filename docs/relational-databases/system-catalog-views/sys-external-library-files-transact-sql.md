---
title: external_library_files (トランザクション-SQL) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 07/24/2019
ms.prod: sql
ms.technology: machine-learning
ms.topic: language-reference
f1_keywords:
- external_library_files
- external_library_files_TSQL
- sys.external_library_files
- sys.external_library_files_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.external_library_files catalog view
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b2f1bbdc3936dc6295b9ecc51b937e50cae20670
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/04/2020
ms.locfileid: "80664227"
---
# <a name="sysexternal_library_files-transact-sql"></a>sys.external_library_files (Transact-SQL)  
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

外部ライブラリを構成する各ファイルの行を一覧表示します。

|列名 |データ型 |説明|
|------|------|-----|
|external_library_id | INT |外部ライブラリ オブジェクトの ID。 |
|content |varbinary(max) |外部ライブラリ ファイルの成果物の内容。 |
|platform |tinyint |SQL Server がインストールされているホスト プラットフォームの ID。 |
|platform_desc | nvarchar(60) |ホスト プラットフォームの名前。 有効な値は「ウィンドウ」、'LINUX'です。 |

### <a name="see-also"></a>関連項目  

[sys.external_libraries](sys-external-libraries-transact-sql.md)  
[外部ライブラリの作成](../../t-sql/statements/create-external-library-transact-sql.md)  

