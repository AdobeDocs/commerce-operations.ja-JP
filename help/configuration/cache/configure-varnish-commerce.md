---
title: コマース用の Vanrish の設定
description: Commerce アプリケーションの Vanrish 構成ファイルを更新および管理する方法を説明します。
feature: Configuration, Cache, SCD
exl-id: 6c007ff9-493f-4df2-b7b4-438b41fd7e37
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# Vanish を使用するように Commerce アプリケーションを設定する

Vanish を使用するように Commerce を設定するには：

1. 管理者として管理者にログインします。
1. クリック **[!UICONTROL Stores]** /設定/ **設定** > **詳細** > **システム** > **フルページキャッシュ**.
1. 次の **[!UICONTROL Caching Application]** リスト、クリック **ワニスのキャッシュ**.
1. 値を **[!UICONTROL TTL for public content]** フィールドに入力します。
1. 展開 **[!UICONTROL Varnish Configuration]** 次の情報を入力します。

   | フィールド | 説明 |
   | ----- | ----------- |
   | アクセスリスト | 完全修飾ホスト名、IP アドレス、または [クラスレスドメイン間ルーティング (CIDR)](https://www.digitalocean.com/community/tutorials/understanding-ip-addresses-subnets-and-cidr-notation-for-networking) 表記法コンテンツを無効にする IP アドレス範囲。 詳しくは、 [ワニスキャッシュのパージ](https://varnish-cache.org/docs/3.0/tutorial/purging.html). |
   | バックエンドホスト | 完全修飾ホスト名または IP アドレスを入力し、Vanish のリッスンポートを入力します。 _バックエンド_ または _接触元サーバー_;つまり、Vanish コンテンツを提供するサーバが高速化します。 通常、これは Web サーバーです。 詳しくは、 [Vanish キャッシュバックエンドサーバ](https://www.varnish-cache.org/docs/trunk/users-guide/vcl-backends.html). |
   | バックエンドポート | オリジンサーバーのリスンポート。 |
   | 猶予期間 | バックエンドが応答しない場合に Vanrish が古いコンテンツを提供する時間は、猶予期間によって決まります。 デフォルト値は 300 秒です。 |

1. クリック **設定を保存**.

また、C コマンドラインインターフェイスツールを使用して、管理者にログインする代わりに、コマンドラインから Vanrish をアクティブにすることもできます。

```bash
bin/magento config:set --scope=default --scope-code=0 system/full_page_cache/caching_application 2
```

## Vanish 設定ファイルを書き出す

Vanish 構成ファイルを管理から書き出すには、次の手順に従います。

1. 書き出しボタンの 1 つをクリックして、 `varnish.vcl` ワニスと併用できます。

   たとえば、Vanish 4 がある場合は、 **VCL を Vanish 4 用に書き出し**

   次の図に例を示します。

   ![Commerce を設定して管理で Vanish を使用する](../../assets/configuration/varnish-admin-22.png)

1. 既存のバックアップ `default.vcl`. 次に、 `varnish.vcl` 先ほどに書き出したファイル `default.vcl`. 次に、 `/etc/varnish/` ディレクトリ。

   ```bash
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak2
   ```

   ```bash
   mv <download_directory>/varnish.vcl default.vcl
   ```

   ```bash
   cp <download_directory>/default.vcl /etc/varnish/default.vcl
   ```

1. Adobeが開くことをお勧めします `default.vcl` をクリックし、 `acl purge` を Vanish ホストの IP アドレスに追加します。 （複数のホストを別々の行で指定することも、 CIDR 表記を使用することもできます）。

   例：

   ```conf
    acl purge {
       "localhost";
    }
   ```

1. Vagrant ヘルスチェック、猶予モード、または SAINT モードの設定をカスタマイズする場合は、 [高度なワニス構成](config-varnish-advanced.md).

1. Vanish と Web サーバーを再起動します。

   ```bash
   service varnish restart
   ```

   ```bash
   service httpd restart
   ```

## 静的ファイルをキャッシュ

静的ファイルは、デフォルトではキャッシュされませんが、キャッシュする場合は、「 」セクションを編集できます `Static files caching` VCL 内に次の内容を含める：

```conf
# Static files should not be cached by default
  return (pass);

# But if you use a few locales and do not use CDN you can enable caching static files by commenting previous line (#return (pass);) and uncommenting next 3 lines
  #unset req.http.Https;
  #unset req.http./* {{ ssl_offloaded_header }} */;
  #unset req.http.Cookie;
```

Commerce で Vanrish を使用するように設定する前に、これらの変更を行う必要があります。
