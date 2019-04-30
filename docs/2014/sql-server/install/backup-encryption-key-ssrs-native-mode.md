---
title: バックアップの暗号化キー (SSRS ネイティブ モード) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.backupencryptionkey.F1
ms.assetid: eb8c82be-323b-4d86-ab10-c1bf69a4abe3
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: db573e1a070b110ff0f5224a6d079f3fe7c377ca
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63214951"
---
# <a name="backup-encryption-key-ssrs-native-mode"></a>暗号化キーをバックアップする (SSRS ネイティブ モード)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] では、暗号化キーを使用して、レポート サーバー データベースに格納されている機密データのセキュリティを保護します。 このキーのバックアップを取ることは、暗号化された接続文字列と資格情報に継続してアクセスできるようにするうえで不可欠です。 レポート サーバー データベースを別のコンピューターに移動する場合や、レポート サーバー サービス アカウントのユーザー名またはパスワードを変更する場合は、このキーのバックアップ コピーを取る必要があります。 どちらの操作でも、前もって作成したバックアップ コピーからキーを復元する必要があります。  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ネイティブ モード。  
  
 [暗号化キーのバックアップ] ダイアログ ボックスを開くには、 **構成マネージャーのナビゲーション ウィンドウで** [暗号化キー] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] をクリックし、 **[バックアップ]** をクリックします。 このダイアログ ボックスは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーの [サービス アカウント] ページを使用してサービス アカウントを更新した場合にも表示されます。 詳細については、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager を参照してください[Reporting Services 構成マネージャー&#40;ネイティブ モード&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)します。  
  
## <a name="options"></a>および  
 **ファイルの場所**  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] に対して対称キーのファイル名と場所を指定します。 対称キーはプレーン テキストのまま保存しないでください。 パスワードを入力してファイルを保護する必要があります。  
  
 **Password**  
 ファイルを不正アクセスから保護するパスワードを入力します。 パスワードを知っているユーザーのみが、ファイル内にロックされているキーを復元できます。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] では、強力なパスワード ポリシーが適用されます。 パスワードは 8 文字以上で、大文字と小文字、英数字、および 1 つ以上の記号文字の組み合わせにする必要があります。  
  
 **[パスワードの確認入力]**  
 入力したパスワードを再入力します。  
  
## <a name="see-also"></a>参照  
 [Reporting Services 構成マネージャーの F1 ヘルプ トピック&#40;SSRS ネイティブ モード&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [Reporting Services の暗号化キーのバックアップと復元](../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md)   
 [暗号化キーの削除と再作成  &#40;SSRS 構成マネージャー&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-delete-and-re-create-encryption-keys.md)   
 [レポート サーバーの初期化 &#40;SSRS 構成マネージャー&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server.md)   
 [暗号化されたレポート サーバー データの格納 &#40;SSRS 構成マネージャー&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md)   
 [暗号化キー &#40;SSRS ネイティブ モード&#41;](../../../2014/sql-server/install/encryption-keys-ssrs-native-mode.md)  
  
  
