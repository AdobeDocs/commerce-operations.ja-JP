---
title: カタログ画像のサイズ変更のベストプラクティス
description: Adobe Commerceサイトを実稼動環境で起動する前に、パフォーマンスの低下を防ぐ方法を説明します。
feature: Best Practices
role: Developer
source-git-commit: 94d37b6a95cae93f465daf8eb96363a198833e27
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---


# カタログ画像のサイズ変更のベストプラクティス

すべてのカタログ画像は、ストアが実稼動環境に移行する前にサイズ変更する必要があります。 実稼動前に画像のサイズ変更に失敗すると、ページの読み込み中に画像のサイズ変更が強制され、サイトの速度が大幅に低下し、起動後の最初の日から数週間でサーバーの読み込みが増加します。

## 遅い道

デフォルトの CLI コマンドを使用して、すべての画像のサイズを変更します。

```bash
bin/magento catalog:images:resize
```

このアプローチのデメリットは次のとおりです。

- プロセスはシングルスレッドです。
- プロセスは、既にサイズ変更された画像のサイズを変更します
- プロセスを中断できないので、数日かかる場合があります

## 速い道

非同期的な画像のサイズ変更がAdobe Commerce 2.4 で導入され、画像のサイズ変更を高速化できました。

1. すべての Web サーバで、追加のキューハンドラを一時的に起動します（サーバあたりの物理プロセッサの数の 2 倍）。

   ```bsh
   for i in {1.."$((2 * `nproc --all`))"};do bin/magento queue:consumers:start media.storage.catalog.image.resize &;done;
   ```

1. キューハンドラーが実行中であることを確認します。

   ```bash
   pgrep -fl media.storage.catalog.image.resize
   ```

1. すべての画像サイズ変更要求をキューに入れます。

   ```bash
   bin/magento catalog:images:resize --async
   ```

1. すべての画像のサイズを変更した後、プロセスを終了します。

   ```bash
   pkill -f media.storage.catalog.image.resize
   ```

## 速い道

フロントエンドを使用して画像のサイズを変更する別の方法もあります。

このアプローチの利点は次のとおりです。

- プロセスはマルチスレッドです。
- プロセスはマルチサーバー ( 複数の Web ノード、ロードバランサー、および `media/` ディレクトリ )
- プロセスは、既にサイズ変更された画像をスキップします

このアプローチでは、100,000 個の画像のサイズが 8 時間未満で変更されますが、CLI コマンドの実行に 6 日かかります。

1. サーバーにログインします。
1. に移動します。 `pub/media/catalog/product` ハッシュの 1 つをメモします ( 例：0047d83143a5a3a4683afdf116df680)。
1. 次の例では、 `www.example.com` をストアのドメインに置き換え、ハッシュを指定したドメインに置き換えます。

>[!BEGINTABS]

>[!TAB sed]

```bash
cd pub/
find ./media/catalog/product -path ./media/catalog/product/cache -prune -o -type f -print | sed 's~./media/catalog/product/~https://www.example.com/media/catalog/product/cache/0047d83143a5a3a4683afdf1116df680/~g' > images.txt
```

>[!TAB 包囲]

～の欠点 `siege` 同時実行が 10 に設定されている場合、はすべての URL を 10 回訪問することを意味します。

```bash
siege --file=./images.txt --user-agent="image-resizer" --no-follow --no-parser --concurrent=10 --reps=once
```

>[!TAB curl]

```bash
xargs -0 -n 1 -P 10 curl -X HEAD -s -w "%{http_code} %{time_starttransfer} %{url_effective}\n" < <(tr \\n \\0 <images.txt)
```

The `-P` 引数は、スレッドの数を決定します。

>[!TAB 一人乗りの人を殴る]

1 人の定期船は `find/curl` 例： `curl` 同じマシンから、イメージは次の場所にあります。

```bash
find ./media/catalog/product -path ./media/catalog/product/cache -prune -o -type f -print | sed 's~./media/catalog/product/~https://www.example.com/media/catalog/product/cache/0047d83143a5a3a4683afdf1116df680/~g' | xargs -n 1 -P 10 curl -X HEAD -s -w "%{http_code} %{time_starttransfer} %{url_effective}\n"
```

再び、 `www.example.com` を Web サイトのドメインに追加し、 `-P` をクラッシュせずにサーバーが処理できるスレッド数に設定します。

>[!ENDTABS]

出力は、ストア内のすべての製品画像のリストを返します。 画像をクロールできます ( `siege` または他のクローラ ) を使用して、使用可能なすべてのサーバとプロセッサコアを使用し、他の方法よりも大幅に高速にサイズ変更キャッシュを生成します。

1 つの画像キャッシュ URL を訪問しても、画像が存在しない場合は、すべての画像サイズがバックグラウンドで生成されます。 また、既にサイズが変更されたファイルはスキップされます。

>[!NOTE]
>
>- Adobe Commerce on cloud infrastructure プロジェクトは、製品イメージのサイズ変更を Fastly サービスにオフロードできます。 詳しくは、 [ディープ画像の最適化](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization.html?lang=en#deep-image-optimization) （内） _クラウドガイド_.
>- リモートストレージモジュールを使用する場合は、nginx に対する画像のサイズ変更のオフロードを試すこともできます。 詳しくは、 [リモートストレージの画像のサイズ変更を設定](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/storage/remote-storage/remote-storage-image-resize.html) （内） _設定ガイド_.
