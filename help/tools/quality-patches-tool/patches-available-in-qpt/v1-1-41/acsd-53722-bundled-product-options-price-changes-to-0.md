---
title: ACSD-53722：バンドルされた製品オプションの価格が$0に変更されました
description: ACSD-53722 パッチを適用して、異なるスコープのスケジュールされた更新がアクティブになると、バンドルされた製品オプションの価格が0 ドルに変わるAdobe Commerceの問題を修正します。
feature: Products
role: Admin, Developer
exl-id: 2e974a6a-0c79-442f-9b45-b4edf831a052
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
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
source-wordcount: '446'
ht-degree: 0%
---
# ACSD-53722：バンドルされた製品オプションの価格が$0に変更されました

ACSD-53722 パッチは、異なるスコープのスケジュールされた更新がアクティブになると、バンドルされた製品オプションの価格が0 ドルに変更される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.41がインストールされている場合に利用できます。 パッチ IDはACSD-53722です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

異なるスコープのスケジュールされた更新がアクティブになると、バンドルされた製品オプションの価格が0 ドルに変更されます。

<u>複製する手順</u>:

1. AとBの2つのweb サイトを作成する：
1. **[!UICONTROL Catalog]** > **[!UICONTROL Price]** > **[!UICONTROL Catalog Price Scope]** = **[!UICONTROL Website]**&#x200B;の設定を設定します。
1. web サイト AとBで、固定価格のバンドル商品を制作する：

   * バンドルされた製品価格=固定= *0*

1. バンドルのドロップダウンオプションとして1つのシンプルな製品を追加します。 以下の価格を設定します。

   * シンプルな商品のすべてのストアビューの価格はバンドルオプション = *120*
   * シンプルな商品のweb サイト バンドルオプション内の価格= *130*
   * バンドルオプション内のシンプルな製品のweb サイト Bの価格= *140*

1. 更新をスケジュールして、web サイト Aでバンドル製品を無効にします。

<u>期待される結果</u>:

web サイト Aの予定された更新は、web サイト Bの価格には影響しません。

<u>実際の結果</u>:

スケジュールされた更新後、web サイト Bのバンドル製品オプションの価格が&#x200B;**$0**&#x200B;に変更されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
