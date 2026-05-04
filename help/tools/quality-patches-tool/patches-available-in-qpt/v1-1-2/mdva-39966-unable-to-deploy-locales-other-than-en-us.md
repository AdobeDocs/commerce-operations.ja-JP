---
title: 'MDVA-39966: en_US以外のロケールをデプロイできません'
description: MDVA-39966 パッチは、ユーザーがen_US以外のロケールをデプロイできない問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.2がインストールされている場合に利用できます。 パッチ IDはMDVA-39966です。 この問題は、Adobe Commerce バージョン 2.4.1で修正されています。
feature: Deploy
role: Admin
exl-id: 03bb0002-9742-4f26-bb41-1b46f0a3573c
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# MDVA-39966: en_US以外のロケールをデプロイできません

MDVA-39966 パッチは、ユーザーがen_US以外のロケールをデプロイできない問題を解決します。 このパッチは、[品質パッチツール （QPT） ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2がインストールされている場合に使用できます。 パッチ IDはMDVA-39966です。 この問題は、Adobe Commerce バージョン 2.4.1で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.3.5-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方式） 2.3.0 - 2.3.5-p2、2.4.0 - 2.4.0-p1

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

en_US以外のロケールをデプロイできません。

<u>複製する手順</u>:

1. en_USやde_DEなど、異なるロケールを持つ2つのストアビューを設定します。
1. 次のコマンドを実行して、これらのロケールの静的コンテンツをデプロイしてみてください。

```shell
bin/magento setup:static-content:deploy --language=en_US
bin/magento setup:static-content:deploy --language=de_DE
```

<u>期待される結果</u>:

de_DE ロケールがデプロイされます。

```shell
bin/magento setup:static-content:deploy --language=de_DE

Deploy using quick strategy
adminhtml/Magento/backend/de_DE         2416/2416           ============================ 100%   9 secs
frontend/Magento/blank/de_DE            2486/2486           ============================ 100%   7 secs
frontend/Magento/luma/de_DE             2504/2504           ============================ 100%   8 secs

Execution time: 27.062166929245
```

<u>実際の結果</u>:

de_DEの代わりにデプロイされたen_US ロケール：

```shell
bin/magento setup:static-content:deploy --language=de_DE

Deploy using quick strategy
adminhtml/Magento/backend/en_US         2416/2416           ============================ 100%   2 secs
frontend/Magento/blank/en_US            2486/2486           ============================ 100%   1 sec
frontend/Magento/luma/en_US             2504/2504           ============================ 100%   2 secs
```

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [品質パッチツール ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
