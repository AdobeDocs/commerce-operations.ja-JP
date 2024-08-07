---
title: 自己ホスト型Adobe Commerceのパフォーマンスヒント
description: 自己ホスト型のパフォーマンスに関するヒントのアイデアと概念、および考慮すべきベストプラクティスについて説明します。
landing-page-description: Adobe Commerceを独自にホストする際に考慮すべきパフォーマンスに関するヒントの概念と事項について説明します。
short-description: Adobe Commerceを自分でホストするための戦略やパフォーマンスに関するヒントの概念について説明します。
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: bfce5c35-66c3-4d5c-a7b0-58f6d54febf8
feature: Install
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '1271'
ht-degree: 0%

---

# 自己ホスト型Adobe Commerceのパフォーマンスヒント

柔軟かつ強力な e コマースプラットフォームを使用するからといって、パフォーマンスを犠牲にする必要があるわけではありません。 Adobe Commerceの創業以来、コアアプリケーションには多くの改善がありました。 バージョン 2.5.4 では、Adobe Commerceのエンジニアリングチームがセットテストを実行して、アプリケーションのベンチマークを実行しました。 テストの結果、Adobe Commerceは 2 億 4,000 万を超える SKU の大規模なカタログを処理でき、API リクエスト時間は平均 300 ミリ秒が例外的で、1 時間あたりのページビューと注文の数は、200 万件のページビューと 1 時間あたりの 208,000 件の注文という驚異的なものになることが示されました。

[ 実装 – Adobe Commerce -Experience Leagueプレイブック – ベンチマーク ](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/infrastructure/performance/benchmarks.html){target="_blank"} に進んで、最新のベンチマーク結果を参照してください。

できるだけ物事を最適な状態に保つため、カスタマイズを追加したりプロジェクトを複雑にしたりする際には、次の基準に従います。

以下の節では、セルフホスティング実装を最適化する方法に関して検討すべきトピックとアドバイスについて説明します。

## ワニス

Varnish は、キャッシュを使用した HTTP リバースプロキシです。 結果は複雑に見えるかもしれませんが、ソースから項目を取得する必要がある場合よりもリクエストが迅速に返されるようにするための迅速な応答です。 一部のバージョンの Varnish を使用せずにAdobe Commerce サイトを実行すると、ページの読み込みが遅くなるなどの主要指標が表示されます。 ワニスは自分で設定して管理するのが少し難しい場合がありますが、Adobe Commerceでの使用について理解を深めるために、Experience League[ ワニスを設定 ](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/varnish/config-varnish.html){target="_blank"} でこのトピックを扱っています。 クラウドベースのソリューションを使用する方法もあります。 検討すべき多くのものがありますが、Fastly は cloud 上のAdobe Commerceのソリューションとして選択されました。 VCL と多くのファセットのニスを使用する、クラウドベースの Fastly のバージョンです。

アプリケーション、構成、予算、および技術的な能力に最適なソリューションを見つけるのは、難しい作業です。 クラウドベースのオプションを使用すると、管理、設定、サーバー、その他のインフラストラクチャコンポーネントを考慮する限り、すべてのハードパーツが消えます。 パフォーマンス、スケーラビリティ、スループット、その他多くの主要指標から、Adobe Commerce on cloud team によってソリューションとして選択されました。

ワニスに関するプロジェクトに適したソリューションを選択することで、顧客に最高のパフォーマンスを提供し、コマースアプリケーションが必要以上に作業しなくて済むように設定できます。

## CDN

Adobe Commerce プロジェクトにとってワニスは貴重な資源であると同時に、次に挙げるのは CDN です。 CDN は、Varnish と共に、CSS のキャッシュされたインスタンス、画像などのページアセットを提供し、Adobe Commerce アプリケーションに発生する帯域幅を減らすのに役立ちます。 ヘッドレスなGraphQL サイトのメリットをさらに高めるために、Adobe Commerceの応答をキャッシュできます。 一部の CDN では、画像の最適化、web アプリケーションファイアウォールおよびその他の機能が提供されます。

cloud 上のAdobe Commerceは、Varnish キャッシュだけでなく CDN にも Fastly を使用することを選択しました。 この 1 つのソリューションは、クラウド上のAdobe Commerceのお客様に優れたエクスペリエンスを提供するために無数の機能を提供します。 詳しくは、Experience Leagueの Fastly サービスの概要 [Fastly サービスの概要 ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html){target="_blank"} を参照してください

CDN は、Adobe Commerce プロジェクト用に最適化された安全な配信コンテンツを提供します。 プロジェクトに必須のコンポーネントではない可能性がある場合は、サイトが成熟し、訪問者数が増加するにつれて考慮する必要があります。 CDN を提供すると、各リクエストから削除された負荷のために、インフラストラクチャへのハードウェアの追加や既存のインフラストラクチャのスケーリングを遅らせることができます。

## モジュールの無効化

未使用のモジュールの無効化は考慮する必要がありますが、軽視しないでください。 この手法により、一部のリクエストのオーバーヘッドと処理時間が削減されますが、考慮すべき副作用もあります。 機能を作成する際に、開発者がモジュールが使用可能であると想定する場合がよくあります。 多くの場合、無効になったモジュールで見つかった一部のクラスを使用することを選択していない限り、これは安全です。

ネイティブの「ニュースレター」などのモジュールを無効にすることは、かなり一般的なイベントです。 これは、特にストアオーナーが、ニュースレターを管理するサードパーティの会社を持っている場合に当てはまります。 これが問題になる可能性があるのは、サードパーティモジュールがインストールされ、何らかの理由で、彼らがニュースレターのクラスを使用することにしました。 この誤った依存関係は、最初のインストールとテストの際に発見される可能性が高いものの、このサードパーティモジュールを保持するか、ニュースレターを有効にするかを決定し、導入された奇妙な動作を探すためにサイトを回帰テストする必要があります。 または、そのサードパーティモジュールの代わりになるものを見つけますか。 どちらの決定にもリスク、時間、場合によってはバグが伴います。

未使用のモジュールを無効にする前に、単体、[MFTF](https://developer.adobe.com/commerce/cloud-tools/docker/test/application-testing/){target="_blank"}、[Codeception テスト ](https://developer.adobe.com/commerce/cloud-tools/docker/test/code-testing/){target=&quot;_blank&quot;} 読み込みテスト、影響を受ける可能性のある API リクエストなどのテストがないことを確認してください。

## すべてのプルリクエストで、Adobe Commerceおよび PHP のコーディング標準に従う必要があります

Adobe Commerceには、一連の [ コーディング標準 ](https://developer.adobe.com/commerce/php/coding-standards/){target="_blank"} があります。 これにより、ソフトウェア開発のタイプに関係なく、同様のパターン、スタイル、期待されるデザインに従うことができます。 Adobe Commerce コードベースにコントリビューションする場合、これは要件です。 ただし、カスタム開発にこの手法に従うことを選択した場合は、現在および将来の両方のすべての開発者にとって強固な基盤が確立されます。 コード標準を渡すためにすべてのプルリクエストを要求する場合、すべての人が同じ一貫性のある開発パターンを理解し、期待できるようにするのに役立ちます。

Adobe Commerceのコーディング標準に合わせて、もう 1 つの基盤は PHP の基本的なコーディング標準です。 開発者ガイドで、従う必要のある標準と、許容できる逸脱を明確に定義する必要があります。 ただし、フォールバックは [PHP-FIG](https://www.php-fig.org){target="_blank"} で公開されているガイドに対して行う必要があります。

PSR-1 及び PSR-12 の遵守に向けた確固たる姿勢 プロジェクトに参加する開発者がこれらの指示に従うことを確認することで、奇妙に構造化されたファイルやパターンが存在しないようにできます。 これにより、今後の開発者が、レビュー対象のコードをすばやく読んで理解できるようになります。 これらのパターンとコーディング標準に忠実に従うほど、今後の開発作業が読みやすくなり、実装が迅速になります。

## 各デプロイメントの後で負荷テストを実行します

各デプロイメントの後に負荷テストを実行すると、負荷テストが過剰に見える場合があります。 ただし、この方法に従うと、パフォーマンスの低下を引き起こす新しく導入された機能の機会を追跡して軽減できます。

新しいコードからパフォーマンスの低下を検出する以外に、サイトの主要指標の履歴参照があると、新しいツールや変更インフラストラクチャがいつ有効になるかについてのインサイトを得ることができます。 例えば、環境のサイズを大きくして、期待するパフォーマンスが向上することを期待してホスティング会社に料金を支払う前に、新しい設定でステージング環境を設定し、負荷テストを実行して、実際の結果を確認できます。

これらのテストは、CI/CD パイプラインの一部として自動化できます。 これにより、結果を受け取り、ノルムからの偏差が大きすぎる場合にフィーチャーのマージをブロックする可能性があるルールを設定することもできます。 このデータのユースケースの数は無制限ですが、このプロセスを開始しないと、その可能性に気付かない可能性があります。

Adobe Commerceには、Experience League[ パフォーマンステストのヒント ](https://experienceleague.adobe.com/docs/commerce-operations/deliver-commerce-at-scale/launch.html){target="_blank"} および [ テストガイダンス ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/guidance.html){target="_blank"} に記載されているこのトピックに関する十分な知識があります。

{{$include /help/_includes/hosting-related-links.md}}
