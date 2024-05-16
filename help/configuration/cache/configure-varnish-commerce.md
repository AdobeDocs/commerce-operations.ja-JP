---
title: Commerce用ワニスの設定
description: Commerce アプリケーションの Varnish 設定ファイルを更新および管理する方法について説明します。
feature: Configuration, Cache, SCD
exl-id: 6c007ff9-493f-4df2-b7b4-438b41fd7e37
source-git-commit: 602a1ef82fcb8d30ff027db0fe0aacb981c7e08e
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# Varnish を使用するように Commerce アプリケーションを設定する

Varnish を使用するようにCommerceを設定するには：

1. 管理者として管理者にログインします。
1. クリック **[!UICONTROL Stores]** > 設定 > **設定** > **詳細** > **システム** > **フルページキャッシュ**.
1. から **[!UICONTROL Caching Application]** リスト、クリック **ワニスのキャッシュ**.
1. に値を入力 **[!UICONTROL TTL for public content]** フィールド。
1. を展開 **[!UICONTROL Varnish Configuration]** さらに、次の情報を入力します。

   | フィールド | 説明 |
   | ----- | ----------- |
   | アクセスリスト | 完全修飾ホスト名、IP アドレス、または [クラスレスドメイン間ルーティング（CIDR）](https://www.digitalocean.com/community/tutorials/understanding-ip-addresses-subnets-and-cidr-notation-for-networking) 表記法コンテンツを無効にする IP アドレス範囲。 参照： [Varnish キャッシュのパージ](https://varnish-cache.org/docs/3.0/tutorial/purging.html). |
   | バックエンドホスト | Varnish の完全修飾ホスト名または IP アドレスとリスニングポートを入力します _バックエンド_ または _公開元サーバー_&#x200B;つまり、コンテンツ Varnish を提供するサーバーが加速します。 通常、これは web サーバーです。 参照： [Varnish キャッシュ バックエンド サーバー](https://www.varnish-cache.org/docs/trunk/users-guide/vcl-backends.html). |
   | バックエンドポート | オリジンサーバーのリッスンポート。 |
   | 猶予期間 | バックエンドが応答しない場合に、ワニスが古いコンテンツを提供する期間を決定します。 デフォルト値は 300 秒です。 |
   | パラメータサイズを処理 | の最大数を指定します [レイアウトハンドル](https://developer.adobe.com/commerce/frontend-core/guide/layouts/#layout-handles) でを処理します [`{BASE-URL}/page_cache/block/esi`](use-varnish-esi.md) フルページキャッシュの HTTP エンドポイント。 サイズを制限すると、セキュリティとパフォーマンスが向上する可能性があります。 デフォルトは 100 です。 |

1. クリック **設定を保存**.

C のコマンドラインインターフェイスツールを使用して、Admin にログインする代わりに、コマンドラインから Varnish をアクティブ化することもできます。

```bash
bin/magento config:set --scope=default --scope-code=0 system/full_page_cache/caching_application 2
```

## Varnish 設定ファイルをエクスポートする

管理者から Varnish 設定ファイルをエクスポートするには、次の手順に従います。

1. エクスポートボタンのいずれかをクリックして、 `varnish.vcl` あなたはワニスで使うことができます。

   たとえば、Varnish 4 がある場合は、 **Varnish 4 用 VCL をエクスポートする**

   次の図に例を示します。

   ![管理者で Varnish を使用するようにCommerceを設定します。](../../assets/configuration/varnish-admin-22.png)

1. 既存のものをバックアップ `default.vcl`. 次に、の名前を `varnish.vcl` 書き出したファイル `default.vcl`. 次に、ファイルをにコピーします `/etc/varnish/` ディレクトリ。

   ```bash
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak2
   ```

   ```bash
   mv <download_directory>/varnish.vcl default.vcl
   ```

   ```bash
   cp <download_directory>/default.vcl /etc/varnish/default.vcl
   ```

1. Adobeでは、を開くことを推奨しています `default.vcl` の値を変更します。 `acl purge` を Varnish ホストの IP アドレスに追加します。 （複数のホストを別々の行に指定することも、CIDR 表記を使用することもできます）。

   以下に例を挙げます。

   ```conf
    acl purge {
       "localhost";
    }
   ```

1. Vagrant ヘルスチェック、猶予モードまたは saint モードの設定をカスタマイズする場合は、以下を参照してください [高度なワニス設定](config-varnish-advanced.md).

1. Varnish と Web サーバーを再起動します。

   ```bash
   service varnish restart
   ```

   ```bash
   service httpd restart
   ```

## 静的ファイルをキャッシュ

静的ファイルはデフォルトではキャッシュすべきではありませんが、静的ファイルをキャッシュする場合は、セクションを編集できます `Static files caching` VCL に次の内容を含めます。

```conf
# Static files should not be cached by default
  return (pass);

# But if you use a few locales and do not use CDN you can enable caching static files by commenting previous line (#return (pass);) and uncommenting next 3 lines
  #unset req.http.Https;
  #unset req.http./* {{ ssl_offloaded_header }} */;
  #unset req.http.Cookie;
```

Commerceで Varnish を使用するように設定する前に、これらの変更を行う必要があります。
