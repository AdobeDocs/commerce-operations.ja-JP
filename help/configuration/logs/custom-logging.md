---
title: カスタムログ
description: カスタムログを使用してエラーを調査する方法を説明します。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---


# カスタムログの概要

ログは、システムプロセスを可視化します。例えば、エラーが発生したタイミングやエラーの原因を把握するのに役立つデバッグ情報などです。

このトピックでは、ファイルベースのログに焦点を当てますが、Commerce では、ログをデータベースに柔軟に保存することもできます。

Adobeでは、次の理由により、一元化されたアプリケーションログの使用をお勧めします。

- アプリケーションサーバー以外のサーバーでログを保存でき、ディスクの I/O 操作を減らし、アプリケーションサーバーのサポートを簡単にします。

- ログデータの処理は、 [Logstash], [Logplex]または [溝] — 本番サーバに影響を与えません。

   >[!INFO]
   >
   >Adobeは、特定のログソリューションを推奨または推奨しません。

## PSR-3 準拠

この [PSR-3 標準][laminas] は、ライブラリをログに記録するための共通の PHP インタフェースを定義します。 PSR-3 の主な目的は、ライブラリが `Psr\Log\LoggerInterface` オブジェクトに書き込み、簡単で普遍的な方法でログを書き込みます。

これにより、実装を簡単に置き換えることができ、そのような置き換えによってアプリケーションコードが破損する可能性があるので、心配する必要はありません。 また、将来のバージョンのシステムでログの実装が変更された場合でも、カスタムコンポーネントが確実に機能するようになります。

## Monolog

コマース 2 は、PSR-3 標準に準拠しています。 デフォルトでは、Commerce は [Monolog]. の環境設定として実装された Monolog `Psr\Log\LoggerInterface` （Commerce アプリケーション内） [`di.xml`][di].

Monolog は、高度なログ戦略を構築できる様々なハンドラを備えた一般的な PHP ログソリューションです。 Monolog の動作の概要を次に示します。

モノローグ _logger_ は、独自のセットを持つチャネルです。 _ハンドラー_. Monolog には、次のような多くのハンドラーがあります。

- ファイルと syslog にログ
- アラートと E メールの送信
- 特定のサーバとネットワークログを記録する
- 開発へのログイン（FireBug や Chrome Logger との統合など）
- データベースにログ

各ハンドラは、入力メッセージを処理して伝播を停止するか、連鎖内の次のハンドラに制御を渡すことができます。

ログメッセージは様々な方法で処理できます。 たとえば、すべてのデバッグ情報をディスク上のファイルに保存し、ログレベルの高いメッセージをデータベースに配置し、最後にログレベルが「重要」のメッセージを電子メールで送信できます。

他のチャネルでは、異なるハンドラーとロジックのセットを使用できます。

<!-- link definitions -->

[di]: https://github.com/magento/magento2/blob/2.4/app/etc/di.xml#L9
[溝]: http://www.fluentd.org
[laminas]: https://docs.laminas.dev/laminas-log/
[Logplex]: https://devcenter.heroku.com/articles/logplex
[Logstash]: https://www.elastic.co/products/logstash
[Monolog]: https://github.com/Seldaek/monolog
