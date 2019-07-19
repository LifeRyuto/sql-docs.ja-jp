---
title: 開発用データベース、テスト用データベース、および実行時用データベース | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- production databases [SQL Server]
- testing databases
- database testing [SQL Server]
ms.assetid: cb403330-8cbe-41c6-bd23-bc432d50f173
author: markingmyname
ms.author: maghan
manager: jroth
ms.openlocfilehash: 6f39595c1d01dcadf39c981f17b4b7d0a7f42754
ms.sourcegitcommit: 5d839dc63a5abb65508dc498d0a95027d530afb6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2019
ms.locfileid: "67690350"
---
# <a name="development-test-and-production-databases-visual-database-tools"></a>開発用データベース、テスト用データベース、および実行時用データベース (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
まったく同じ構成のデータベースが 2 つある場合は、一方のデータベースで変更を行い、その変更をもう一方のデータベースに反映させることができます。 たとえば、個人で使用する開発用データベースとグループ全体で使用するテスト用データベースがある場合は、開発用データベースを変更してから、その変更をテスト用データベースに反映させます。  
  
これを実現するには、すべての変更を開発用データベースでの単一のセッション内で実行し、セッションの変更スクリプトを作成して、そのスクリプトを後からテスト用データベースで実行します。  
  
## <a name="see-also"></a>参照  
[マルチユーザー環境 (Visual Database Tools)](../../ssms/visual-db-tools/multiuser-environments-visual-database-tools.md)  
  
