---
title: 自己ホスト型Adobe Commerceのパフォーマンスに関するヒント
description: 自己ホスト型パフォーマンスに関するヒントのアイデアと概念、および考慮すべきベストプラクティスについて説明します。
landing-page-description: Adobe Commerceを独自にホストする際に考慮すべきパフォーマンスに関するヒントの概念と事項について説明します。
short-description: Adobe Commerceを自分でホストするための戦略とパフォーマンスに関するヒントの概念について説明します。
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
source-git-commit: ab099b2a8a353c2462424831cf8100e7e281b1be
workflow-type: tm+mt
source-wordcount: '1304'
ht-degree: 0%

---


# 自己ホスト型Adobe Commerceのパフォーマンスに関するヒント

柔軟で強力な e コマースプラットフォームを使用することは、パフォーマンスを犠牲にする必要があるわけではありません。 Adobe Commerceの設立以降、コアアプリケーションに多数の改善が加えられています。 バージョン 2.5.4 では、Adobe Commerceのエンジニアリングチームが、アプリケーションをベンチマークするための設定テストを実行しました。 テスト結果によると、Adobe Commerceは 2 億 4,000 万を超える SKU の大きなカタログを処理でき、API リクエスト時間は例外的に平均 300 ミリ秒です。また、1 時間あたりのページビュー数と注文数は、200 万ページビュー、208,000 注文です。

に目を通して最新のベンチマーク結果を確認する [Experience League- Adobe Commerce — 実装プレイブック — ベンチマーク](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/infrastructure/performance/benchmarks.html){target="_blank"}.

可能な限り最適な状態を維持するには、カスタマイズと複雑さをプロジェクトに追加する際に、次の標準に従います。

以下の節では、自己ホスト型実装を最適化する方法について考慮するトピックとアドバイスを示します。

## ワニス

Vanish はキャッシュ付きの HTTP リバースプロキシです。 複雑に見えるかもしれませんが、結果は高速応答で、ソースから項目を取得する場合よりもリクエストを迅速に返すようにします。 一部のバージョンの Vanrish を使用せずにAdobe Commerceサイトを実行すると、ページの読み込みが遅くなり、その他の主要指標が表示されます。 Vanrish は、設定と管理が少し難しい場合がありますが、このトピックはExperience Leagueにあります [ワニスを設定](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/varnish/config-varnish.html){target="_blank"} Adobe Commerceでの使用に関する理解を深めるために。 クラウドベースのソリューションを使用する方法もあります。 多くの検討が必要ですが、Fastly はクラウド上のAdobe Commerceのソリューションとして選ばれました。 VCL とワニスの多くのファセットを使用する Fastly の雲ベースのバージョンです。

アプリケーション、設定、予算、技術的な能力に最適なソリューションを見つけるのは、難しい作業です。 クラウドベースのオプションを使用すると、管理、設定、サーバ、その他のインフラストラクチャコンポーネントが考慮される限り、すべてのハードパーツが消えます。 パフォーマンス、拡張性、スループット、その他多くの主要指標が原因で、Adobe Commerce on cloud チームがソリューションとして選択されました。

Vanish に関するプロジェクトに適したソリューションを選択すると、顧客に最適なパフォーマンスを提供し、コマースアプリケーションを必要以上に高い作業から保存するための設定を行います。

## CDN

Vanish は、Adobe Commerceプロジェクトにとって貴重なアセットですが、次の行は CDN です。 CDN は、Vanrish と共に、CSS にキャッシュされたインスタンス（画像など）を提供し、Adobe Commerceアプリケーションに送られる帯域幅を減らすのに役立ちます。 ヘッドレスAdobe Commerceサイトのメリットを促進するGraphQL応答をキャッシュできます。 一部の CDN には、画像の最適化、Web アプリケーションのファイアウォール、その他の機能が用意されています。

Adobe Commerce On Cloud は、Vanish のキャッシュに Fastly を使用するだけでなく、CDN としても使用することを選択しました。 この単一のソリューションは、クラウド上のAdobe Commerceのお客様に優れたエクスペリエンスを提供する、無数の機能を提供します。 Fastly サービスの概要については、Experience Leagueを参照してください [Fastly サービスの概要](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html){target="_blank"}

CDN は、Adobe Commerceプロジェクト用に最適化された安全な配信コンテンツを提供します。 これがプロジェクトの必須コンポーネントでない場合は、サイトが成長し、訪問者数が増えると考える必要があります。 CDN を提供すると、各要求から負荷が削除されるので、インフラストラクチャへのハードウェアの追加や既存のインフラストラクチャの拡張を遅らせることができます。

## モジュールの無効化

未使用のモジュールを無効にする場合は、慎重に検討する必要がありますが、慎重におこなう必要はありません。 この方法を使用すると、一部のリクエストでのオーバーヘッドと処理時間が少なくなりますが、考慮すべき副作用があります。 多くの場合、開発者が機能を作成する際にモジュールが使用可能であると想定している場合があります。 無効にされたモジュール内の一部のクラスを使用した場合を除き、多くの場合、これは安全です。

ネイティブの「ニュースレター」などのモジュールを無効にすることは、かなり一般的なイベントです。 これは特に、店舗の所有者がニュースレターを管理するサードパーティの会社を持っている場合に当てはまります。 これが問題になる可能性があるのは、サードパーティのモジュールがインストールされている場合で、何らかの理由でニュースレターのクラスを使用することにした場合です。 この誤った依存関係は、初期のインストールとテストの間に発生する可能性が高いですが、このサードパーティのモジュールを保持するかどうかを決定し、ニュースレターを有効にしてから、サイトの回帰テストを実行して、導入された奇妙な動作を探します。 または、そのサードパーティ製モジュールの代替機能を見つけるか、 どちらの意思決定もリスク、時間、そしておそらくバグを伴います。

未使用のモジュールを無効にする前に、unit、 [MFTF](https://developer.adobe.com/commerce/cloud-tools/docker/test/application-testing/){target="_blank"}, [Codeception testing](https://developer.adobe.com/commerce/cloud-tools/docker/test/code-testing/){targe="_blank"} 影響を受ける可能性のあるロードテストまたは API リクエスト。

## すべてのプル要求に対してAdobe Commerceと PHP のコーディング規格に従う必要がある

Adobe Commerceは [コーディング規格](https://developer.adobe.com/commerce/php/coding-standards/){target="_blank"}. これらは、ソフトウェア開発の種類に関係なく、同様のパターン、スタイル、および期待されるデザインに従うことを保証します。 Adobe Commerceのコードベースに貢献する場合は、これが必須です。 ただし、カスタム開発でこの方法に従うことを選択する場合は、現在と将来の両方のすべての開発者に対して、確実な基礎を確立します。 すべてのプルリクエストにコード標準を渡す必要がある場合、誰もが同じ一貫した開発パターンを理解し、期待できるようにします。

Adobe Commerceのコーディング規格に従うために、他の基盤として PHP の基本的なコーディング規格が使用されます。 開発者ガイドで、従う必要のある標準と、許容可能な偏差について明確に定義する必要があります。 ただし、フォールバックは、次の場所にある公に管理されているガイドに対するものです。 [PHP-FIG](https://www.php-fig.org){target="_blank"}.

PSR-1 および PSR-12 に対する確固たる姿勢。 プロジェクトに貢献する開発者が必ずこれらに従うようにすることで、明確に構造化されたファイルやパターンがなくなります。 また、これは、将来の開発者がレビュー中のコードをすばやく読み、理解するのに役立ちます。 これらのパターンやコーディング標準に準拠すればするほど、今後の開発作業は読みやすく、迅速に実装する必要があります。

## 各デプロイメント後に負荷テストを実行

各デプロイメントの後に負荷テストを実行すると、負荷テストが行き過ぎているように見える場合があります。 ただし、この方法に従うと、新しく導入された機能がパフォーマンスの低下を引き起こす機会を追跡し、軽減することができます。

新しいコードからパフォーマンスの低下を検出する以外に、サイトからの主要指標の履歴参照を使用すると、新しいツールや変更インフラストラクチャが有効になったタイミングを把握できます。 例えば、ホスティング会社に環境の規模を拡大して期待する場合は、新しい設定でステージング環境を設定し、実際の結果を確認するための負荷テストを実行します。

これらのテストは、CI/CD パイプラインの一部として自動化できます。 このため、結果を取り込むルールを適用し、標準との偏差が大きすぎる場合に機能のマージを妨げる可能性もあります。 このデータの使用例の数には制限はありませんが、このプロセスを開始しないと、その可能性を常に認識できなくなります。

Adobe Commerceは、Experience Leagueで見つかったこのトピックに関する良い書き上げを行いました [パフォーマンステストのヒント](https://experienceleague.adobe.com/docs/commerce-operations/deliver-commerce-at-scale/launch.html){target="_blank"} and in [Testing guidance](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/guidance.html){target="_blank"}.

{{$include /help/_includes/hosting-related-links.md}}
