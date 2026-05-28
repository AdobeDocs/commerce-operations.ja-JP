---
title: 'ACSD-66093: ゲスト顧客名フィールドでメール入力が許可され、注文メールが無効になる'
description: ACSD-66093 パッチを適用して、Guest カスタマー**[!UICONTROL First Name]および**[!UICONTROL Last Name]のフィールドに電子メールアドレスを入力し**無効な注文確認メールを送信できるAdobe Commerceの問題を修正**ます。
feature: Checkout
role: Admin, Developer
type: Troubleshooting
exl-id: 30790492-330e-4810-8069-fce87b40ebb2
source-git-commit: b1912bbc5aabd36067563326ee5c6bb84e14441d
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-66093: ゲスト顧客名フィールドでメール入力が許可され、注文メールが無効になる

ACSD-66093 パッチでは、ゲスト顧客の&#x200B;**[!UICONTROL First Name]**&#x200B;および&#x200B;**[!UICONTROL Last Name]**&#x200B;のフィールドに電子メールアドレスを入力すると、注文確認メールが無効になる問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65がインストールされている場合に利用できます。 パッチ IDはACSD-66093です。 この問題は、Adobe Commerce 2.4.8で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p11

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

ゲスト顧客の&#x200B;**[!UICONTROL First Name]**&#x200B;および&#x200B;**[!UICONTROL Last Name]**&#x200B;のフィールドに電子メールアドレスを入力できたため、注文確認メールが無効になりました。

<u>複製する手順</u>:

1. ゲスト顧客として商品をカートに追加します。
2. 決済プロセスを見る。
3. メールアドレスに「test1@gmail.co」を入力します。
4. **[!UICONTROL First Name]**&#x200B;に「<test2@gmail.co>」を入力します。
5. **[!UICONTROL Last Name]**&#x200B;に「<test3@gmail.co>」を入力します。
6. その他の必須フィールドに入力します。
7. 発注：

<u>期待される結果</u>:

**[!UICONTROL First Name]**&#x200B;および&#x200B;**[!UICONTROL Last Name]** フィールドが&#x200B;*名のように無効であることを示す検証メッセージが表示されます。 姓が無効です！* そして注文は行われるべきではありません。

<u>実際の結果</u>:

注文が行われます。
**[!UICONTROL First Name]**&#x200B;および&#x200B;**[!UICONTROL Last Name]**個のフィールドが入力済みとして保存されます。
注文確認メールは、test1@gmail.co、test2@gmail.co、test3@gmail.coの3つすべてのメールに送信されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
