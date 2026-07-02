---
title: ACSD-53643：発注の際に誤った合計が表示される
description: 無効な商品または在庫切れの商品を含む注文を発注する際に、注文の合計数が正しくないAdobe Commerceの問題を修正するには、ACSD-53643 パッチを適用します。
feature: B2B
role: Admin, Developer
exl-id: 72b52695-ef3c-4143-9e77-901463d4a9ed
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 0%

---

# ACSD-53643：発注の際に誤った合計が表示される

ACSD-53643 パッチは、無効な製品または在庫切れの製品で発注する際に、注文の合計が誤っている問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.41がインストールされている場合に利用できます。 パッチ IDはACSD-53643です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

無効な製品または在庫切れの製品を使用して発注する場合、注文合計が正しくありません。

<u>複製する手順</u>:

1. *[!UICONTROL B2B]*&#x200B;と&#x200B;*[!UICONTROL Inventory]*&#x200B;をインストールします。
1. **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B]**&#x200B;に移動し、**[!UICONTROL Company]** = *はい*&#x200B;と&#x200B;**[!UICONTROL Purchase Order]** = *はい*&#x200B;を設定します。
1. 設定キャッシュをクリアします。
1. 新しい会社を作成し、それをアクティブ化して、会社の&#x200B;*[!UICONTROL Purchase order]*&#x200B;を有効にします。
1. 会社の新しいユーザーを作成します。
1. *承認ルール*&#x200B;を作成して、*1 USD*&#x200B;を超えるすべての注文を会社の管理者が承認します。
1. 追加のソースを作成。
1. 新しい会社ユーザーとしてログインします。
1. 2つの商品をカートに入れて発注します。
1. 2番目の製品を無効にします。
1. 会社の管理者としてログインします。
1. 発注を開き、発注に両方の製品が含まれており、合計が両方の製品であることを確認します。
1. 発注を承認します。
1. 注文する。
1. 注文の詳細を開きます。

<u>期待される結果</u>:

* 注文の商品が&#x200B;*無効*&#x200B;または&#x200B;*在庫切れ*&#x200B;の場合でも、注文を行うことはできません。
* *[!UICONTROL Place Order]* ボタンは非表示です。

<u>実際の結果</u>:

配置された注文には最初のアクティブな製品のみが含まれますが、注文合計は両方の製品について計算されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
