---
title: パッチの動作
description: Adobe CommerceおよびMagento Open Source用の様々なタイプのパッチとその動作について説明します。
source-git-commit: 1a18a445cb104420dd9b853b7c4d42ce3bddf2ac
workflow-type: tm+mt
source-wordcount: '606'
ht-degree: 0%

---


# パッチの仕組み

>[!WARNING]
>
>実稼動環境にデプロイする前に、ステージング環境または開発環境ですべてのパッチをテストすることを強くお勧めします。 また、パッチを適用する前に、データをバックアップすることを強くお勧めします。 詳しくは、 [ファイル・システムのバックアップとロールバック](../../installation/tutorials/backup.md).

パッチ（または差分）ファイルは、次の点に注意するテキストファイルです。

- 変更するファイル。
- 変更を開始するライン番号と変更するライン数。
- スワップインする新しいコード。

パッチプログラムを実行すると、このファイルが読み込まれ、指定された変更がファイルに対して行われます。

パッチには次の 3 つのタイプがあります。

- **ホットフィックス**-Adobeが [セキュリティセンター](https://magento.com/security/patches).
- **個々のパッチ**- Adobe Commerce Support が作成し、個々に配布するパッチ。
- **カスタムパッチ**—Git コミットから作成できる非公式のパッチです。

## ホットフィックス

ホットフィックスは、多くの商人に影響を与える、大きな影響を及ぼすセキュリティや品質の修正を含むパッチです。 これらの修正は、該当するマイナーバージョンの次のパッチリリースに適用されます。 Adobeは、必要に応じてホットフィックスをリリースします。

ホットフィックスは、 [セキュリティセンター](https://magento.com/security/patches). ページの手順に従って、バージョンとインストールタイプに応じて、パッチファイルをダウンロードします。 以下を使用： [コマンドライン](../patches/apply.md#) または [コンポーザー](../patches/apply.md) ホットフィックスパッチを適用する。

>[!NOTE]
>
>ホットフィックスに、後方互換性のない変更が含まれている可能性があります。

## 個々のパッチ

個々のパッチには、特定の問題に対する影響の低い品質の修正が含まれています。 これらの修正は、最も新しくサポートされたマイナーバージョン（2.4.x など）に適用されますが、以前のサポートされたマイナーバージョン（2.3.x など）には適用されません。 Adobeは、必要に応じて個々のパッチをリリースします。

以下を使用： [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)個々のパッチを適用する場合は、{target=&quot;_blank&quot;}。

>[!NOTE]
>
>個々のパッチには、後方互換性のない変更は含まれません。

## カスタムパッチ

AdobeエンジニアリングチームがAdobe CommerceまたはMagento Open Sourceコンポーザーのリリースで GitHub でおこなわれたバグ修正を含めるのに時間がかかる場合があります。 それまでの間、GitHub からパッチを作成し、 [`cweagans/composer-patches`](https://github.com/cweagans/composer-patches/) プラグインを使用して、Composer ベースのインストールに適用できます。

以下を使用： [コマンドライン] または [コンポーザー] カスタムパッチを適用する場合。

カスタムパッチファイルを作成する方法は多数あります。 次の例では、既知の Git コミットからパッチを作成する方法に焦点を当てています。

カスタムパッチを作成するには：

1. の作成 `patches/composer` ローカルプロジェクトのディレクトリ。
1. パッチに使用する GitHub コミットまたはプル要求を特定します。 この例では、 [`2d31571`](https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede) コミット、GitHub の問題にリンク [#6474](https://github.com/magento/magento2/issues/6474).
1. を追加します。 `.patch` または `.diff` コミット URL の拡張子。 用途 `.diff` を使用します。 例： [https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede.diff](https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede.diff)
1. ページをファイルとしてに保存します。 `patches/composer` ディレクトリ。 例： `github-issue-6474.diff`.
1. ファイルを編集し、を削除します。 `app/code/<VENDOR>/<PACKAGE>` すべてのパスから、 `vendor/<VENDOR>/<PACKAGE>` ディレクトリ。

   >[!NOTE]
   >
   >末尾の空白文字を自動的に削除したり、新しい行を追加したりするテキストエディターは、パッチを壊す可能性があります。 簡単なテキストエディターを使用して、これらの変更を行います。

次の例は、のすべてのインスタンスを削除した後の、前述の DIFF ファイルを示しています。 `app/code/Magento/Payment`:

```diff
diff --git a/view/frontend/web/js/view/payment/iframe.js b/view/frontend/web/js/view/payment/iframe.js
index c8a6fef58d31..7d01c195791e 100644
--- a/view/frontend/web/js/view/payment/iframe.js
+++ b/view/frontend/web/js/view/payment/iframe.js
@@ -154,6 +154,7 @@ define(
              */
             clearTimeout: function () {
                 clearTimeout(this.timeoutId);
+                this.fail();

                 return this;
             },
```

## パッチの適用

次のいずれかの方法でパッチを適用できます。

- [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target=&quot;_blank&quot;}
- [コマンドライン](/help/upgrade/patches/apply.md#command-line)
- [コンポーザー](/help/upgrade/patches/apply.md#composer)

>[!NOTE]
>
>クラウドインフラストラクチャ上のAdobe Commerceプロジェクトにパッチを適用するには、 [パッチの適用](https://devdocs.magento.com/cloud/project/project-patch.html) 内 _クラウドガイド_.
