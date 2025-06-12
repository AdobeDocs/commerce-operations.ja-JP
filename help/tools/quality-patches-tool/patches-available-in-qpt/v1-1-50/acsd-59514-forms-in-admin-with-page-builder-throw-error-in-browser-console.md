---
title: ACSD-59514：ブラウザーコンソールの管理者のFormsで  [!DNL Page Builder]  スローエラーが発生する
description: ACSD-59514 パッチを適用すると、管理者のフォームで「[!DNL Page Builder] はロックを解除せずに 5 秒間レンダリングしてい  [!DNL Page Builder]  した」というエラーがスローされるAdobe Commerceの問題が修正されます。 フォームの送信後にブラウザーコンソールで開き、変更を保存できない。
feature: Page Builder
role: Admin, Developer
exl-id: 3d1167d2-0a75-48ac-bc31-5bbd3c4a409e
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-59514：ブラウザーコンソールの投 [!DNL Page Builder] エラーを伴う管理画面のForms

ACSD-59514 パッチは、[!DNL Page Builder] を持つ管理画面のフォームが、ロックを解除せずにレンダリングしてい *[!DNL Page Builder]エラーを 5 秒間スローする問題を修正しました。フォームの送信後にブラウザーコンソールを* リックすると、変更を保存できない。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50 がインストールされている場合に使用できます。 パッチ ID は ACSD-59514 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p8

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

[!DNL Page Builder] を使用している管理者のFormsで、レンダリング中のエラー *[!DNL Page Builder]ロックを解放せずに 5 秒間スローされる。フォームの送信後にブラウザーコンソールを* リックすると、変更を保存できない。

<u> 前提条件 </u>:

Adobe Commerce [!DNL Page Builder] モジュールがインストールされ、有効になっています。

<u> 再現手順 </u>:

1. 管理パネルを開き、「[!UICONTROL Content]」ボタンをクリックします。
1. ブロックを選択し、ブロックを編集します。
1. コンテンツを変更し、「変 [!UICONTROL Save]」をクリックします。
1. コンソールを開き、エラーメッセージを確認します。

<u> 期待される結果 </u>:

ブロックが正常に保存されました。

<u> 実際の結果 </u>:

ローダーは回転を停止せず、ブロックは保存されません。 次のエラーがブラウザーコンソールに表示されます。
*[!DNL Page Builder]は、ロックを解除せずに 5 秒間レンダリングされていました。*

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
