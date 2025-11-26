---
title: カタログ画像のサイズ変更のベストプラクティス
description: Adobe Commerce サイトの実稼動環境でのローンチ前にパフォーマンスの低下を防ぐ方法について説明します。
feature: Best Practices
role: Developer
exl-id: 591b1a62-bdba-4301-858a-77620ee657a9
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 0%

---

# カタログ画像のサイズ変更のベストプラクティス

すべてのカタログ画像は、ストアが実稼動環境に移行する前にサイズ変更する必要があります。 実稼動環境で事前に画像のサイズを変更しないと、ページの読み込み中に画像のサイズが強制的に変更されます。これにより、サイトの速度が大幅に低下し、起動後最初の数日から数週間でサーバーの読み込みが増加します。

## ゆっくりした道

デフォルトの CLI コマンドを使用して、すべてのイメージのサイズを変更します。

```bash
bin/magento catalog:images:resize
```

このアプローチの欠点は次のとおりです。

- プロセスはシングルスレッドです
- 既にサイズ変更された画像のサイズが変更されます
- プロセスを中断することはできません。これには数日かかる場合があります

## 速い方法

Adobe Commerce 2.4 では、非同期の画像サイズ変更が導入され、画像のサイズ変更が高速になりました。

1. すべての Web サーバーで、一時的に追加のキューハンドラーを起動します（サーバーあたりの物理プロセッサー数の 2 倍）。

   ```bsh
   for i in {1.."$((2 * `nproc --all`))"};do bin/magento queue:consumers:start media.storage.catalog.image.resize &;done;
   ```

1. キューハンドラーが実行中であることを確認します。

   ```bash
   pgrep -fl media.storage.catalog.image.resize
   ```

1. すべての画像サイズ変更リクエストでキューを埋めます。

   ```bash
   bin/magento catalog:images:resize --async
   ```

1. すべての画像のサイズが変更されたら、プロセスを終了します。

   ```bash
   pkill -f media.storage.catalog.image.resize
   ```

## 速い道

フロントエンドを使用して画像のサイズを変更する別の方法があります。

このアプローチの利点は次のとおりです。

- プロセスはマルチスレッドです
- プロセスはマルチサーバーです（複数の web ノード、ロードバランサー、`media/` ディレクトリの共有ディスク領域がある場合）
- 既にサイズ変更された画像はスキップされます

このアプローチでは 100,000 個の画像のサイズが 8 時間以内に変更されますが、CLI コマンドでは完了するまで 6 日かかります。

1. サーバーにログインします。
1. `pub/media/catalog/product` に移動して、ハッシュの 1 つ（例：0047d83143a5a3a4683afdf1116df680）をメモします。
1. 次の例では、`www.example.com` をストアのドメインに置き換え、ハッシュをメモに記載したドメインに置き換えます。

>[!BEGINTABS]

>[!TAB sed]

```bash
cd pub/
find ./media/catalog/product -path ./media/catalog/product/cache -prune -o -type f -print | sed 's~./media/catalog/product/~https://www.example.com/media/catalog/product/cache/0047d83143a5a3a4683afdf1116df680/~g' > images.txt
```

>[!TAB  包囲 ]

`siege` の欠点は、同時実行性が 10 に設定されている場合、すべての URL を 10 回訪問することです。

```bash
siege --file=./images.txt --user-agent="image-resizer" --no-follow --no-parser --concurrent=10 --reps=once
```

>[!TAB curl]

```bash
xargs -0 -n 1 -P 10 curl -X HEAD -s -w "%{http_code} %{time_starttransfer} %{url_effective}\n" < <(tr \\n \\0 <images.txt)
```

`-P` 引数は、スレッドの数を決定します。

>[!TAB bash ワンライナー ]

`find/curl` の例では、画像が置かれている同じマシンから `curl` を実行できる場合の 1 つのライナーです。

```bash
find ./media/catalog/product -path ./media/catalog/product/cache -prune -o -type f -print | sed 's~./media/catalog/product/~https://www.example.com/media/catalog/product/cache/0047d83143a5a3a4683afdf1116df680/~g' | xargs -n 1 -P 10 curl -X HEAD -s -w "%{http_code} %{time_starttransfer} %{url_effective}\n"
```

先ほどと同様に、`www.example.com` を web サイトのドメインに置き換え、`-P` を、サーバーがクラッシュすることなく処理できるスレッドの数に設定します。

>[!ENDTABS]

出力では、ストア内のすべての製品画像のリストが返されます。 使用可能なすべてのサーバーとプロセッサーコアを使用して（`siege` またはその他のクローラを使用して）画像をクロールし、他の方法よりも大幅に高速にサイズ変更キャッシュを生成できます。

1 つの画像キャッシュ URL にアクセスすると、画像がまだ存在しない場合は、バックグラウンドですべての画像サイズが生成されます。 また、既にサイズ変更されたファイルはスキップされます。

>[!NOTE]
>
>- クラウドインフラストラクチャプロジェクトのAdobe Commerceでは、商品の画像のサイズ変更を Fastly サービスに任せることができます。 [&#x200B; クラウドガイド &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization.html#deep-image-optimization) の _ディープ画像の最適化_ を参照してください。
>- リモートストレージモジュールを使用する場合は、画像のサイズ変更を nginx にオフロードすることもできます。 [&#x200B; 構成ガイド &#x200B;](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/storage/remote-storage/remote-storage-image-resize.html) の「リモート・ストレージの画像サイズ変更の構成 _を参照_。
