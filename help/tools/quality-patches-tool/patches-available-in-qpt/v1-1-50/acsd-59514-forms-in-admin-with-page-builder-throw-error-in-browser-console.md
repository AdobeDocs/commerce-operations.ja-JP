---
title: ACSD-59514：管理画面でFormsがブラウザーコンソールで [!DNL Page Builder]  スローのエラーが発生する
description: ACSD-59514 パッチを適用して、Admin with  [!DNL Page Builder] のフォームがロックを解除せずに5秒間レンダリングされたというエラー「[!DNL Page Builder]」をスローするAdobe Commerceの問題を修正します。 フォームの送信後にブラウザーコンソールで変更を保存できません。
feature: Page Builder
role: Admin, Developer
exl-id: 3d1167d2-0a75-48ac-bc31-5bbd3c4a409e
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# ACSD-59514：管理画面のFormsで[!DNL Page Builder] スローエラーが発生しました

ACSD-59514 パッチでは、[!DNL Page Builder]を持つ管理者のフォームがエラー&#x200B;*[!DNL Page Builder]をスローし、ロックを解除せずに5秒間レンダリングしていた問題を修正します。* フォームの送信後にブラウザーコンソールで変更を保存できません。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.50がインストールされている場合に利用できます。 パッチ IDはACSD-59514です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p8

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

管理画面で[!DNL Page Builder]を使用しているFormsで、エラー&#x200B;*[!DNL Page Builder]が5秒間ロックを解除せずにレンダリングされていたというエラーがスローされました。* フォームの送信後にブラウザーコンソールで変更を保存できません。

<u>前提条件</u>:

Adobe Commerce [!DNL Page Builder] モジュールがインストールされ、有効になっています。

<u>複製する手順</u>:

1. 管理パネルを開き、[!UICONTROL Content] ボタンをクリックします。
1. ブロックを選択し、ブロックを編集します。
1. コンテンツを変更して、[!UICONTROL Save]をクリックします。
1. コンソールを開き、エラーメッセージを確認します。

<u>期待される結果</u>:

ブロックが正常に保存されました。

<u>実際の結果</u>:

ローダーは回転を停止せず、ブロックは保存されません。 ブラウザーコンソールに次のエラーが表示されます。
*[!DNL Page Builder]はロックを解除せずに5秒間レンダリングしていました。*

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
