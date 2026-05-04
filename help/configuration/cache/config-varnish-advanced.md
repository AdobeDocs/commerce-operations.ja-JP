---
title: 高度なVarnish設定
description: ヘルスチェック、グレース、サントモードなど、Adobe Commerceの高度なVarnish機能を設定する方法について説明します。 VCL最適化テクニックの詳細。
feature: Configuration, Cache
exl-id: 178bd675-6ed0-40cc-9455-08a11b32c054
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '908'
ht-degree: 0%

---

# 高度なVarnish設定

Varnishには、Commerce サーバーが正常に機能していない場合に長い遅延やタイムアウトが発生するのを防ぐ機能がいくつか用意されています。 これらの機能は、`default.vcl` ファイルで設定できます。 このトピックでは、AdminからダウンロードしたVCL （Varnish Configuration Language）ファイルにCommerceが提供する追加機能について説明します。

Varnish設定言語の使用について詳しくは、[Varnish リファレンスマニュアル ](https://varnish-cache.org/docs/index.html)を参照してください。

## ヘルスチェック

Varnish ヘルスチェック機能は、Commerce サーバーをポーリングして、タイムリーに応答しているかどうかを判断します。 正常に応答している場合、有効期間（TTL）が終了すると、新しいコンテンツが再生成されます。 そうでない場合、Varnishは常に古いコンテンツを提供します。

Commerceでは、次のデフォルトのヘルスチェックを定義します。

```conf
.probe = {
    .url = "/pub/health_check.php";
    .timeout = 2s;
    .interval = 5s;
    .window = 10;
    .threshold = 5;
    }
```

5秒ごとに、このヘルスチェックは`pub/health_check.php` スクリプトを呼び出します。 このスクリプトは、サーバー、各データベース、およびRedis （インストールされている場合）の可用性を確認します。 スクリプトは2秒以内に応答を返す必要があります。 これらのリソースのいずれかがダウンしているとスクリプトが判断した場合は、500 HTTP エラーコードが返されます。 このエラーコードが10回の試行のうち6回で受信された場合、バックエンドは異常と見なされます。

`health_check.php` スクリプトは`pub` ディレクトリにあります。 Commerce ルート ディレクトリが`pub`の場合は、`url` パラメーターのパスを`/pub/health_check.php`から`health_check.php`に変更してください。

詳しくは、[Varnish ヘルスチェック ](https://varnish-cache.org/docs/7.4/users-guide/vcl-backends.html#health-checks)のドキュメントを参照してください。

## 猶予モード

グレース モードを使用すると、VarnishはTTL値を超えてオブジェクトをキャッシュに保持できます。 Varnishは、新しいバージョンを取得する間、期限切れの（古い）コンテンツを配信できます。 これにより、トラフィックの流れが改善され、読み込み時間が短縮されます。 次のような状況で使用されます。

- Commerce バックエンドが正常に動作しているが、リクエストに通常よりも時間がかかっている場合
- Commerce バックエンドが正常でない場合。

`vcl_hit` サブルーチンは、キャッシュされたオブジェクトに対するリクエストにVarnishがどのように応答するかを定義します。

### Commerceのバックエンドが正常に動作している場合

ヘルスチェックでCommerce バックエンドが正常であると判断された場合、Varnishは時間が猶予期間に残っているかどうかをチェックします。 デフォルトの猶予期間は300秒ですが、マーチャントは、[CommerceをVarnish](configure-varnish-commerce.md)を使用するように設定で説明されているように、管理者から値を設定できます。 猶予期間が終了していない場合、Varnishは古いコンテンツを配信し、Commerce サーバーからオブジェクトを非同期で更新します。 猶予期間が終了した場合、Varnishは古いコンテンツを提供し、オブジェクトをCommerce バックエンドから同期して更新します。

Varnishが古いオブジェクトにサービスを提供する最大時間は、猶予期間（デフォルトでは300秒）とTTL値（デフォルトでは86400秒）の合計です。

`default.vcl` ファイル内からデフォルトの猶予期間を変更するには、`vcl_hit` サブルーチンで次の行を編集します。

```conf
if (obj.ttl + 300s > 0s) {
```

### Commerceのバックエンドが正常でない場合

Commerce バックエンドがレスポンシブでない場合、Varnishは、キャッシュされたコンテンツが手動でパージされない限り、キャッシュから古いコンテンツを3日間（または`beresp.grace`で定義されたとおりに）追加して残りのTTL （デフォルトでは1日）提供します。

## Saint モード

Saint モードは、設定可能な時間の不健全なバックエンドを除外します。 その結果、Varnishをロードバランサーとして使用する場合、不健全なバックエンドはトラフィックを提供できません。 Saint モードをgrace モードと組み合わせて使用すると、正常でないバックエンドサーバーを複雑に処理できます。 例えば、あるバックエンドサーバーが正常でない場合、再試行は別のサーバーにルーティングされます。 他のすべてのサーバーがダウンしている場合は、古いキャッシュオブジェクトを提供します。 Saint モードのバックエンド ホストとブラックアウト期間は、`default.vcl` ファイルで定義されます。

Saint モードは、Commerce インスタンスを個別にオフラインにして、Commerce サイトの可用性に影響を与えることなく、メンテナンスやアップグレードのタスクを実行する場合にも使用できます。

### Saint モードの前提条件

1台のマシンをプライマリインストールとして指定します。 このマシンに、Commerce、mySQL データベース、およびVarnishのメインインスタンスをインストールします。

その他のすべてのマシンでは、Commerce インスタンスがプライマリマシンのmySQL データベースにアクセスできる必要があります。 セカンダリマシンは、プライマリ Commerce インスタンスのファイルにもアクセスできる必要があります。

または、すべてのマシンで静的ファイルのバージョン管理をオフにすることもできます。 これは、管理者から&#x200B;**ストア** >設定> **設定** > **詳細** > **開発者** > **静的ファイル設定** > **静的ファイルに署名** = **No**&#x200B;でアクセスできます。

最後に、すべてのCommerce インスタンスが実稼動モードである必要があります。 Varnishを開始する前に、各インスタンスのキャッシュをクリアします。 管理画面で、**System** > Tools > **Cache Management**&#x200B;に移動し、**Flush Magento Cache**&#x200B;をクリックします。 次のコマンドを実行して、キャッシュをクリアすることもできます。

```shell
bin/magento cache:flush
```

### インストール

Saint モードはメインのVarnish パッケージの一部ではありません。 ダウンロードしてインストールする必要がある、個別にバージョン管理された`vmod`です。 そのため、Varnishのバージョンについては、[ インストール手順](https://varnish-cache.org/docs/index.html)の説明に従って、ソースからVarnishを再コンパイルする必要があります。

再コンパイルしたら、Saint モードモジュールをインストールできます。 一般的には、次の手順に従います。

1. ソースコードを[Varnish モジュール ](https://github.com/varnish/varnish-modules)から取得します。 0.9.x バージョンにソースコードエラーが含まれているので、Git バージョン（マスターバージョン）をクローンします。
1. オートツールを使用してソースコードを作成します。

   ```shell
   sudo apt-get install libvarnishapi-dev || sudo yum install varnish-libs-devel
   ./bootstrap   # If running from git.
   ./configure
   make
   make check   # optional
   sudo make install
   ```

Saint モードモジュールのインストールについて詳しくは、[Varnish モジュールコレクション ](https://github.com/varnish/varnish-modules)を参照してください。

### VCL ファイルのサンプル

次のコード例は、saint モードを有効にするためにVCL ファイルに追加する必要があるコードを示しています。 ファイルの先頭に`import`文と`backend`定義を配置します。

```cpp
import saintmode;
import directors;

backend default1 {
    .host = "192.168.0.1";
    .port = "8080";
    .first_byte_timeout = 600s;
    .probe = {
        .url = "/pub/health_check.php";
        .timeout = 2s;
        .interval = 5s;
        .window = 10;
        .threshold = 5;
    }
}

backend default2 {
    .host = "192.168.0.2";
    .port = "8080";
    .first_byte_timeout = 600s;
    .probe = {
        .url = "/pub/health_check.php";
        .timeout = 2s;
        .interval = 5s;
        .window = 10;
        .threshold = 5;
    }
}

sub vcl_init {
    # Instantiate sm1, sm2 for backends tile1, tile2
    # with 10 blacklisted objects as the threshold for marking the
    # whole backend sick.
    new sm1 = saintmode.saintmode(default1, 10);
    new sm2 = saintmode.saintmode(default2, 10);

    # Add both to a director. Use sm0, sm1 in place of tile1, tile2.
    # Other director types can be used in place of random.
    new magedirector = directors.random();
    magedirector.add_backend(sm1.backend(), 1);
    magedirector.add_backend(sm2.backend(), 1);
}

sub vcl_backend_fetch {
    # Get a backend from the director.
    # When returning a backend, the director will only return backends
    # saintmode says are healthy.
    set bereq.backend = magedirector.backend();
}

sub vcl_backend_response {
    if (beresp.status >= 500) {
        # This marks the backend as sick for this specific
        # object for the next 20s.
        saintmode.blacklist(20s);
        # Retry the request. This will result in a different backend
        # being used.
        return (retry);
    }
}
```
