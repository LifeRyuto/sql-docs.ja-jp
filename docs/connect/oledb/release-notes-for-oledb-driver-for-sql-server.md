---
title: リリース ノート (OLE DB Driver for SQL Server) | Microsoft Docs
ms.date: 05/13/2019
ms.prod: sql
ms.technology: connectivity
ms.topic: conceptual
ms.reviewer: genemi
author: mateusz-kmiecik
ms.author: v-makmie
ms.openlocfilehash: 969caa46506c9fd19410c5ace753076b3ba02fbe
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "65619985"
---
# <a name="release-notes-for-the-microsoft-ole-db-driver-for-sql-server"></a>Microsoft OLE DB Driver for SQL Server のリリース ノート

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../includes/driver_oledb_download.md)]

このページでは、Microsoft OLE DB Driver for SQL Server の各バージョンで追加された内容について説明します。

<!--
USE THE TABLE FORMAT!
Hello, from now on, please use the table-based format standard for all new Release Notes content.
See section "## 18.2.1" for a live example in this article.
Thank you. For questions, contact GeneMi. (2019/03/16)
-->

## <a name="1822"></a>18.2.2

2019 年 5 月

### <a name="bugs-fixed"></a>修正されたバグ

| 修正されたバグ | 詳細 |
| :-------- | :------ |
| マルチスレッド アパートメント (MTA) で対話しない Azure Active Directory 認証を修正しました。 | マルチスレッド (MTA) として以前に初期化されたアパートメントで OLE DB Driver 18.2.1 が COM 同時実行モデルを誤って変更しようとします。 その結果、[IDBInitialize::Initialize](https://go.microsoft.com/fwlink/?linkid=2092522) インターフェイスを呼び出す前に 2 回以上 [CoInitialize](https://go.microsoft.com/fwlink/?linkid=2092520) または [CoInitializeEx](https://go.microsoft.com/fwlink/?linkid=2092521) に呼び出しを行うアプリケーションで、いずれかの Azure Active Directory 認証モードを使用するとドライバーが接続に失敗します。 |
| &nbsp; | &nbsp; |

## <a name="1821"></a>18.2.1

2019 年 2 月

### <a name="features-added"></a>追加された機能

| 追加された機能 | 詳細 |
| :------------ | :------ |
| UTF-8 サーバー エンコードのサポート。 | &bull; &nbsp; [OLE DB Driver for SQL Server の UTF-8 のサポート](features/utf-8-support-in-oledb-driver-for-sql-server.md)。 |
| Azure Active Directory 認証のサポート。 | &bull; &nbsp; [Azure Active Directory の使用](features/using-azure-active-directory.md)。 |
| &nbsp; | &nbsp; |

## <a name="1810"></a>18.1.0

2018 年 7 月

### <a name="features-added"></a>追加された機能

| 追加された機能 | 詳細 |
| :------------ | :------ |
| `UseFMTONLY` 接続文字列キーワードと `SSPROP_INIT_USEFMTONLY` 初期化プロパティのサポート。 | `UseFMTONLY` は [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 以上に接続する場合のメタデータの取得方法を制御します。<br/><br/>&bull; &nbsp; [OLE DB Driver for SQL Server での接続文字列キーワードの使用](applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md)。 |
| &nbsp; | &nbsp; |

### <a name="bugs-fixed"></a>修正されたバグ

| 修正されたバグ | 詳細 |
| :-------- | :------ |
| BCP フォーマット ファイルのバージョンの誤りを修正しました。 | OLE DB Driver 18.0 では BCP フォーマット ファイルのバージョンが 11.0 ではなく 18.0 と誤って設定されています。<br/><br/>OLE DB Driver 18.0 で生成されたフォーマット ファイルは OLE DB Driver 18.1 で読み取ることができません。<br/><br/>以前のバージョンのドライバーで生成されたフォーマット ファイルを新しいドライバーで使用する必要がある場合、ファイルを手動で編集してバージョンを 11.0 に変更することができます。 |
| &nbsp; | &nbsp; |

## <a name="1802"></a>18.0.2

### <a name="features-added"></a>追加された機能

| 追加された機能 | 詳細 |
| :------------ | :------ |
| `MultiSubnetFailover` 接続文字列キーワードと `SSPROP_INIT_MULTISUBNETFAILOVER` 初期化プロパティのサポート。 | &bull; &nbsp; [OLE DB Driver for SQL Server の高可用性、ディザスター リカバリーに関するサポート](features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)。<br/><br/>&bull; &nbsp; [OLE DB Driver for SQL Server での接続文字列キーワードの使用](applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md)。 |
| &nbsp; | &nbsp; |

## <a name="see-also"></a>参照

[Microsoft OLE DB Driver for SQL Server](oledb-driver-for-sql-server.md)
