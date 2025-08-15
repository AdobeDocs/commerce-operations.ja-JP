---
title: パッチの動作
description: Adobe Commerceの様々なタイプのパッチとその動作について説明します。
exl-id: d7072ed4-7d51-41fe-881a-aae3b2000b55
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# パッチの動作

>[!WARNING]
>
>実稼動環境にデプロイする前に、ステージング環境または開発環境で、すべてのパッチをテストすることを強くお勧めします。 また、パッチを適用する前にデータをバックアップすることを強くお勧めします。 [ ファイルシステムのバックアップとロールバック ](../../installation/tutorials/backup.md) を参照してください。

パッチ（または差分）ファイルは、次の点に注意するテキストファイルです。

- 変更するファイル。
- 変更を開始するライン番号と変更するライン数。
- 入れ替える新しいコード。

パッチプログラムを実行すると、このファイルが読み込まれ、指定された変更がファイルに加えられます。

パッチには次の 3 種類があります。

- **ホットフィックス** - Adobeが [ セキュリティセンター ](https://magento.com/security/patches) に公開するパッチ。
- **個別パッチ** - Adobe Commerce サポートが個別に作成および配布するパッチ。
- **カスタムパッチ** - Git コミットから作成できる非公式パッチ。

## ホットフィックス

ホットフィックスは、多くのマーチャントに影響を与える影響の大きいセキュリティ修正または品質修正を含むパッチです。 これらの修正は、該当するマイナーバージョンの次のパッチリリースに適用されます。 Adobeは、必要に応じてホットフィックスをリリースします。

ホットフィックスは、[ セキュリティセンター ](https://magento.com/security/patches) で入手できます。 ページの指示に従って、バージョンとインストールの種類に応じてパッチファイルをダウンロードします。 [ コマンドライン ](../patches/apply.md#) または [Composer](../patches/apply.md) を使用して、ホットフィックス パッチを適用します。

>[!NOTE]
>
>ホットフィックスには、後方互換性のない変更が含まれている場合があります。

## 個々のパッチ

個々のパッチには、特定の問題に対する影響の低い品質修正が含まれています。 これらの修正は、最新のサポートされているマイナーバージョン（例：2.4.x）に適用されますが、以前のサポートされているマイナーバージョン（例：2.3.x）には含まれていない場合があります。 Adobeでは、必要に応じて個別のパッチをリリースします。

[[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja){target="_blank"} を使用して、個別のパッチを適用します。

>[!NOTE]
>
>個々のパッチには、後方互換性のない変更は含まれません。

## カスタムパッチ

Adobe エンジニアリングチームが、Adobe Commerce Composer リリースで GitHub に加えられたバグ修正を含めるのに時間がかかる場合があります。 それまでの間、GitHub からパッチを作成し、[`cweagans/composer-patches`](https://github.com/cweagans/composer-patches/) プラグインを使用して Composer ベースのインストールに適用できます。

[ コマンドライン ](apply.md#command-line) または [Composer](apply.md#composer) を使用して、カスタムパッチを適用します。

カスタム パッチ ファイルを作成する方法は多数あります。 次の例では、既知の Git コミットからのパッチの作成に焦点を当てています。

カスタムパッチを作成するには：

1. ローカルプロジェクトに `patches/composer` ディレクトリを作成します。
1. パッチに使用する GitHub コミットまたはプルリクエストを特定します。 この例では、GitHub の問題 [`2d31571`#6474](https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede) にリンクされた [&#128279;](https://github.com/magento/magento2/issues/6474) コミットを使用しています。
1. コミット URL に `.patch` または `.diff` の拡張子を追加します。 ファイルサイズを小さくするには、`.diff` を使用します。 例：[https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede.diff](https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede.diff)
1. `patches/composer` ディレクトリにページをファイルとして保存します。 例：`github-issue-6474.diff`。
1. ファイルを編集し、すべてのパスから `app/code/<VENDOR>/<PACKAGE>` を削除して、`vendor/<VENDOR>/<PACKAGE>` ディレクトリに対する相対パスにします。

   >[!NOTE]
   >
   >末尾の空白を自動的に削除したり、新しい行を追加したりするテキストエディターは、パッチを破損する可能性があります。 これらの変更を行うには、単純なテキストエディターを使用します。

次の例は、`app/code/Magento/Payment` のすべてのインスタンスを削除した後の前述の DIFF ファイルを示しています。

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

パッチは、次のいずれかの方法で適用できます。

- [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja){target="_blank"}
- [コマンドライン](/help/upgrade/patches/apply.md#command-line)
- [コンポーザー](/help/upgrade/patches/apply.md#composer)

>[!NOTE]
>
>クラウドインフラストラクチャプロジェクト上のAdobe Commerceにパッチを適用するには、[Commerce on Cloud ガイド ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja) の _パッチの適用_ を参照してください。
