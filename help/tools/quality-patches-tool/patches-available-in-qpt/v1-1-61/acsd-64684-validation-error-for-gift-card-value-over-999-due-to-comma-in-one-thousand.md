---
title: 'ACSD-64684: コンマが1,000 （1,000）の場合、値が999を超えるギフトカードを保存すると検証エラーが発生する'
description: コンマが「1000」（1,000）の場合に、999を超える値のギフトカードを保存すると検証エラーが発生するAdobe Commerceの問題を修正するには、ACSD-64684 パッチを適用します。
feature: Catalog Management
role: Admin, Developer
exl-id: 327c5d28-b52c-4da9-a905-8a3deb755241
type: Troubleshooting
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-64684: コンマが1,000 （1,000）の場合、値が999を超えるギフトカードを保存すると検証エラーが発生する

ACSD-64684 パッチでは、コンマが「1000」（1,000）であるため、999を超える値のギフトカードを保存すると検証エラーが発生する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61がインストールされている場合に利用できます。 パッチ IDはACSD-64684です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

「千」（1,000）など、数字のコンマ（千区切り記号）が原因で、999を超える値のギフトカードを編集して保存すると、検証エラーが発生します。

<u>複製する手順</u>:

1. ギフトカード商品の作成。
   1. [!UICONTROL Amount]に1,000と入力します。
   1. **[!UICONTROL Save]**&#x200B;をクリックします。

<u>期待される結果</u>:

* 1,000枚の新しいギフトカードが保存されます。

<u>実際の結果</u>:

* ギフトカードの金額が999を超えると、検証エラーが発生します。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
