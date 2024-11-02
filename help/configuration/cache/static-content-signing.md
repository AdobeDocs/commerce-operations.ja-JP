---
title: 静的コンテンツキャッシュ
description: 静的コンテンツの署名と、この機能を有効または無効にする方法を理解します。
feature: Configuration, Cache, SCD
exl-id: b54ceea2-b3a1-4dbb-ba87-743f2af0d2fb
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# 静的コンテンツキャッシュ

パフォーマンスを向上させるために、Commerceでは、画像、JavaScript、CSS ファイルなどの静的リソースの `Expires` ヘッダーを設定します。
静的リソースに `Expires` ヘッダーを設定すると、その URL のリソースをキャッシュし、有効期限が切れるまでキャッシュされたバージョンを提供するようにブラウザーに指示されます。
これは、静的リソースをキャッシュする場合に一般的な [ ベストプラクティス ](https://developer.yahoo.com/performance/rules.html#expires=) です。

ブラウザーが静的リソースをキャッシュし、そのリソースがサーバー上で変更された場合、新しいバージョンをダウンロードできるように、ブラウザーキャッシュをクリアする必要があります。
Web サイト管理者の場合はブラウザーキャッシュの手動によるクリアで機能しますが、静的リソースの新しいバージョンをダウンロードする際に、ユーザーに対して行う適切なリクエストではありません。

## 静的コンテンツ署名

静的コンテンツ署名は、静的リソースのブラウザーキャッシュを無効にするためのCommerceの機能です。
Commerceでは、静的ファイルの URL にデプロイメントバージョンを追加することでこれを実行します。

次に、バージョンで署名された URL の例を示します。

```
http://magento2.com/pub/static/version1475604434/frontend/Magento/luma/en_US/images/logo.svg
```

コマンド [`setup:static-content:deploy`](../cli/static-view-file-deployment.md) を実行して静的コンテンツをデプロイすると、Commerceによってデプロイメントバージョンが自動的に変更されます。
これにより、静的ファイルの URL が変更され、ブラウザーで新しいバージョンのファイルが強制的に読み込まれます。

Commerceでは、この機能がデフォルトで有効になっています。Adobeでは、古い静的リソースを提供するブラウザーに関連する問題を防ぐために、この機能を有効にしておくことをお勧めします。

静的コンテンツ署名の設定は、[**[!UICONTROL Stores]**/設定/設定/**[!UICONTROL Advanced]**/**[!UICONTROL Developer]**/**[!UICONTROL Static Files Settings]**](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/developer-tools#static-file-signatures) にあります。

- **オンプレミスのみ**：この設定は、サイトが [ 実稼動モード **で** 使用できない ](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html#production-mode) 場合に使用できます。
- **Cloud**：この設定は、実稼動モードが厳密に適用されるので、非表示です。そのため、次に示すように、コマンドラインを使用する必要があります。

![ 静的ファイル設定 ](../../assets/configuration/static-files-settings.png)

ステータスを次のように決定します。

```bash
bin/magento config:show dev/static/sign
```

静的コンテンツ署名を有効または無効にする：

```bash
bin/magento config:set dev/static/sign <value>
```

ここで、`<value>` は 1 （有効）または 0 （無効）です。

## バージョンの署名

静的リソース間の相対 URL の整合性を維持するために、Commerceでは静的ビューファイルのベース URL の直後にバージョン署名をパスコンポーネントとして追加します。
また、これにより、署名値の有無に関係なく、ブラウザーのコンテンツを保持しながら、正しい署名済みソースへの相対 URL を解決するように強制されます。

ブラウザーがサーバーから署名済みソースを要求すると、サーバーは URL の書き換えを使用して、URL から署名コンポーネントを削除します。

## デプロイメント中の使用

静的リソースをアップグレードまたは変更した後、`setup:static-content:deploy` コマンドを実行してバージョンをデプロイし、静的コンテンツを更新する必要があります。これにより、ブラウザーは更新されたリソースを強制的に読み込みます。

コードを別のサーバーにデプロイし、コードリポジトリを使用して実稼動環境に移動してダウンタイムを短縮する場合は、ファイル `pub/static/deployed_version.txt` もリポジトリに追加する必要があります。
このファイルには、デプロイされた静的コンテンツの新しいバージョンが含まれています。
