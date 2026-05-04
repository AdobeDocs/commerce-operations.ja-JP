---
title: Commerce用Varnishの設定
description: Adobe Commerce アプリケーションに特化したVarnishの設定方法を説明します。 設定ファイルの更新と管理手法について説明します。
feature: Configuration, Cache, SCD
exl-id: 6c007ff9-493f-4df2-b7b4-438b41fd7e37
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# Varnishを使用するようにCommerce アプリケーションを設定する

Varnishを使用するようにCommerceを設定するには：

1. 管理者としてAdminにログインします。
1. **[!UICONTROL Stores]** / 設定/ **設定** / **詳細** / **システム** / **フルページキャッシュ**&#x200B;をクリックします。
1. **[!UICONTROL Caching Application]** リストから、**Varnish Caching**&#x200B;をクリックします。
1. **[!UICONTROL TTL for public content]** フィールドに値を入力します。
1. **[!UICONTROL Varnish Configuration]**&#x200B;を展開し、次の情報を入力します。

   | フィールド | 説明 |
   | ----- | ----------- |
   | アクセスリスト | コンテンツを無効にする完全修飾ホスト名、IP アドレス、または[&#x200B; クラスレス ドメイン間ルーティング （CIDR） &#x200B;](https://www.digitalocean.com/community/tutorials/understanding-ip-addresses-subnets-and-cidr-notation-for-networking)表記法IP アドレス範囲を入力します。 [&#x200B; ニス キャッシュ パージ &#x200B;](https://varnish-cache.org/docs/3.0/tutorial/purging.html)を参照してください。 |
   | バックエンドホスト | Varnish _バックエンド_&#x200B;または&#x200B;_オリジンサーバー_&#x200B;の完全修飾ホスト名またはIP アドレスとリッスポートを入力します。つまり、コンテンツ Varnishを提供するサーバーが高速化します。 通常、これはあなたのweb サーバーです。 [Varnish キャッシュバックエンドサーバー](https://www.varnish-cache.org/docs/trunk/users-guide/vcl-backends.html)を参照してください。 |
   | バックエンドポート | オリジンサーバーのリッスンポート。 |
   | 猶予期間 | バックエンドがレスポンシブでない場合に、Varnishが古いコンテンツを提供する時間を決定します。 デフォルト値は300秒です。 |
   | パラメーターのサイズを処理します | フルページキャッシュ用に[`{BASE-URL}/page_cache/block/esi`](use-varnish-esi.md) HTTP エンドポイントで処理する[&#x200B; レイアウトハンドル &#x200B;](https://developer.adobe.com/commerce/frontend-core/guide/layouts/#layout-handles)の最大数を指定します。 サイズを制限すると、セキュリティとパフォーマンスが向上します。 デフォルトは100です。 |

1. 「**設定を保存**」をクリックします。

また、C コマンドラインインターフェイスツールを使用して、管理者にログインする代わりに、コマンドラインからVarnishをアクティベートすることもできます。

```shell
bin/magento config:set --scope=default --scope-code=0 system/full_page_cache/caching_application 2
```

## Varnish設定ファイルの書き出し

管理者からVarnish設定ファイルを書き出すには：

1. Varnishで使用できる`varnish.vcl`を作成するには、いずれかの書き出しボタンをクリックします。

   例えば、Varnish 4がある場合、「**VCLをVarnish 4**&#x200B;用に書き出し」をクリックします

   次の図は、例を示しています。

   ![管理者でVarnishを使用するようにCommerceを設定](../../assets/configuration/varnish-admin-22.png)

1. 既存の`default.vcl`をバックアップします。 次に、`default.vcl`に書き出した`varnish.vcl` ファイルの名前を変更します。 次に、ファイルを`/etc/varnish/` ディレクトリにコピーします。

   ```shell
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak2
   ```

   ```shell
   mv <download_directory>/varnish.vcl default.vcl
   ```

   ```shell
   cp <download_directory>/default.vcl /etc/varnish/default.vcl
   ```

1. Adobeでは、`default.vcl`を開き、`acl purge`の値をVarnish ホストのIP アドレスに変更することをお勧めします。 （複数のホストを別々の行に指定することも、CIDR表記を使用することもできます）。

   以下に例を挙げます。

   ```conf
    acl purge {
       "localhost";
    }
   ```

1. Vagrant ヘルスチェック、猶予モードまたはsaint モード設定をカスタマイズする場合は、[高度なVarnish設定](config-varnish-advanced.md)を参照してください。

1. Varnishとweb サーバーを再起動します。

   ```shell
   service varnish restart
   ```

   ```shell
   service httpd restart
   ```

## 静的ファイルをキャッシュ

静的ファイルはデフォルトではキャッシュされませんが、キャッシュする場合は、VCLのセクション `Static files caching`を編集して、次のコンテンツを得ることができます。

```conf
# Static files should not be cached by default
  return (pass);

# But if you use a few locales and do not use CDN you can enable caching static files by commenting previous line (#return (pass);) and uncommenting next 3 lines
  #unset req.http.Https;
  #unset req.http./* {{ ssl_offloaded_header }} */;
  #unset req.http.Cookie;
```

Varnishを使用するようにCommerceを設定する前に、これらの変更を行う必要があります。
