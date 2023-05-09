---
title: 自己ホストの概要
description: 自己ホスト型のベストプラクティスについて学びます。 このトピックは、セキュリティ要素から災害復旧まで、さらに多くの領域に及びます。 これらのトピックは、独自のバージョンのAdobe Commerceをホストすることを決定した会社を支援するために、ここにあります。 提示される項目はすべて包括的ではありませんが、安全で安定した、回復力の高い Web サイトを促進するための適切な概念の範囲を提供する必要があります。
landing-page-description: Adobe Commerceを単独でホストする際に考慮すべき概念と事項について説明します。
short-description: 自分でAdobe Commerceをホストするための戦略と概念について学びます。
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
source-git-commit: ef89ace2f03d5010384ba759e81695b6ae7e630b
workflow-type: tm+mt
source-wordcount: '738'
ht-degree: 0%

---


# 自己ホスト型Adobe Commerceの概要

Adobe Commerceなどの e コマースプラットフォームへの移行を検討する場合、オプションが豊富に用意されています。 ただし、これらのオプションを使用すると、追加のコスト、リスク、負債を考慮する必要があります。 コマースサイトのホストは、パッケージ化されたソリューション（例： ）を使用しておこなうことができます。 [Adobe Commerce an cloud infrastructure](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"}：インフラストラクチャ、サーバー、E メール、SSL 証明書など、多くの証明書が事前に設定され、使用できる状態になっています。 クラウドインフラストラクチャ上のAdobe Commerceなどの適切なホスティングソリューションを見つけると、プロセス全体をより簡単にすることができ、コマースサイトを自己ホストする理由が生じます。 付属のページには、自己ホストが提供するサービス、技術および概念に関するインサイトとガイダンスを提供する多くのトピックが含まれています。 ここに示す情報は完全なものではなく、すべての提案を実装する必要があるとは限りません。 ただし、これらの記事は、Adobe Commerceの自己ホストをできるだけ安定し、安全にするためのアイデアと概念を理解するのに役立ちます。

Adobe Commerce on cloud infrastructure を使用しない場合、自己ホスト型またはオンプレミス型の用語、またはオンプレミス型の用語が使用されます。 オンプレミスは、会社が所有するビル内のデータセンターでのみ意味しません。 この用語は、インフラストラクチャ上でAdobe Commerceがサポートを管理していないものを表します。 Adobe Commerceを利用するホスティング会社もあり、自己ホストまたはオンプレミスと見なされます。

Adobe CommerceとMagentoのオープンソースに関して、提供されるアドバイスとヒントのほとんどは、どちらのバージョンでも機能します。 直接述べていない場合でも、両方に適用できることを期待しています。 Adobe Commerceの自己ホストオプションのこのトピックでは、両方のバージョンが考慮されます。 最後に、ほとんどのトピックは [Adobe Commerce an cloud infrastructure](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"} がホスティングプロバイダーとして選択されている。

## 用語レベルセット

以下の用語は、DevOps チームと話し合い、会社のサポートと協力する際に、Experience League記事全体で一般的に使用されます。

* **DevOps** は、Adobe Commerceサイトの実行に使用される実際のサーバーやサービスに関する、サーバーの設定、設定、管理、SSL 証明書など、すべてのチームを表す用語です。 この用語は、開発者の責任が通常終了するタイミングと、インフラストラクチャチームによるトリエージとサポートが開始される場所を指定するのに役立ちます。

* **セキュリティ概念** Adobe Commerceのコードベース、ファイル、ファイルシステムをサーバ上に作成するためのトピックと考慮事項、および既知の不正利用パターンの攻撃面を減らす設定や更新に関する情報をいくつか取り上げます。

* **監視ツール** では、Adobe Commerce Web サイトを監視する既存のツールおよびサービスの一部について説明します。 これらのツールでは、改善方法に関するヒントを提供したり、問題やセキュリティの脆弱性を明らかにしたりできます。

* **災害復旧** は、破損した、または悪用されたプロジェクトの不幸なイベントに関する概念や考慮事項を提供するのに役立ちます。

* **パフォーマンスのヒント** Adobe Commerceアプリケーションのパフォーマンスを可能な限り高めるための、いくつかのプロヒントとガイダンスを提供します。

* **悪役** は、悪意のある、または権限のない何かをしようとする人またはチームに対して使用される用語です。 コマースアプリケーションに限定されるのではなく、インフラストラクチャや Web サイトに関連する任意のコンポーネントにも拡張されます。

* **Web アプリケーションファイアウォール** (WAF) は、コマースアプリケーションへの各要求の見出しを監視するのに役立ち、既知のパターンや悪用をブロックします。 多くの場合、WAF は、DDOS 攻撃の管理に役立つカスタムフィルターやルールと組み合わせて使用されます。

* **分散型サービス拒否** (DDoS) は、Web サイトを実行しているサーバーを、正当なリクエストに応答できなくなる十分な量の偽のリクエストで消費するよう強制する攻撃方法です。

## 次の手順

これらのトピックは、特別な順序やシーケンスではありません。 これは、DevOps エンジニア、コマースアーキテクト、およびAdobe Commerceのホスト場所と方法に関するこの重要な決定に関わる他の誰かと話し合うポイントを提供することを目的としています。

{{$include /help/_includes/hosting-related-links.md}}