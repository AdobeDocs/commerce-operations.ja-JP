---
title: 高度なワニス構成
description: ヘルスチェック、猶予、SAINT モードなど、高度な Vanrish 機能を設定します。
feature: Configuration, Cache
exl-id: 178bd675-6ed0-40cc-9455-08a11b32c054
source-git-commit: ec3ab7e3c6c3835e73653b0d4f74aadc861016d3
workflow-type: tm+mt
source-wordcount: '871'
ht-degree: 0%

---

# 高度なワニス構成

Vanish は、コマースサーバーが正しく機能していない場合に、顧客が長時間の遅延やタイムアウトを経験するのを防ぐいくつかの機能を提供します。 これらの機能は、 `default.vcl` ファイル。 このトピックでは、Commerce が管理からダウンロードする VCL (Varnish Configuration Language) ファイルに追加する機能について説明します。

詳しくは、 [ワニスリファレンスマニュアル](https://varnish-cache.org/docs/index.html) を参照してください。

## ヘルスチェック

Vanish ヘルスチェック機能は、コマースサーバーをポーリングして、応答がタイムリーに行われているかどうかを判断します。 正常に応答している場合は、有効期間 (TTL) が切れた後に新しいコンテンツが再生成されます。 そうでない場合、Vanish は常に古いコンテンツを提供します。

Commerce では、次のデフォルトのヘルスチェックが定義されます。

```conf
.probe = {
    .url = "/pub/health_check.php";
    .timeout = 2s;
    .interval = 5s;
    .window = 10;
    .threshold = 5;
    }
```

5 秒ごとに、このヘルスチェックが `pub/health_check.php` スクリプト。 このスクリプトは、サーバー、各データベース、Redis（インストールされている場合）の可用性を確認します。 スクリプトは、2 秒以内に応答を返す必要があります。 スクリプトは、これらのリソースのいずれかが停止していると判断した場合、500 HTTP エラーコードを返します。 このエラーコードが 10 回に 1 回の試行のうち 6 回受信された場合、バックエンドは異常と見なされます。

The `health_check.php` スクリプトは、 `pub` ディレクトリ。 コマースルートディレクトリが `pub`を変更した場合は、必ず `url` パラメーターから `/pub/health_check.php` から `health_check.php`.

詳しくは、 [ワニスのヘルスチェック](https://varnish-cache.org/docs/7.4/users-guide/vcl-backends.html#health-checks) ドキュメント。

## 猶予モード

猶予モードを使用すると、Vanish は TTL 値を超えてオブジェクトをキャッシュに保持できます。 Vanish は、新しいバージョンを取得する間、期限切れ（古い）コンテンツを提供できます。 これにより、トラフィックの流れが向上し、読み込み時間が短縮されます。 これは、次の状況で使用されます。

- Commerce バックエンドが正常で、リクエストが通常より長くかかっている場合。
- Commerce バックエンドが正常でない場合。

The `vcl_hit` サブルーチンは、キャッシュされたオブジェクトの要求に対する Vanish の応答を定義します。

### Commerce バックエンドが正常な場合

ヘルスチェックがコマースバックエンドが正常であると判断した場合、Vanrish は猶予期間に残っている時間を確認します。 デフォルトの猶予期間は 300 秒ですが、マーチャントは管理者から値を設定できます ( [Vanish を使用するように Commerce を設定する](configure-varnish-commerce.md). 猶予期間が期限切れになっていない場合、Vanrish は古いコンテンツを配信し、Commerce サーバーからオブジェクトを非同期的に更新します。 猶予期間が終了した場合、Vanrish は古いコンテンツを提供し、Commerce バックエンドからオブジェクトを同期的に更新します。

Vanish が古いオブジェクトを提供する最大時間は、猶予期間（デフォルトでは 300 秒）と TTL 値 ( デフォルトでは86400秒 ) の合計です。

デフォルトの猶予期間を `default.vcl` ファイルを編集する場合は、 `vcl_hit` サブルーチン：

```conf
if (obj.ttl + 300s > 0s) {
```

### Commerce のバックエンドが正常でない場合

Commerce バックエンドが応答しない場合、Vanrish は 3 日間 ( または `beresp.grace`) に残りの TTL（デフォルトでは 1 日）を加えたもの（キャッシュされたコンテンツが手動でパージされない限りは 1 日）です。

## SAINT モード

SAINT モードでは、異常なバックエンドは設定可能な時間だけ除外されます。 その結果、Vanish をロードバランサーとして使用する場合、異常なバックエンドはトラフィックを処理できません。 SAINT モードを猶予モードと共に使用すると、異常なバックエンドサーバーを複雑に処理できます。 例えば、あるバックエンドサーバーが異常な場合、再試行を別のサーバーにルーティングすることができます。 その他のすべてのサーバーがダウンした場合は、キャッシュされた古いオブジェクトを提供します。 SAINT モードのバックエンドホストとブラックアウト期間は、 `default.vcl` ファイル。

コマースインスタンスが個別にオフラインになっている場合にも、SAINT モードを使用して、コマースサイトの可用性に影響を与えることなく、メンテナンスタスクやアップグレードタスクを実行できます。

### SAINT モードの前提条件

1 台のマシンをプライマリインストールとして指定します。 このマシンに、Commerce、mySQL データベース、および Vanish のメインインスタンスをインストールします。

その他のすべてのマシンでは、コマースインスタンスがプライマリマシンの mySQL データベースにアクセスできる必要があります。 また、セカンダリコンピューターは、プライマリ Commerce インスタンスのファイルにもアクセスできる必要があります。

または、すべてのマシンで静的ファイルのバージョン管理をオフにすることもできます。 これには、以下の管理者からアクセスできます。 **ストア** /設定/ **設定** > **詳細** > **開発者** > **静的ファイル設定** > **静的ファイルに署名** = **いいえ**.

最後に、すべてのコマースインスタンスは実稼動モードである必要があります。 Vanish を起動する前に、各インスタンスのキャッシュをクリアします。 管理者で、に移動します。 **システム** /ツール/ **キャッシュ管理** をクリックします。 **フラッシュMagentoキャッシュ**. 次のコマンドを実行して、キャッシュをクリアすることもできます。

```bash
bin/magento cache:flush
```

### インストール

SAINT モードは、メインの Vanrish パッケージに含まれていません。 個別にバージョン管理される `vmod` をダウンロードしてインストールする必要があります。 その結果、ソースから Vanrish を再コンパイルする必要があります。 [インストール手順](https://varnish-cache.org/docs/index.html) あなたのバージョンの Vanrish のために。

再コンパイル後に、Saint モードモジュールをインストールできます。 一般に、次の手順に従います。

1. ソースコードの取得元 [ワニスモジュール](https://github.com/varnish/varnish-modules). 0.9.x バージョンにソースコードエラーが含まれているので、Git バージョン（マスターバージョン）を複製します。
1. autotools を使用してソースコードを作成します。

   ```bash
   sudo apt-get install libvarnishapi-dev || sudo yum install varnish-libs-devel
   ./bootstrap   # If running from git.
   ./configure
   make
   make check   # optional
   sudo make install
   ```

詳しくは、 [Vanish モジュールの収集](https://github.com/varnish/varnish-modules) を参照してください。

### サンプル VCL ファイル

以下のコードの例は、VCL ファイルに追加して saint モードを有効にする必要があるコードを示しています。 を `import` ステートメントと `backend` 定義を参照してください。

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
