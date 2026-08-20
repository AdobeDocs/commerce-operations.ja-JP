---
title: 'ADOBE COMMERCE Adminで通知を閉じるときにACSD-47336: [!UICONTROL Something went wrong] エラーが発生しました'
description: ACSD-47336 パッチを適用して、 [!DNL Commerce] 管理者で通知を閉じると[!UICONTROL Something went wrong] エラーが表示されるAdobe Commerceの問題を修正します。
feature: Admin Workspace
role: Admin
exl-id: da0c0119-6720-493f-a278-d573ed898a63
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# ADOBE COMMERCE Adminで通知を閉じるときにACSD-47336: _[!UICONTROL Something went wrong]_エラーが発生しました

ACSD-47336 パッチは、[!DNL Commerce]管理者で通知を却下する際にユーザーに&#x200B;_[!UICONTROL Something went wrong]_エラーが表示される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.24がインストールされている場合に利用できます。 パッチ IDはACSD-47336です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法）:2.4.5

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法）: 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

[!DNL Commerce]管理者で通知を閉じると、_[!UICONTROL Something went wrong]_エラーが表示されます。

<u>複製する手順</u>:

1. 一括操作を実行します（例：製品グリッドからの製品属性の一括更新）。
1. 操作を完了します（例：`bin/magento queue:consumer:start product_action_attribute.update`を実行）。
1. [!DNL Commerce]管理者ページを更新し、管理者通知セクションを展開して、**[!UICONTROL Dismiss All Completed Tasks]** リンクをクリックします。

<u>期待される結果</u>:

完了したタスクをクリアすると、_[!UICONTROL Something went wrong]_エラーは表示されません。

<u>実際の結果</u>:

_[!UICONTROL Something went wrong]_エラーが表示されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
