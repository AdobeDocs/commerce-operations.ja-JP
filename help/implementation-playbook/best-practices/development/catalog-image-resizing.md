---
title: カタログ画像のサイズ変更のベストプラクティス
description: Adobe Commerce サイトの実稼動環境でのローンチ前にパフォーマンスの低下を防ぐ方法について説明します。
feature: Best Practices
role: Developer
exl-id: 591b1a62-bdba-4301-858a-77620ee657a9
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
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
- プロセスはマルチサーバーです（複数の web ノードがある場合、ロードバランサー、およびの共有ディスク領域） `media/` ディレクトリ）
- 既にサイズ変更された画像はスキップされます

このアプローチでは 100,000 個の画像のサイズが 8 時間以内に変更されますが、CLI コマンドでは完了するまで 6 日かかります。

1. サーバーにログインします。
1. に移動します。 `pub/media/catalog/product` また、ハッシュの 1 つ（例：0047d83143a5a3a4683afdf1116df680）をメモします。
1. 次の例では、を置換します `www.example.com` をストアのドメインに置き換え、ハッシュをメモしたハッシュに置き換えます。

>[!BEGINTABS]

>[!TAB sed]

```bash
cd pub/
find ./media/catalog/product -path ./media/catalog/product/cache -prune -o -type f -print | sed 's~./media/catalog/product/~https://www.example.com/media/catalog/product/cache/0047d83143a5a3a4683afdf1116df680/~g' > images.txt
```

>[!TAB 包囲攻撃]

欠点 `siege` 同時実行性が 10 に設定されている場合、すべての URL を 10 回訪問するということです。

```bash
siege --file=./images.txt --user-agent="image-resizer" --no-follow --no-parser --concurrent=10 --reps=once
```

>[!TAB curl]

```bash
xargs -0 -n 1 -P 10 curl -X HEAD -s -w "%{http_code} %{time_starttransfer} %{url_effective}\n" < <(tr \\n \\0 <images.txt)
```

この `-P` 引数は、スレッドの数を決定します。

>[!TAB 単行車を引っ張る]

～のための一等船 `find/curl` 例えば、次を実行できる場合 `curl` 画像が置かれている同じマシンから：

```bash
find ./media/catalog/product -path ./media/catalog/product/cache -prune -o -type f -print | sed 's~./media/catalog/product/~https://www.example.com/media/catalog/product/cache/0047d83143a5a3a4683afdf1116df680/~g' | xargs -n 1 -P 10 curl -X HEAD -s -w "%{http_code} %{time_starttransfer} %{url_effective}\n"
```

この場合も、 `www.example.com` Web サイトのドメインとの連携 `-P` サーバーがクラッシュせずに処理できるスレッドの数に制限します。

>[!ENDTABS]

出力では、ストア内のすべての製品画像のリストが返されます。 イメージをクロールできます（次を使用） `siege` または、その他のクローラ）を使用して、使用可能なすべてのサーバーとプロセッサコアを使用し、他の方法よりも大幅に高速にサイズ変更キャッシュを生成します。

1 つの画像キャッシュ URL にアクセスすると、画像がまだ存在しない場合は、バックグラウンドですべての画像サイズが生成されます。 また、既にサイズ変更されたファイルはスキップされます。

>[!NOTE]
>
>- クラウドインフラストラクチャプロジェクトのAdobe Commerceでは、商品の画像のサイズ変更を Fastly サービスに任せることができます。 参照： [深みのある画像の最適化](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization.html?lang=en#deep-image-optimization) が含まれる _クラウドガイド_.
>- リモートストレージモジュールを使用する場合は、画像のサイズ変更を nginx にオフロードすることもできます。 参照： [リモートストレージの画像のサイズ変更の設定](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/storage/remote-storage/remote-storage-image-resize.html) が含まれる _設定ガイド_.
