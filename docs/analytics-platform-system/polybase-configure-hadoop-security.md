---
title: Analytics Platform System での PolyBase での Hadoop セキュリティの構成 |Microsoft Docs
description: 外部の Hadoop に接続するための Parallel Data Warehouse で PolyBase を構成する方法について説明します。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 10/26/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: c916fef2b70333c2d5bc89fec5c86d61482cdba7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62678610"
---
# <a name="polybase-configuration-and-security-for-hadoop"></a>PolyBase の構成と Hadoop 用のセキュリティ

この記事から Hadoop への AP PolyBase 接続性に影響するさまざまな構成設定の参照を提供します。 チュートリアルについては、PolyBase は、次を参照してください。 [PolyBase は](configure-polybase-connectivity-to-external-data.md)します。

> [!NOTE]
> AP のすべてのコンピューティング ノードと制御ノードでの XML ファイルに変更が必要です。
> 
> APS の XML ファイルを変更するときに特別な注意してください。 不足しているタグまたは望ましくない文字が含までは、機能の usablilty が妨げられている xml ファイルが無効にできます。
> Hadoop 構成ファイルは、次のパスに配置されます。  
> ```  
> C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\Hadoop\conf 
> ``` 
> Xml ファイルを変更するには、サービスの再起動を有効にする必要があります。

## <a id="rpcprotection"></a> Hadoop.RPC.Protection 設定

Hadoop クラスターで通信を保護する一般的な方法は、hadoop.rpc.protection 構成を "Privacy" または "Integrity" に変更することです。 既定では、PolyBase は構成が "Authenticate" に設定されているものと想定します。 この既定値をオーバーライドするには、次のプロパティを core-site.xml ファイルに追加します。 この構成を変更すると、Hadoop ノード間の安全なデータ転送と、SQL Server への SSL 接続が有効になります。

```xml
<!-- RPC Encryption information, PLEASE FILL THESE IN ACCORDING TO HADOOP CLUSTER CONFIG -->
   <property>
     <name>hadoop.rpc.protection</name>
     <value></value>
   </property> 
```

## <a name="example-xml-files-for-cdh-5x-cluster"></a>CDH 5.X クラスター用のサンプル XML ファイル

yarn.application.classpath と mapreduce.application.classpath で構成される Yarn-site.xml。

```xml
<?xml version="1.0" encoding="utf-8"?>
<?xml-stylesheet type="text/xsl" href="configuration.xsl"?>
<!-- Put site-specific property overrides in this file. -->
 <configuration>
   <property>
      <name>yarn.resourcemanager.connect.max-wait.ms</name>
      <value>40000</value>
   </property>
   <property>
      <name>yarn.resourcemanager.connect.retry-interval.ms</name>
      <value>30000</value>
   </property>
<!-- Applications' Configuration-->
   <property>
     <description>CLASSPATH for YARN applications. A comma-separated list of CLASSPATH entries</description>
      <!-- Please set this value to the correct yarn.application.classpath that matches your server side configuration -->
      <!-- For example: $HADOOP_CONF_DIR,$HADOOP_COMMON_HOME/share/hadoop/common/*,$HADOOP_COMMON_HOME/share/hadoop/common/lib/*,$HADOOP_HDFS_HOME/share/hadoop/hdfs/*,$HADOOP_HDFS_HOME/share/hadoop/hdfs/lib/*,$HADOOP_YARN_HOME/share/hadoop/yarn/*,$HADOOP_YARN_HOME/share/hadoop/yarn/lib/* -->
      <name>yarn.application.classpath</name>
      <value>$HADOOP_CLIENT_CONF_DIR,$HADOOP_CONF_DIR,$HADOOP_COMMON_HOME/*,$HADOOP_COMMON_HOME/lib/*,$HADOOP_HDFS_HOME/*,$HADOOP_HDFS_HOME/lib/*,$HADOOP_YARN_HOME/*,$HADOOP_YARN_HOME/lib/,$HADOOP_MAPRED_HOME/*,$HADOOP_MAPRED_HOME/lib/*,$MR2_CLASSPATH*</value>
   </property>

<!-- kerberos security information, PLEASE FILL THESE IN ACCORDING TO HADOOP CLUSTER CONFIG
   <property>
      <name>yarn.resourcemanager.principal</name>
      <value></value>
   </property>
-->
</configuration>
```

2 つの構成設定を mapred-site.xml と yarn-site.xml に分割する場合は、ファイルは次のようになります

**yarn-site.xml**

```xml
<?xml version="1.0" encoding="utf-8"?>
<?xml-stylesheet type="text/xsl" href="configuration.xsl"?>
<!-- Put site-specific property overrides in this file. -->
 <configuration>
   <property>
      <name>yarn.resourcemanager.connect.max-wait.ms</name>
      <value>40000</value>
   </property>
   <property>
      <name>yarn.resourcemanager.connect.retry-interval.ms</name>
      <value>30000</value>
   </property>
<!-- Applications' Configuration-->
   <property>
     <description>CLASSPATH for YARN applications. A comma-separated list of CLASSPATH entries</description>
      <!-- Please set this value to the correct yarn.application.classpath that matches your server side configuration -->
      <!-- For example: $HADOOP_CONF_DIR,$HADOOP_COMMON_HOME/share/hadoop/common/*,$HADOOP_COMMON_HOME/share/hadoop/common/lib/*,$HADOOP_HDFS_HOME/share/hadoop/hdfs/*,$HADOOP_HDFS_HOME/share/hadoop/hdfs/lib/*,$HADOOP_YARN_HOME/share/hadoop/yarn/*,$HADOOP_YARN_HOME/share/hadoop/yarn/lib/* -->
      <name>yarn.application.classpath</name>
      <value>$HADOOP_CLIENT_CONF_DIR,$HADOOP_CONF_DIR,$HADOOP_COMMON_HOME/*,$HADOOP_COMMON_HOME/lib/*,$HADOOP_HDFS_HOME/*,$HADOOP_HDFS_HOME/lib/*,$HADOOP_YARN_HOME/*,$HADOOP_YARN_HOME/lib/*</value>
   </property>

<!-- kerberos security information, PLEASE FILL THESE IN ACCORDING TO HADOOP CLUSTER CONFIG
   <property>
      <name>yarn.resourcemanager.principal</name>
      <value></value>
   </property>
-->
</configuration>
```

**mapred-site.xml**

プロパティ mapreduce.application.classpath が追加されています。 CDH 5.x では、Ambari で同じ名前付け規則の構成値が検索されます。

```xml
<?xml version="1.0"?>
<?xml-stylesheet type="text/xsl" href="configuration.xsl"?>
<!-- Put site-specific property overrides in this file. -->
<configuration xmlns:xi="http://www.w3.org/2001/XInclude">
   <property>
     <name>mapred.min.split.size</name>
       <value>1073741824</value>
   </property>
   <property>
     <name>mapreduce.app-submission.cross-platform</name>
     <value>true</value>
   </property>
<property>
     <name>mapreduce.application.classpath</name>
     <value>$HADOOP_MAPRED_HOME/*,$HADOOP_MAPRED_HOME/lib/*,$MR2_CLASSPATH</value>
   </property>


<!--kerberos security information, PLEASE FILL THESE IN ACCORDING TO HADOOP CLUSTER CONFIG
   <property>
     <name>mapreduce.jobhistory.principal</name>
     <value></value>
   </property>
   <property>
     <name>mapreduce.jobhistory.address</name>
     <value></value>
   </property>
-->
</configuration>
```

## <a name="kerberos-configuration"></a>Kerberos の構成  

PolyBase が Kerberos でセキュリティが強化されているクラスターに対して認証を行う場合、hadoop.rpc.protection が既定で "Authenticate" に設定されている必要があることに注意してください。 これにより、Hadoop ノード間のデータ通信が暗号化されなくなります。 hadoop.rpc.protection の "Privacy" または "Integrity" 設定を使用するには、PolyBase サーバーで core-site.xml ファイルを更新します。 詳細については、前のセクションの「[Hadoop.RPC.Protection 設定での Hadoop クラスターへの接続](#rpcprotection)」を参照してください。

Kerberos でセキュリティ保護された Hadoop に接続するには、すべての AP の次の変更が必要な MIT KDC を使用してクラスターのコンピューティング ノードと制御ノード。

1. アクセス ポイントのインストール パスで Hadoop 構成ディレクトリが見つかりません。 通常、このパスは次のとおりです。  

   ```  
   C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\Hadoop\conf  
   ```  

2. 次の表に示す構成キーの Hadoop 側の構成値を検索します (Hadoop コンピューター上の Hadoop 構成ディレクトリ内でファイルを検索します)。  
   
3. これらの構成値を、SQL Server コンピューター上の対応するファイル内の値プロパティにコピーします。  
   
   |**#**|**構成ファイル**|**構成キー**|**操作**|  
   |------------|----------------|---------------------|----------|   
   |1|core-site.xml|polybase.kerberos.kdchost|KDC のホスト名を指定します。 例: kerberos.your-realm.com.|  
   |2|core-site.xml|polybase.kerberos.realm|Kerberos 領域を指定します。 以下に例を示します。YOUR-REALM.COM|  
   |3|core-site.xml|hadoop.security.authentication|Hadoop 側の構成を検出して SQL Server コンピューターにコピーします。 以下に例を示します。KERBEROS<br></br>**セキュリティに関する注意:** KERBEROS は大文字で記述する必要があります。 小文字の場合、機能しない可能性があります。|   
   |4|hdfs-site.xml|dfs.namenode.kerberos.principal|Hadoop 側の構成を検出して SQL Server コンピューターにコピーします。 例: hdfs/_HOST@YOUR-REALM.COM|  
   |5|mapred-site.xml|mapreduce.jobhistory.principal|Hadoop 側の構成を検出して SQL Server コンピューターにコピーします。 例: mapred/_HOST@YOUR-REALM.COM|  
   |6|mapred-site.xml|mapreduce.jobhistory.address|Hadoop 側の構成を検出して SQL Server コンピューターにコピーします。 以下に例を示します。10.193.26.174:10020|  
   |7|yarn-site.xml yarn.|yarn.resourcemanager.principal|Hadoop 側の構成を検出して SQL Server コンピューターにコピーします。 例: yarn/_HOST@YOUR-REALM.COM|  

**core-site.xml**
```xml
<property>
  <name>polybase.kerberos.realm</name>
  <value></value>
</property>
<property>
  <name>polybase.kerberos.kdchost</name>
  <value></value>
</property>
<property>
    <name>hadoop.security.authentication</name>
    <value>KERBEROS</value>
</property>
```

**hdfs-site.xml**
```xml
<property>
  <name>dfs.namenode.kerberos.principal</name>
  <value></value> 
</property>
```

**mapred-site.xml**
```xml
<property>
  <name>mapreduce.jobhistory.principal</name>
  <value></value>
</property>
<property>
  <name>mapreduce.jobhistory.address</name>
  <value></value>
</property>
```

**yarn-site.xml**
```xml
<property>
  <name>yarn.resourcemanager.principal</name>
  <value></value>
</property>
```

4. 各 Hadoop ユーザーの認証情報を指定するデータベース スコープ資格情報オブジェクトを作成します。 「 [PolyBase T-SQL オブジェクト](../relational-databases/polybase/polybase-t-sql-objects.md)」を参照してください。

## <a id="encryptionzone"></a> Hadoop 暗号化ゾーンのセットアップ
Hadoop を使用している場合は、暗号化ゾーンが core-site.xml、hdfs-site.xml 次のように変更します。 対応するポート番号を持つ KMS サービスが実行されている ip アドレスを提供します。 CDH の KMS の既定のポートでは、16000 です。

**core-site.xml**
```xml
<property>
  <name>hadoop.security.key.provider.path</name>
  <value>kms://http@<ip address>:16000/kms</value> 
</property>
```

**hdfs-site.xml**
```xml
<property>
  <name>dfs.encryption.key.provider.uri</name>
  <value>kms://http@<ip address>:16000/kms</value>
</property>
<property>
  <name>hadoop.security.key.provider.path</name>
  <value>kms://http@<ip address>:16000/kms</value>
  </property>
```