---
title: カスタムログ
description: PSR-3への準拠や一元的なログ記録に関する考慮事項など、Adobe Commerceでカスタムファイルベースのログを使用してエラーを調査する方法について説明します。
feature: Configuration, Logs
exl-id: 6c94ebcf-70df-4818-a17b-32512eba516d
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: 3c398179-d35a-51ba-b317-6c5b95feef5e
    internal-label: Logs
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%
---
# カスタムログの概要

ログは、システムプロセスの可視性を提供します。例えば、エラーがいつ発生したか、エラーの原因を把握するのに役立つ情報をデバッグします。

このトピックでは、ファイルベースのロギングに焦点を当てていますが、Commerceでは、データベースにログを保存する柔軟性も提供しています。

Adobeでは、次の理由から、一元化されたアプリケーションログを使用することをお勧めします。

- アプリケーションサーバー以外のサーバーにログを保存できるようにし、ディスク I/O操作を減らすことで、アプリケーションサーバーのサポートを簡素化します。

- 本番サーバーに影響を与えることなく、[Logstash](https://www.elastic.co/products/logstash)、[Logplex](https://devcenter.heroku.com/articles/logplex)、[fluentd](https://www.fluentd.org/)などの特殊なツールを使用することで、ログデータの処理がより効果的になります。

  >[!INFO]
  >
  >Adobeは、特定のロギングソリューションを推奨または推奨するものではありません。

## PSR-3準拠

[PSR-3標準](https://docs.laminas.dev/laminas-log/)は、ライブラリをログ記録するための共通のPHP インターフェイスを定義します。 PSR-3の主な目的は、ライブラリが`Psr\Log\LoggerInterface` オブジェクトを受け取り、シンプルかつユニバーサルな方法でログを書き込めるようにすることです。

これにより、実装を容易に置き換えることができるため、アプリケーションのコードが破損する恐れがあります。 また、ログ実装が将来のバージョンのシステムで変更された場合でも、カスタムコンポーネントが機能することも保証されます。

## モノログ

Commerce 2はPSR-3規格に準拠しています。 デフォルトでは、Commerceは[Monolog](https://github.com/Seldaek/monolog)を使用します。 モノログは、Commerce アプリケーション [`di.xml`](https://github.com/magento/magento2/blob/2.4/app/etc/di.xml#L9)で`Psr\Log\LoggerInterface`の環境設定として実装されました。

Monologは、高度なロギング戦略を構築できる幅広いハンドラーを備えた人気のあるPHP ロギングソリューションです。 以下は、Monologの仕組みの概要です。

モノログ _logger_&#x200B;は、独自の&#x200B;_ハンドラー_&#x200B;のセットを持つチャネルです。 Monologには、以下のような多くのハンドラーがあります。

- ファイルとsyslogにログイン
- アラートと電子メールの送信
- 特定のサーバーとネットワーク化されたログの記録
- 開発中のログイン（FireBugやChrome Loggerとの統合など）
- データベースにログイン

各ハンドラーは、入力メッセージを処理して伝播を停止するか、チェーン内の次のハンドラーに制御を渡すことができます。

ログメッセージは、さまざまな方法で処理できます。 例えば、すべてのデバッグ情報をディスク上のファイルに保存し、ログレベルが高いメッセージをデータベースに格納し、最終的にログレベルが「クリティカル」なメッセージをメールで送信できます。

他のチャネルには、異なるハンドラーとロジックのセットを持つことができます。

