---
title: ACSD-66093：ゲスト顧客名フィールドでは、メール入力が許可されており、その結果注文メールが無効になります
description: ACSD-66093 パッチを適用すると、Adobe Commerceの問題を修正できます。この問題では、「Guest customer **[!UICONTROL First Name]**」および「**[!UICONTROL Last Name]**」フィールドにメールアドレスを入力して、無効な注文確認メールを送信できます。
feature: Checkout
role: Admin, Developer
type: Troubleshooting
exl-id: 30790492-330e-4810-8069-fce87b40ebb2
source-git-commit: b1912bbc5aabd36067563326ee5c6bb84e14441d
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-66093：ゲスト顧客名フィールドでは、メール入力が許可されており、その結果注文メールが無効になります

ACSD-66093 パッチでは、ゲスト顧客の **[!UICONTROL First Name]** フィールドと **[!UICONTROL Last Name]** フィールドにメールアドレスを入力すると、注文確認メールが無効になる可能性がある問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65 がインストールされている場合に使用できます。 パッチ ID は ACSD-66093 です。 この問題はAdobe Commerce 2.4.8 で修正されました。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p11

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

ゲスト顧客の **[!UICONTROL First Name]** フィールドと **[!UICONTROL Last Name]** フィールドにメールアドレスを入力する際に、注文確認メールで無効な情報が返されることがありました。

<u> 再現手順 </u>:

1. ゲスト顧客として商品を買い物かごに追加します。
2. チェックアウトに移動します。
3. メールアドレスを「test1@gmail.co」に入力します。
4. **[!UICONTROL First Name]** に「<test2@gmail.co>」を入力します。
5. **[!UICONTROL Last Name]** に「<test3@gmail.co>」を入力します。
6. その他の必須フィールドに入力します。
7. 注文する。

<u> 期待される結果 </u>:

*First Name is not valid!（名が無効です！）のように、**[!UICONTROL First Name]**&#x200B;および&#x200B;**[!UICONTROL Last Name]**&#x200B;フィールドが無効であることを示す検証メッセージが表示されます。 と姓が無効です。* と注文しないでください。

<u> 実際の結果 </u>:

注文が行われます。
**[!UICONTROL First Name]** および **[!UICONTROL Last Name]** フィールドは入力時に保存されます。
注文確認メールが 3 通のメール（test1@gmail.co、test2@gmail.co、test3@gmail.co）すべてに送信されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
