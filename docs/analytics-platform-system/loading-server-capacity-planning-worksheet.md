---
title: サーバーの容量計画を読み込んでいます
description: この容量計画ワークシートは、Analytics Platform System Parallel Data Warehouse にデータを読み込むための読み込みサーバーの要件を決定するのに役立ちます。 "
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 7dded8c79495d0bdc684927f4875a93c3160c1bf
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "74401030"
---
# <a name="loading-server-capacity-planning-worksheet-for-analytics-platform-system"></a>分析プラットフォームシステムのサーバー容量計画ワークシートを読み込んでいます
この容量計画ワークシートは、SQL Server PDW にデータを読み込むための読み込みサーバーの要件を決定するのに役立ちます。 既存の読み込みサーバーを購入またはプロビジョニングするためのプランを作成するには、これを使用します。  
  
## <a name="worksheet-notes"></a>ワークシートのメモ
  
1.  このワークシートは、 **dwloader**コマンドライン読み込みツールを使用してデータを読み込むサーバーに適用されます。  
  
2.  Integration Services またはサードパーティ製の読み込みツールを使用してデータを読み込む場合、読み込みプロセスの違いによって要件が異なることがあります。  
  
3.  ほとんどの要件は、圧縮データファイルまたは圧縮されていないデータファイルの読み込みに適用されます。要件の違いについては、太字で示されています。  
  
## <a name="clipboardmediaclipboard-iconpng-clipboard-capacity-planning-worksheet"></a>![クリップボード](media/clipboard-icon.png "クリップボード")容量計画ワークシート  
  
このワークシートを印刷し、独自の要件を入力します。  
  
|コンポーネント|要件|この列に独自の要件を入力してください|Recommendations|  
|-------------|---------------|--------------------------------------------------|-------------------|  
|ストレージ|指定した時間内に、読み込み中のサーバーに格納する最大バイト数。|![鉛筆アイコン](media/pencil-icon.png "鉛筆アイコン")|ストレージの要件を決定するには、特定の期間に、読み込み中のサーバーに格納するデータ量を算出します。  容量の要件は、ファイルの読み込みのみを対象としています。オペレーティングシステムと読み込みファイルは、異なるディスクアレイに配置する必要があります。<br /><br />たとえば、1日に3回、ディスクから 100 GB のデータをロードする予定であるのに、週の終わりまでデータファイルを削除しない場合は、データファイルを格納するために最低 2.1 TB が必要になります。 差異と成長を考慮するために、控えめにして30% のストレージを使用することをお勧めします。  この例では、2.73 TB のストレージ領域が適しています。|  
|読み込み率|PDW に読み込むデータの1時間あたりの最大バイト数。|![鉛筆アイコン](media/pencil-icon.png "鉛筆アイコン")|これは推定値です。 この要件を計算するときは、ファイルが既に読み込まれているサーバー上にあり、その他の読み込み条件ができるだけ良好であることを前提としています。<br /><br />例: dwloader は常に非圧縮データを PDW に送信するため、データ圧縮率を考慮する必要はありません。 データ型変換と変換先テーブルのサイズを考慮する必要はありません。|  
|ネットワーク|ネットワーク接続の種類。|![鉛筆アイコン](media/pencil-icon.png "鉛筆アイコン")|負荷率の要件に最適なネットワーク接続の種類を決定します。<br /><br />たとえば、InfiniBand または10ギガビットイーサネットは、最適な読み込みレートを提供します。 1ギガビットイーサネットでは、負荷率が1時間あたり 360 GB に制限されます。|  
|I/O|読み取りと書き込みの1時間あたりのバイト数。|![鉛筆アイコン](media/pencil-icon.png "鉛筆アイコン")|データを読み込むには、dwloader は、PDW に送信する前に、ディスクからすべてのデータを読み取る必要があります。<br /><br />各読み込み元のサーバーは、アプライアンスがすべての読み込み元からデータを受信できるよりも速くデータを読み込むことができません。 コストを節約するには、読み込み用の i/o 読み取り容量を、アプライアンスの負荷容量を超えないように計画します。<br /><br />次に例を示します。<br />PDW は、1時間あたり 1.8 TB の最大レートで1ラックのアプライアンスにデータを受信して読み込みます。 ラックが2台以上のアプライアンスの場合、最大負荷率は1時間あたり 3.6 TB です。<br /><br />複数の読み込みサーバーからの読み込みを同時に行う場合、各読み込みサーバーの i/o 要件は、1台のサーバーがすべての読み込みを実行しているときよりも少なくなります。<br /><br />たとえば、1台のラックのアプライアンスで1つの読み込みサーバーで1時間あたり最大 1.8 TB を読み込むことができます。 2つの読み込みサーバーは、1時間あたり 900 GB を1ラックのアプライアンスに同時に読み込むことができます。 高いレベルの同時実行性により、効率と最大スループットが低下する可能性があります。<br /><br />I/o 容量については、読み込み中のサーバーで発生したすべての i/o を考慮してください。 ETL サーバーからのデータファイルの受信など、読み込みサーバーにデータの読み込みに加えて他の i/o トラフィックがある場合は、i/o の要件が増加します。<br /><br />圧縮データの場合、i/o の要件はデータ圧縮率によって異なります。 dwloader は、圧縮されたデータを読み取り、それを PDW に送信する前に圧縮解除します。 圧縮率が高いほど、読み込みサーバーがディスクから読み取る必要があるデータの量が少なくなります。<br /><br />たとえば、必要な負荷率が1時間あたり 1.8 TB で、データが2:1 圧縮を使用して読み込み中のサーバーに格納されている場合、読み込みサーバーは、1.8 TB ではなく、ディスクから1時間あたり 900 GB を読み取る必要があります。 圧縮率3:1 は、読み込みサーバーがディスクから1時間あたり 600 GB を読み取る必要があることを意味します。|  
|CPU|ソケットの数。|![鉛筆アイコン](media/pencil-icon.png "鉛筆アイコン")|非圧縮データを読み込む場合、dwloader は CPU を集中的に使用するアプリケーションではありません。  最小要件として、最近製造された2ソケットサーバーを使用することをお勧めします。<br /><br />圧縮データを読み込むには、PDW に送信する前にデータを圧縮解除するのに十分な CPU 電源が必要です。 dwloader では、10個のアクティブスレッドを一度に実行できます。 圧縮された10個のファイルを同時に読み込む場合は、少なくとも10コアの CPU または2つの6コア cpu がサーバーにあることをお勧めします。|  
|RAM|読み込み中に Windows がファイルをキャッシュできるようにするメモリ容量 (GB)。|![鉛筆アイコン](media/pencil-icon.png "鉛筆アイコン")|dwloader では、読み込みサーバーで RAM がほとんど使用されません。 パフォーマンスを向上させるために、Windows はメモリを使用して、読み込みファイルをディスクから読み取った後にキャッシュします。<br /><br />RAM の要件を確認するには、Windows Server のインストールとサードパーティ製のアプリケーションの要件を参照してください。 他のソースからの要件がない場合は、少なくとも 32 GB をお勧めします。<br /><br />圧縮されたデータの場合は、圧縮解除を高速化するため、より高速な RAM が役立ちます。|  
  
## <a name="see-also"></a>参照  
[読み込みサーバーの取得と構成](acquire-and-configure-loading-server.md)  
[dwloader コマンドラインローダー](dwloader.md)  
  
