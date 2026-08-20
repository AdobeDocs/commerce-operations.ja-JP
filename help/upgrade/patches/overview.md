---
title: パッチの動作
description: Adobe Commerceの様々な種類のパッチとその仕組みについて説明します。
exl-id: d7072ed4-7d51-41fe-881a-aae3b2000b55
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '592'
ht-degree: 0%

---

# パッチの動作

>[!WARNING]
>
>実稼動にデプロイする前に、ステージング環境または開発環境ですべてのパッチをテストすることを強くお勧めします。 また、パッチを適用する前にデータをバックアップすることを強くお勧めします。 [&#x200B; ファイルシステムのバックアップとロールバック &#x200B;](../../installation/tutorials/backup.md)を参照してください。

パッチ（または差分）ファイルは、次の点に注意するテキストファイルです。

- 変更するファイル。
- 変更を開始する行番号と変更する行数。
- スワップする新しいコード。

パッチプログラムを実行すると、このファイルが読み込まれ、指定された変更がファイルに加えられます。

パッチには3つのタイプがあります。

- **ホットフィックス** - Adobeが[&#x200B; セキュリティセンター](https://magento.com/security/patches)で公開するパッチ。
- **個別パッチ** - Adobe Commerce サポートが個別に作成および配布するパッチ。
- **カスタムパッチ** - Git コミットから作成できる非公式パッチ。

## ホットフィックス

修正プログラムは、多くのマーチャントに影響を与える影響の大きいセキュリティまたは品質の修正プログラムを含むパッチです。 これらの修正は、該当するマイナーバージョンの次のパッチリリースに適用されます。 Adobeは、必要に応じてホットフィックスをリリースします。

修正プログラムは、[&#x200B; セキュリティ センター](https://magento.com/security/patches)で見つけることができます。 パッチファイルをダウンロードするには、バージョンとインストールタイプに応じて、ページの指示に従います。 [&#x200B; コマンドライン &#x200B;](../patches/apply.md#)または[Composer](../patches/apply.md)を使用して、ホットフィックス パッチを適用します。

>[!NOTE]
>
>ホットフィックスには、後方互換性のない変更が含まれる場合があります。

## 個別のパッチ

個々のパッチには、特定の問題に対する影響の小さい品質修正が含まれています。 これらの修正は、サポートされている最新のマイナーバージョン（2.4.xなど）に適用されますが、サポートされている以前のマイナーバージョン（2.3.xなど）には反映されない可能性があります。 Adobeでは、必要に応じて個別のパッチをリリースします。

個別のパッチを適用するには、[[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}を使用します。

>[!NOTE]
>
>個々のパッチには、後方互換性のない変更は含まれていません。

## カスタムパッチ

Adobeのエンジニアリングチームが、GitHubで行われたバグ修正をAdobe Commerceの公式リリースに含めるまでに、時間がかかる場合があります。 また、GitHubからパッチを作成し、[`cweagans/composer-patches`](https://github.com/cweagans/composer-patches/) プラグインを使用して、それをComposer ベースのインストールに適用することもできます。

{{custom-patches-disclaimer}}

カスタムパッチを適用するには、[&#x200B; コマンドライン &#x200B;](apply.md#command-line)または[Composer](apply.md#composer)を使用します。

カスタムパッチファイルを作成する方法はたくさんあります。 次の例では、既知のGit コミットからパッチを作成することに焦点を当てています。

カスタムパッチを作成するには：

1. ローカルプロジェクトに`patches/composer` ディレクトリを作成します。
1. パッチに使用するGitHub コミットまたはプルリクエストを特定します。 この例では、GitHubの問題[#6474](https://github.com/magento/magento2/issues/6474)にリンクされた[`2d31571`](https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede)のコミットを使用しています。
1. コミット URLに`.patch`または`.diff`拡張機能を追加します。 ファイルサイズを小さくするには、`.diff`を使用してください。 例：[https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede.diff](https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede.diff)
1. ページを`patches/composer` ディレクトリにファイルとして保存します。 例：`github-issue-6474.diff`。
1. ファイルを編集し、すべてのパスから`app/code/<VENDOR>/<PACKAGE>`を削除して、`vendor/<VENDOR>/<PACKAGE>` ディレクトリに関連するようにします。

   >[!NOTE]
   >
   >末尾の空白を自動的に削除したり、新しい行を追加したりするテキストエディターは、パッチを壊す可能性があります。 単純なテキストエディターを使用して、これらの変更を行います。

次の例は、`app/code/Magento/Payment`のすべてのインスタンスを削除した後、前述のDIFF ファイルを示しています。

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

パッチは、次のいずれかの方法を使用して適用できます。

- [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}
- [コマンドライン](/help/upgrade/patches/apply.md#command-line)
- [Composer](/help/upgrade/patches/apply.md#composer)

>[!NOTE]
>
>Adobe Commerce on Cloud Infrastructure プロジェクトにパッチを適用するには、_Commerce on Cloud ガイド_&#x200B;の「[&#x200B; パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」を参照してください。
