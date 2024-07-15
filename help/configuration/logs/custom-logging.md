---
title: カスタムログ
description: カスタムログを使用してエラーを調査する方法を説明します。
feature: Configuration, Logs
exl-id: 6c94ebcf-70df-4818-a17b-32512eba516d
source-git-commit: 991bd5fb34a2ffe61aa194ec46e2b04b4ce5b3e7
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# カスタムログの概要

ログはシステムプロセスを可視化します。例えば、エラーがいつ発生したか、何がエラーにつながったかを理解するのに役立つデバッグ情報などです。

このトピックではファイルベースのログに重点を置いていますが、Commerceにはデータベースにログを柔軟に保存する機能もあります。

Adobeは、次の理由から、一元化されたアプリケーションログを使用することをお勧めします。

- アプリケーションサーバー以外のサーバーにログを保存できるので、ディスクの I/O 操作が少なくなり、アプリケーションサーバーのサポートが簡単になります。

- [Logstash]、[Logplex]、[fluentd] などの特別なツールを使用することで、実稼動サーバーに影響を与えることなく、ログデータの処理をより効果的に行うことができます。

  >[!INFO]
  >
  >Adobeは、特定のログソリューションを推奨または推奨しません。

## PSR-3 への準拠

[PSR-3 標準 ][laminas] は、ライブラリをロギングするための共通の PHP インタフェースを定義します。 PSR-3 の主な目的は、ライブラリが `Psr\Log\LoggerInterface` オブジェクトを受け取り、ログを簡単かつ普遍的な方法で書き込めるようにすることです。

これにより、実装を簡単に置き換えることができ、置き換えるとアプリケーションコードが破損する可能性を心配する必要はありません。 また、システムの将来のバージョンでログの実装が変更された場合でも、カスタムコンポーネントが機能することが保証されます。

## モノローグ

Commerce 2 は PSR-3 規格に準拠しています。 デフォルトでは、Commerceは [Monolog] を使用します。 Monolog は、Commerce アプリケーション [`di.xml`][di] で `Psr\Log\LoggerInterface` の環境設定として実装されています。

Monolog は、高度なロギング戦略を構築できる幅広いハンドラを備えた一般的な PHP ログソリューションです。 以下は、モノローグの仕組みの概要です。

モノログ _ロガー_ は、独自の _ハンドラー_ を持つチャネルです。 Monolog には、次のような多くのハンドラーがあります。

- ファイルと syslog へのログ
- アラートとメールの送信
- ログ固有のサーバとネットワーク・ログ
- 開発のログイン（特に FireBug およびChrome Logger との統合）
- データベースへのログ

各ハンドラーは、入力メッセージを処理して伝播を停止するか、チェーン内の次のハンドラーに制御を渡すことができます。

ログメッセージは様々な方法で処理できます。 例えば、すべてのデバッグ情報をディスク上のファイルに保存し、より高いログレベルのメッセージをデータベースに配置し、最後にログレベルが「重要」なメッセージをメールで送信することができます。

他のチャネルでは、ハンドラーとロジックのセットが異なる場合があります。

<!-- link definitions -->

[di]: https://github.com/magento/magento2/blob/2.4/app/etc/di.xml#L9
[fluentd]: https://www.fluentd.org/
[laminas]: https://docs.laminas.dev/laminas-log/
[Logplex]: https://devcenter.heroku.com/articles/logplex
[Logstash]: https://www.elastic.co/products/logstash
[モノローグ]: https://github.com/Seldaek/monolog
