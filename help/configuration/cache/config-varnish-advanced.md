---
title: 高度なワニス設定
description: ヘルスチェック、グレース、saint モードなど、Adobe Commerceの高度なワニス機能を設定する方法について説明します。 VCL の最適化テクニックを紹介します。
feature: Configuration, Cache
exl-id: 178bd675-6ed0-40cc-9455-08a11b32c054
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '881'
ht-degree: 0%

---

# 高度なワニス設定

Varnish には、Commerce サーバーが正常に機能していないときに、お客様が長い遅延やタイムアウトを経験するのを防ぐいくつかの機能が用意されています。 これらの機能は、`default.vcl` ファイルで設定できます。 ここでは、管理者からダウンロードする VCL （Varnish Configuration Language）ファイルにCommerceによって追加された機能について説明します。

Varnish Configuration Language の使用について詳しくは、[Varnish Reference Manual](https://varnish-cache.org/docs/index.html) を参照してください。

## ヘルスチェック

ワニスヘルスチェック機能は、Commerce サーバーをポーリングして、サーバーがタイムリーに応答しているかどうかを判断します。 正常に応答している場合、有効期間（TTL）の期限が切れた後に、新しいコンテンツが再生成されます。 そうでない場合、ワニスは常に古いコンテンツを提供します。

Commerceは、次のデフォルトのヘルスチェックを定義します。

```conf
.probe = {
    .url = "/pub/health_check.php";
    .timeout = 2s;
    .interval = 5s;
    .window = 10;
    .threshold = 5;
    }
```

このヘルスチェックは 5 秒ごとに `pub/health_check.php` スクリプトを呼び出します。 このスクリプトは、サーバ、各データベース、および Redis （インストールされている場合）の可用性をチェックします。 スクリプトは、2 秒以内に応答を返す必要があります。 スクリプトがこれらのリソースのいずれかがダウンしていると判断した場合は、500 HTTP エラーコードが返されます。 このエラーコードが 10 回のうち 6 回受信された場合、バックエンドは正常でないと見なされます。

`health_check.php` スクリプトは、`pub` ディレクトリにあります。 Commerceのルートディレクトリが `pub` の場合は、`url` パラメーターのパスを必ず `/pub/health_check.php` から `health_check.php` に変更してください。

詳しくは、[ ワニスのヘルスチェック ](https://varnish-cache.org/docs/7.4/users-guide/vcl-backends.html#health-checks) のドキュメントを参照してください。

## 猶予モード

猶予モードを使用すると、Varnish は TTL 値を超えてオブジェクトをキャッシュに保持できます。 その後、ワニスは、新しいバージョンを取得しながら、期限切れ（古い）コンテンツを提供できます。 これにより、トラフィックのフローが改善され、読み込み時間が短縮されます。 次の状況で使用されます。

- Commerce バックエンドが正常であるが、リクエストに通常より長い時間がかかる場合
- Commerce バックエンドが正常でない場合。

`vcl_hit` サブルーチンは、キャッシュされたオブジェクトに対する要求に対する Varnish の応答方法を定義します。

### Commerce バックエンドが正常な場合

ヘルスチェックによってCommerce バックエンドが正常であることが判断されると、Varnish は時間が猶予期間内に残っているかどうかを確認します。 デフォルトの猶予時間は 300 秒ですが、[Commerceを使用するための設定 ](configure-varnish-commerce.md) で説明されているように、マーチャントは管理者から値を設定できます。 猶予期間が終了していない場合、Varnish は古いコンテンツを配信し、Commerce サーバーからオブジェクトを非同期に更新します。 猶予期間が経過すると、Varnish は古いコンテンツを提供し、Commerce バックエンドからオブジェクトを同期更新します。

Varnish が古いオブジェクトを提供する最大時間は、猶予期間（デフォルトでは 300 秒）と TTL 値（デフォルトでは 86400 秒）の合計です。

`default.vcl` ファイル内からデフォルトの猶予期間を変更するには、`vcl_hit` サブルーチンで次の行を編集します。

```conf
if (obj.ttl + 300s > 0s) {
```

### Commerce バックエンドが正常でない場合

Commerce バックエンドが応答しない場合、キャッシュされたコンテンツが手動でパージされない限り、Varnish は、3 日間（または `beresp.grace` で定義された期間）キャッシュから古いコンテンツと残りの TTL （デフォルトでは 1 日）を提供します。

## セイント モード

Saint モードでは、設定可能な時間、異常なバックエンドが除外されます。 その結果、Varnish をロードバランサーとして使用する場合、異常なバックエンドはトラフィックを提供できません。 Saint モードを grace モードと併用すると、異常なバックエンドサーバーを複雑に処理できるようになります。 例えば、あるバックエンドサーバーが正常でない場合、再試行は別のサーバーにルーティングされます。 他のすべてのサーバーがダウンしている場合は、古くなったキャッシュされたオブジェクトを提供します。 saint モードのバックエンド・ホストとブラックアウト期間は、`default.vcl` ファイルで定義されます。

また、Commerce サイトの可用性に影響を与えずに、メンテナンスやアップグレードを行うためにCommerce インスタンスを個別にオフラインにする場合にも、saint モードを使用できます。

### Saint モードの前提条件

1 台のマシンをプライマリインストールとして指定します。 このマシンに、Commerceのメインインスタンス、mySQL データベースおよび Varnish をインストールします。

その他のすべてのマシンでは、Commerce インスタンスがプライマリマシンの mySQL データベースにアクセスできる必要があります。 セカンダリマシンからも、プライマリ Commerce インスタンスのファイルにアクセスできます。

また、すべてのマシンで静的ファイルのバージョン管理をオフにすることもできます。 この設定には、管理者の **ストア**/設定/**設定**/**詳細**/**開発者**/**静的ファイル設定**/**静的ファイルに署名** = **いいえ** でアクセスできます。

最後に、すべてのCommerce インスタンスが実稼動モードである必要があります。 Varnish を起動する前に、各インスタンスのキャッシュをクリアします。 管理画面で、**システム** / ツール / **キャッシュ管理** に移動し、「**Magento キャッシュをフラッシュ**」をクリックします。 次のコマンドを実行してキャッシュをクリアすることもできます。

```bash
bin/magento cache:flush
```

### インストール

Saint モードはメインのワニスパッケージの一部ではありません。 これは、個別にバージョン管理される `vmod` であり、ダウンロードしてインストールする必要があります。 その結果、お使いのバージョンのワニスの [ インストール手順 ](https://varnish-cache.org/docs/index.html) に記載されているように、ソースからワニスを再コンパイルする必要があります。

再コンパイル後、Saint モード モジュールをインストールできます。 通常は、次の手順に従います。

1. [Varnish module](https://github.com/varnish/varnish-modules) からソースコードを取得します。 0.9.x バージョンにはソースコードエラーが含まれているので、Git バージョン（マスターバージョン）をクローンします。
1. 自動ツールを使用してソースコードをビルドします。

   ```bash
   sudo apt-get install libvarnishapi-dev || sudo yum install varnish-libs-devel
   ./bootstrap   # If running from git.
   ./configure
   make
   make check   # optional
   sudo make install
   ```

Saint モードのモジュールのインストールについては、[Varnish モジュール コレクション ](https://github.com/varnish/varnish-modules) を参照してください。

### サンプル VCL ファイル

次のコード例は、saint モードを有効にするために VCL ファイルに追加する必要があるコードを示しています。 `import` ステートメントと `backend` 定義をファイルの先頭に配置します。

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
