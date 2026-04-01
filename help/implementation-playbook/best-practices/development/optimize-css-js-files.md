---
title: CSSおよびJS リソースファイルの最適化
description: Adobe Commerce プロジェクトのCSS ファイルとJavaScript（JS）ファイルを管理者またはコマンドラインから結合および縮小する方法について説明します。
role: Developer
feature: Best Practices
exl-id: ff0bc407-b563-418b-9d6a-7c1dc8f235df
source-git-commit: a08560eb307638a36fdc52224c41bdf2c5d47763
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# リソースファイルの最適化

Commerceのレスポンシブなサイトを実現するには、CSSとJavaScript（JS）のリソースファイルを最適化し、レンダーブロックリソースを排除します。

- **CSS ファイルとJS ファイルを最適化**- Adobe Commerceを使用してファイルを縮小およびバンドルするように設定することで、CSSおよびJavaScript（JS）ファイルを読み込むのに必要な時間を短縮します。
- **レンダリング ブロック リソースを排除** – 重要なJSおよびCSS機能をインラインで配信し、重要ではないJS/CSS スタイルをすべて延期することを検討します。 ガイダンスについては、[ レンダーブロッキングリソースの排除](https://web.dev/render-blocking-resources/)を参照してください。

## 影響を受ける製品とバージョン

[ サポートされているすべてのバージョン、2.3以降](../../../release/versions.md) /:

- Adobe Commerce on cloud infrastructure
- Adobe Commerce オンプレミス

## CSS ファイルを結合または縮小

CSSおよびJavaScript（JS）ファイルの読み込み時間は、個別のファイルを1つのファイルに結合、縮小、バンドルすることで短縮できます。

>[!IMPORTANT]
>
>Adobe Commerce オンクラウドインフラストラクチャは、常に実稼動モードで実行され、それ以外の場合は設定できません。そのため、結合、縮小、バンドルを有効にするには、コマンドラインメソッドを使用する必要があります。

デプロイメントでHTTP/2を使用している場合は、ファイルを結合またはバンドルしないでください。 HTTP/2は、静的ファイルを非同期でダウンロードします。 ブラウザーは、ファイルの内容を処理する前に、結合ファイル全体をダウンロードする必要があります。

### 管理者の使用

CSSの結合または縮小を有効にするには、**[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL CSS Settings]**&#x200B;に移動します。

### コマンドラインの使用

クラウドインフラストラクチャ上のAdobe CommerceでCSS結合を有効にするには：

1. 次のコマンドをローカルで実行します。

   ```bash
   bin/magento config:set --lock-config dev/css/merge_css_files 1
   ```

1. `app/etc/config.php` ファイルに変更をコミットして再デプロイします。

Adobe Commerce クラウドインフラストラクチャでCSSの縮小を有効にするには：

1. 次のコマンドをローカルで実行します。

   ```bash
   bin/magento config:set --lock-config dev/css/minify_files 1
   ```

1. `app/etc/config.php` ファイルに変更をコミットして再デプロイします。

## JS ファイルを縮小

### [!UICONTROL Admin]の使用中

[!UICONTROL Admin] サイドバーで、**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL JavaScript Settings]**&#x200B;に移動します。

### コマンドラインの使用

Adobe Commerce クラウドインフラストラクチャでJSの縮小を有効にするには：

1. 次のコマンドをローカルで実行します。

   ```bash
   bin/magento config:set --lock-config dev/js/minify_files 1
   ```

1. `app/etc/config.php` ファイルに変更をコミットして再デプロイします。

## バンドル JS ファイル

Commerce [!UICONTROL Admin]でバンドルを有効にできます：**[!UICONTROL Stores]** > ***[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL JavaScript Settings]**。

>[!NOTE]
>
>結合とバンドルを同時に有効にすることはできません。

コマンドラインからAdobe Commerceのビルトインバンドル（基本バンドル）を有効にすることもできます。

```bash
php -f bin/magento config:set dev/js/enable_js_bundling 1
```

## JS ファイルの結合（推奨されません） {#merge-js-files}

>[!WARNING]
>
>**[!UICONTROL Merge JavaScript Files]**&#x200B;を有効にすることはお勧めしません。 この設定は、ページの&#x200B;**[!UICONTROL HEAD]** セクションで同期的に読み込まれたJavaScriptに対してのみ設計されており、バンドルと[!DNL RequireJS] ロジックが正しく動作しない可能性があります。 後方互換性のみに保持され、HTTP/2が有効になっている場合にパフォーマンス上のメリットはありません。
>
>**[!UICONTROL Merge JavaScript Files]**&#x200B;を有効にして問題が発生した場合は、パッチを適用する前に無効にしてみてください。 結合を無効にできない場合は、[ACSD-67908](../../../tools/quality-patches-tool/patches-available-in-qpt/v1-1-73/acsd-67908.md)を参照してください。

## 追加情報

- [クライアントサイド最適化設定](../../../performance/configuration.md#client-side-optimization-settings)
- [設定のベストプラクティス ](../../../performance/configuration.md#bundling-tips)の&#x200B;*バンドルヒント* - サードパーティのバンドルツール、HTTP/2、非推奨のJSおよびCSS結合に関するガイダンス
- [ ユーザーガイド：リソースファイルの最適化](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/developer-tools#optimizing-resource-files)
- [ フロントエンド開発者ガイド：CSSの結合、縮小、サイトパフォーマンス ](https://developer.adobe.com/commerce/frontend-core/guide/css/#css-merging-minification-and-performance)
- [高度なJavaScriptのバンドル](../../../performance/advanced-js-bundling.md)
