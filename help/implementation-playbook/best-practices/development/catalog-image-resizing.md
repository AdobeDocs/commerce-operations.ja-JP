---
title: カタログ画像のサイズ変更のベストプラクティス
description: Adobe Commerce サイトの本番環境のローンチ前に、パフォーマンスの低下を防ぐ方法について説明します。
feature: Best Practices
role: Developer
exl-id: 591b1a62-bdba-4301-858a-77620ee657a9
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 0%

---

# カタログ画像のサイズ変更のベストプラクティス

ストアを本番環境に導入する前に、あらゆるカタログ画像のサイズを変更する必要があります。 本番環境に導入する前に画像のサイズを変更しないと、ページの読み込み中に画像のサイズが変更されるため、サイトの読み込み速度が大幅に低下し、導入後の最初の数日から数週間でサーバーの読み込みが増加します。

## ザ・スローウェイ

デフォルトのCLI コマンドを使用して、すべてのイメージのサイズを変更します。

```shell
bin/magento catalog:images:resize
```

このアプローチの欠点は、次のとおりです。

- このプロセスはシングルスレッドです
- 既にサイズ変更されている画像は、プロセスによってサイズ変更されます
- プロセスを中断することはできません。これには数日かかる場合があります

## より高速な方法

Adobe Commerce 2.4では、非同期画像のサイズ変更が導入され、画像のサイズ変更を高速に行えるようになりました。

1. 各web サーバーで、一時的にいくつかの追加のキューハンドラーを開始します（サーバーあたりの物理プロセッサ数の2倍）。

   ```bsh
   for i in {1.."$((2 * `nproc --all`))"};do bin/magento queue:consumers:start media.storage.catalog.image.resize &;done;
   ```

1. キューハンドラーが実行されていることを確認します。

   ```shell
   pgrep -fl media.storage.catalog.image.resize
   ```

1. 画像のサイズ変更リクエストをすべてキューに入力します。

   ```shell
   bin/magento catalog:images:resize --async
   ```

1. すべての画像のサイズを変更したら、プロセスを終了します。

   ```shell
   pkill -f media.storage.catalog.image.resize
   ```

## 迅速な方法

フロントエンドを使用して画像のサイズを変更する別の方法があります。

このアプローチの利点は次のとおりです。

- プロセスはマルチスレッドです
- プロセスはマルチサーバーです（複数のweb ノードがある場合は、ロードバランサーと、`media/` ディレクトリの共有ディスク領域）
- 既にサイズ変更済みの画像はスキップされます

この方法では、100,000個の画像のサイズを8時間未満で変更しますが、CLI コマンドの完了には6日かかります。

1. サーバーにログインします。
1. `pub/media/catalog/product`に移動し、いずれかのハッシュをメモします（例：0047d83143a5a3a4683afdf1116df680）。
1. 次の例では、`www.example.com`をストアのドメインに置き換え、ハッシュをメモしたドメインに置き換えます。

>[!BEGINTABS]

>[!TAB sed]

```shell
cd pub/
find ./media/catalog/product -path ./media/catalog/product/cache -prune -o -type f -print | sed 's~./media/catalog/product/~https://www.example.com/media/catalog/product/cache/0047d83143a5a3a4683afdf1116df680/~g' > images.txt
```

>[!TAB 包囲戦]

`siege`の欠点は、同時実行が10に設定されている場合、10回以内にすべてのURLにアクセスすることです。

```shell
siege --file=./images.txt --user-agent="image-resizer" --no-follow --no-parser --concurrent=10 --reps=once
```

>[!TAB curl]

```shell
xargs -0 -n 1 -P 10 curl -X HEAD -s -w "%{http_code} %{time_starttransfer} %{url_effective}\n" < <(tr \\n \\0 <images.txt)
```

`-P`引数によってスレッドの数が決まります。

>[!TAB ワンライナーをバッシュ]

`find/curl`の例の1行目。画像が存在するのと同じコンピューターから`curl`を実行できる場合に使用します。

```shell
find ./media/catalog/product -path ./media/catalog/product/cache -prune -o -type f -print | sed 's~./media/catalog/product/~https://www.example.com/media/catalog/product/cache/0047d83143a5a3a4683afdf1116df680/~g' | xargs -n 1 -P 10 curl -X HEAD -s -w "%{http_code} %{time_starttransfer} %{url_effective}\n"
```

繰り返しますが、`www.example.com`をweb サイトのドメインに置き換え、`-P`をクラッシュせずにサーバーが処理できるスレッド数に設定します。

>[!ENDTABS]

出力は、ストア内のすべての商品画像のリストを返します。 利用可能なすべてのサーバーとプロセッサーのコアを使用して、画像（`siege`またはその他のweb クローラー）をクロールし、サイズ変更キャッシュを他のアプローチよりも大幅に高速で生成できます。

1つの画像キャッシュ URLにアクセスすると、画像がまだ存在しない場合は、すべての画像サイズがバックグラウンドで生成されます。 また、既にサイズが変更されているファイルはスキップされます。

>[!NOTE]
>
>- Adobe Commerceのクラウドインフラプロジェクトでは、Fastly サービスに商品イメージのサイズ変更をオフロードできます。 _クラウドガイド_&#x200B;の[深層画像最適化](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization.html#deep-image-optimization)を参照してください。
>- リモートストレージモジュールを使用する場合は、画像のサイズをnginxにオフロードすることもできます。 _設定ガイド_&#x200B;の「[&#x200B; リモートストレージ用の画像サイズ変更の設定](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/storage/remote-storage/remote-storage-image-resize.html)」を参照してください。
