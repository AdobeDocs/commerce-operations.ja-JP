---
title: 静的コンテンツ署名とブラウザーキャッシュの無効化
description: Adobe Commerceで静的コンテンツ署名を使用して、静的リソースのブラウザーキャッシュを無効にする方法を説明します。 この機能を有効にして設定する方法について説明します。
feature: Configuration, Cache, SCD
exl-id: b54ceea2-b3a1-4dbb-ba87-743f2af0d2fb
badgePaas: label="PaaS" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Adobe Commerce クラウド版およびオンプレミスプロジェクトにのみ適用されます。"
autotag-review: '2026-06-22T21:48:08.334Z'
TQID: 'https://experienceleague.adobe.com/vagWBVnjIS7tjnwVE5Dk56VDmPtbPgjsNVLBHSlOc-s'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
    internal-label: Commerce on Prem
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
    internal-label: Commerce on Cloud
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: d05f97c9-0a96-5792-92cf-f66ce7326e3a
    internal-label: SCD
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '532'
ht-degree: 0%
---
# 静的コンテンツの署名とブラウザーキャッシュの無効化

Commerceは、パフォーマンスを向上させるために、画像、JavaScript、CSS ファイルなどの静的リソースに`Expires` ヘッダーを設定します。
静的リソースに`Expires` ヘッダーを設定すると、ブラウザーはそのURLでリソースをキャッシュし、有効期限が切れるまでキャッシュされたバージョンを提供するように指示されます。
これは、静的リソースをキャッシュするための一般的な[ ベストプラクティス ](https://developer.yahoo.com/performance/rules.html#expires=)です。

ブラウザーが静的リソースをキャッシュし、そのリソースがサーバー上で変更された場合、ブラウザーのキャッシュをクリアして新しいバージョンをダウンロードできるようにする必要があります。
Web サイト管理者は、ブラウザーのキャッシュを手動でクリアできますが、静的リソースの新しいバージョンをダウンロードする場合は、ユーザーに適切なリクエストを行う必要はありません。

## 静的コンテンツ署名

静的コンテンツ署名は、静的リソースのブラウザーキャッシュを無効にできるCommerceの機能です。
Commerceでは、静的ファイルのURLにデプロイメントバージョンを追加することで、これを実現します。

次に、バージョンで署名されたURLの例を示します。

```text
http://magento2.com/pub/static/version1475604434/frontend/Magento/luma/en_US/images/logo.svg
```

静的コンテンツをデプロイするためにコマンド [`setup:static-content:deploy`](../cli/static-view-file-deployment.md)を実行すると、Commerceによってデプロイメントバージョンが自動的に変更されます。
これにより、静的ファイルのURLが変更され、ブラウザーは新しいバージョンのファイルを強制的に読み込みます。

Commerceでは、デフォルトでこの機能が有効になっています。Adobeでは、古い静的リソースを提供するブラウザーに関する問題を回避するために、この機能を有効にしておくことをお勧めします。

静的コンテンツ署名の設定は、[**[!UICONTROL Stores]**/ 設定/設定/**[!UICONTROL Advanced]**/**[!UICONTROL Developer]**/**[!UICONTROL Static Files Settings]**](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/developer-tools#static-file-signatures)にあります。

- **オンプレミスのみ**：この設定は、[実稼動モード ](../bootstrap/application-modes.md#production-mode)でサイトが&#x200B;**not**&#x200B;の場合に使用できます。
- **Cloud**：実稼動モードが厳密に適用されているため、この設定は非表示になっています。したがって、次に示すようにコマンドラインを使用する必要があります。

![静的ファイル設定](../../assets/configuration/static-files-settings.png)

ステータスの決定：

```shell
bin/magento config:show dev/static/sign
```

静的コンテンツ署名を有効または無効にする：

```shell
bin/magento config:set dev/static/sign <value>
```

ここで、`<value>`は1 （有効）または0 （無効）です。

## バージョンの署名

Commerceは、静的なビューファイルのベース URLの直後にバージョン署名をパスコンポーネントとして追加し、静的なリソース間の相対URLの整合性を維持します。
これにより、ブラウザーは、署名値の有無に関係なく、コンテンツを保持しながら、適切な署名済みソースへの相対URLを解決する必要があります。

ブラウザーがサーバーから署名済みソースを要求すると、サーバーはURLの書き換えを使用して、署名コンポーネントをURLから削除します。

## デプロイ時の使用

静的リソースをアップグレードまたは変更した後、`setup:static-content:deploy` コマンドを実行してバージョンをデプロイし、静的コンテンツを更新する必要があります。これにより、ブラウザーは更新されたリソースを強制的に読み込みます。

別のサーバーにコードをデプロイし、ダウンタイムを減らすためにコードリポジトリを使用して実稼動に移行する場合は、ファイル `pub/static/deployed_version.txt`をリポジトリに追加する必要もあります。
このファイルには、デプロイされた静的コンテンツの新しいバージョンが含まれます。
