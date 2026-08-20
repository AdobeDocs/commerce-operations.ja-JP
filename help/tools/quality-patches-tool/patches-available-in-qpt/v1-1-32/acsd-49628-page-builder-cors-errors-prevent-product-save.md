---
title: 'ACSD-49628: [!DNL Page Builder] CORS エラーが製品の保存を妨げています'
description: ACSD-49628 パッチを適用して、 [!DNL Page Builder] CORS エラーが製品の保存を妨げるAdobe Commerceの問題を修正します。
feature: Categories, Page Builder, Products
role: Admin
exl-id: 5bceddfa-5fbf-4ebe-a233-de7720764849
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 3%

---

# ACSD-49628: [!DNL Page Builder]個のCORS エラーが製品の保存を妨げます

ACSD-49628 パッチは、[!DNL Page Builder] CORS エラーによって管理者が製品を保存できない問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.32がインストールされている場合に利用できます。 パッチ IDはACSD-49628です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 - 2.4.6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

[!DNL Page Builder]個のCORS エラーが製品の保存を妨げています。

<u>複製する手順</u>:

1. 管理者としてログインします。
1. 次の権限を持つユーザーロールを作成します。

   * **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Products]**.
   * **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Categories]**.

1. *[!UICONTROL Content]*&#x200B;権限は追加しないでください。
1. 別の管理者ユーザーを作成し、上記で作成した役割をこのユーザーに割り当てます。
1. 製品を作成してログアウトします。
1. 2人目の管理者としてログインします。
1. 製品を編集して保存してみてください。

<u>期待される結果</u>:

2人目の管理者は製品を保存できますが、*[!UICONTROL Content]*&#x200B;権限がなければ&#x200B;**[!UICONTROL Edit with Page Builder]** ボタンは管理者に表示されません。

<u>実際の結果</u>:

複数の[!DNL Page Builder] エラーが発生したため、2人目の管理者は製品を保存できません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
