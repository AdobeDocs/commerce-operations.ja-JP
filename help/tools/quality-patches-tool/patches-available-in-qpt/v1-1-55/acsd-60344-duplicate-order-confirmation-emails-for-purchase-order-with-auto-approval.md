---
title: ACSD-60344：自動承認を使用して[!UICONTROL Purchase Order]を使用すると、注文確認メールが重複する
description: 自動承認付きの[!UICONTROL Purchase Order]を使用する際に重複した注文確認メールが送信されるAdobe Commerceの問題を修正するには、ACSD-60344 パッチを適用します。
feature: Purchase Orders
role: Admin, Developer
exl-id: c4d415ee-b1ac-4094-9209-19b91f9a7666
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# ACSD-60344：自動承認を使用して&#x200B;*[!UICONTROL Purchase Order]*&#x200B;を使用すると、注文確認メールが重複する

ACSD-60344 パッチは、自動承認付きの&#x200B;*[!UICONTROL Purchase Order]*&#x200B;を使用する際に重複した注文確認メールが送信される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55がインストールされている場合に利用できます。 パッチ IDはACSD-60344です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p4

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3


>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

自動承認で&#x200B;*[!UICONTROL Purchase Order]*&#x200B;を使用すると、重複した注文確認メールが送信されます。

<u>前提条件</u>

B2B モジュールと&#x200B;*[!UICONTROL Purchase Order]*&#x200B;を有効にします。

<u>複製する手順</u>:

1. 会社アカウントを作成し、その&#x200B;*[!UICONTROL Purchase Order]*&#x200B;を有効にします。
1. 通常のユーザーアカウントを作成し、会社ユーザーとして会社アカウントに追加します。
1. このアカウントを使用して注文します。
1. cronを実行してメールを確認します。

<u>期待される結果</u>:

1回の注文につき1件の注文確認メールのみが送信されます。

<u>実際の結果</u>:

2通の注文確認メールが届きます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。


## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
