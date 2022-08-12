---
title: 静的コンテンツキャッシュ
description: 静的コンテンツの署名と、この機能を有効または無効にする方法を理解できます。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# 静的コンテンツキャッシュ

パフォーマンスを向上させるために、Commerce では `Expires` 画像、JavaScript、CSS ファイルなどの静的リソースのヘッダー。
の設定 `Expires` 静的リソースのヘッダーは、その URL でリソースをキャッシュし、キャッシュされたバージョンを期限が切れるまで提供するようにブラウザーに指示します。
これは一般的な例です [ベストプラクティス](https://developer.yahoo.com/performance/rules.html#expires=) 静的リソースをキャッシュする場合。

ブラウザーが静的リソースをキャッシュし、そのリソースがサーバー上で変更された場合、新しいバージョンをダウンロードできるように、ブラウザーのキャッシュをクリアする必要があります。
次の場合、ブラウザーキャッシュの手動クリアは機能します。 [web サイト](https://glossary.magento.com/website) 管理者ですが、静的リソースの新しいバージョンをユーザーにダウンロードしてもらいたい場合にユーザーに要求するのに適した要求ではありません。

## 静的コンテンツ署名

[静的コンテンツ](https://glossary.magento.com/static-content) 署名は、静的リソースのブラウザーキャッシュを無効にするコマース機能です。
Commerce は、の URL にデプロイメントバージョンを追加することでこれを実現します [静的ファイル](https://glossary.magento.com/static-files).

次に、バージョンで署名された URL の例を示します。

```terminal
http://magento2.com/pub/static/version1475604434/frontend/Magento/luma/en_US/images/logo.svg
```

コマンドを実行するとき [`setup:static-content:deploy`](../cli/static-view-file-deployment.md) 静的コンテンツをデプロイする場合、Commerce はデプロイメントバージョンを自動的に変更します。
これにより、静的ファイルの URL が変更され、ブラウザーに新しいバージョンのファイルが強制的に読み込まれます。

Commerce では、デフォルトでこの機能が有効になっています。古い静的リソースを提供するブラウザーに関する問題を防ぐため、Adobeではこの機能を有効にしておくことをお勧めします。

この機能の設定については、 [**[!UICONTROL Stores]**/設定/設定/**[!UICONTROL Advanced]**>**[!UICONTROL Developer]**>**[!UICONTROL Static Files Settings]**](https://docs.magento.com/user-guide/system/static-file-signature.html).

![静的ファイル設定](../../assets/configuration/static-files-settings.png)

ステータスを決定します。

```bash
bin/magento config:show dev/static/sign
```

静的コンテンツ署名を有効または無効にする：

```bash
bin/magento config:set dev/static/sign <value>
```

ここで、 `<value>` が 1（有効）または 0（無効）の場合。

## バージョン署名

Commerce は、静的リソース間の相対 URL の整合性を維持するために、静的ビューファイルのベース URL の直後にバージョン署名をパスコンポーネントとして追加します。
また、これにより、ブラウザーは、署名値の有無に関係なく、コンテンツを維持しながら、正しい署名済みソースへの相対 URL を解決するようになります。

ブラウザーがサーバーから署名されたソースを要求すると、サーバーは URL の書き換えを使用して、URL から署名コンポーネントを削除します。

## デプロイメント中の使用状況

静的リソースをアップグレードまたは変更した後、 `setup:static-content:deploy` コマンドを使用して、バージョンをデプロイし、静的コンテンツを更新します。これにより、ブラウザーに更新されたリソースが強制的に読み込まれます。

別のサーバーにコードをデプロイし、コードリポジトリを使用して実稼動環境に移動してダウンタイムを短縮する場合は、ファイルも追加する必要があります `pub/static/deployed_version.txt` をリポジトリに追加します。
このファイルには、デプロイされた静的コンテンツの新しいバージョンが含まれます。