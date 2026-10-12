---
title: ACSD-60632：注文が試行されるたびにアドレスが保存される
description: ACSD-60632 パッチを適用して、注文が正常に作成されたかどうかに関係なく、注文の配置が試行されるたびに新しいアドレスが保存されるAdobe Commerceの問題を修正します。
feature: Orders, Products
role: Admin, Developer
exl-id: 9b623a1c-594f-47ed-82b4-d11ba20f3a58
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%
---
# ACSD-60632：注文が試行されるたびにアドレスが保存される

ACSD-60632 パッチは、注文が正常に作成されたかどうかに関係なく、注文の配置が試行されるたびに新しいアドレスが保存される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.51がインストールされている場合に利用できます。 パッチ IDはACSD-60632です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p8

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p8 - 2.4.7-p2

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

注文の配置が試行されるたびに、注文が正常に作成されたかどうかに関係なく、新しいアドレス入力がシステムに保存されます。

<u>複製する手順</u>:

1. **[!DNL PayPal Payflow Link]**&#x200B;支払い方法を有効にする：
   * ローカルマシンでは、実際のIPがなければ、システムは[!DNL PayPal Payflow Link]からAPI呼び出しを受信できません。
1. シンプルな商品の作成。
1. アドレスなしで登録済み顧客を作成します。
1. 商品をカートに追加します。
1. 決済プロセスに進む。
1. アドレスを入力してください。 最初のアドレスがこの手順で作成されていることを確認します。
1. *[!UICONTROL Review and Payments]* ページで、**[!UICONTROL Credit Card (Payflow Link)]** ラジオボタンを選択します。
1. **[!UICONTROL Continue]**&#x200B;をクリックします。
   * チェックアウトページは、事前入力されたアドレスと想定されるエラーメッセージで&#x200B;*[!UICONTROL Review and Payments]* ステップに戻ります。
1. もう一度&#x200B;*[!UICONTROL Credit Card (Payflow Link)]* ラジオボタンを選択します。
1. **[!UICONTROL Continue]**&#x200B;をクリックします。

<u>期待される結果</u>:

2回目の注文のプレースメントでは、新しいアドレスは作成されません。

<u>実際の結果</u>:

新しいアドレスは、注文の配置が試行されるたびに作成されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ja)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
