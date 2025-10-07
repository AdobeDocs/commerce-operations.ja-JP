---
title: Commerce用ワニスの設定
description: Adobe Commerce アプリケーション専用にワニスを設定する方法を説明します。 設定ファイルのアップデートと管理手法について説明します。
feature: Configuration, Cache, SCD
exl-id: 6c007ff9-493f-4df2-b7b4-438b41fd7e37
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# Varnish を使用するようにCommerce アプリケーションを設定します。

Varnish を使用するようにCommerceを設定するには：

1. 管理者として管理者にログインします。
1. **[!UICONTROL Stores]**/設定/**設定**/**詳細**/**システム**/**フルページキャッシュ** をクリックします。
1. **[!UICONTROL Caching Application]** リストから、**Varnish Caching** をクリックします。
1. **[!UICONTROL TTL for public content]** フィールドに値を入力します。
1. **[!UICONTROL Varnish Configuration]** を展開し、次の情報を入力します。

   | フィールド | 説明 |
   | ----- | ----------- |
   | アクセスリスト | コンテンツを無効にする完全修飾ホスト名、IP アドレス、または [Classless Inter-domain Routing （CIDR） ](https://www.digitalocean.com/community/tutorials/understanding-ip-addresses-subnets-and-cidr-notation-for-networking) 表記の IP アドレス範囲を入力します。 [Varnish キャッシュのパージ ](https://varnish-cache.org/docs/3.0/tutorial/purging.html) を参照してください。 |
   | バックエンドホスト | Varnish _バックエンド_ または _オリジンサーバー_ の完全修飾ホスト名または IP アドレスとリッスンポートを入力します。つまり、Varnish が加速するコンテンツを提供するサーバーです。 通常、これは web サーバーです。 [Varnish キャッシュバックエンドサーバー ](https://www.varnish-cache.org/docs/trunk/users-guide/vcl-backends.html) を参照してください。 |
   | バックエンドポート | オリジンサーバーのリッスンポート。 |
   | 猶予期間 | バックエンドが応答しない場合に、ワニスが古いコンテンツを提供する期間を決定します。 デフォルト値は 300 秒です。 |
   | パラメータサイズを処理 | フルページキャッシュ用に [ HTTP エンドポイントで処理する ](https://developer.adobe.com/commerce/frontend-core/guide/layouts/#layout-handles) レイアウトハンドル [`{BASE-URL}/page_cache/block/esi`](use-varnish-esi.md) の最大数を指定します。 サイズを制限すると、セキュリティとパフォーマンスが向上する可能性があります。 デフォルトは 100 です。 |

1. 「**設定を保存**」をクリックします。

C のコマンドラインインターフェイスツールを使用して、Admin にログインする代わりに、コマンドラインから Varnish をアクティブ化することもできます。

```bash
bin/magento config:set --scope=default --scope-code=0 system/full_page_cache/caching_application 2
```

## Varnish 設定ファイルをエクスポートする

管理者から Varnish 設定ファイルをエクスポートするには、次の手順に従います。

1. いずれかの書き出しボタンをクリックして、Varnish で使用できる `varnish.vcl` を作成します。

   たとえば、Varnish 4 がある場合は、[**Varnish 4 の VCL を書き出す**] をクリックします

   次の図に例を示します。

   ![Admin で Varnish を使用するようにCommerceを設定する ](../../assets/configuration/varnish-admin-22.png)

1. 既存の `default.vcl` をバックアップします。 次に、`varnish.vcl` に書き出した `default.vcl` ファイルの名前を変更します。 次に、ファイルを `/etc/varnish/` ディレクトリにコピーします。

   ```bash
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak2
   ```

   ```bash
   mv <download_directory>/varnish.vcl default.vcl
   ```

   ```bash
   cp <download_directory>/default.vcl /etc/varnish/default.vcl
   ```

1. Adobeでは、`default.vcl` を開き、`acl purge` の値を Varnish ホストの IP アドレスに変更することをお勧めします。 （複数のホストを別々の行に指定することも、CIDR 表記を使用することもできます）。

   以下に例を挙げます。

   ```conf
    acl purge {
       "localhost";
    }
   ```

1. Vagrant ヘルスチェック、猶予モードまたは saint モードの設定をカスタマイズする場合は、[ 高度な Varnish 設定 ](config-varnish-advanced.md) を参照してください。

1. Varnish と Web サーバーを再起動します。

   ```bash
   service varnish restart
   ```

   ```bash
   service httpd restart
   ```

## 静的ファイルをキャッシュ

静的ファイルはデフォルトではキャッシュしてはいけませんが、静的ファイルをキャッシュする場合は、VCL の `Static files caching` のセクションを編集して、次の内容を指定できます。

```conf
# Static files should not be cached by default
  return (pass);

# But if you use a few locales and do not use CDN you can enable caching static files by commenting previous line (#return (pass);) and uncommenting next 3 lines
  #unset req.http.Https;
  #unset req.http./* {{ ssl_offloaded_header }} */;
  #unset req.http.Cookie;
```

Commerceで Varnish を使用するように設定する前に、これらの変更を行う必要があります。
