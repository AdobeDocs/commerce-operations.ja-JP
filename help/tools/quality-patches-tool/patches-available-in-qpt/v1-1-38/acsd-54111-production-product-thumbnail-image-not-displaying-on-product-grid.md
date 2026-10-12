---
title: ACSD-54111：製品のサムネール画像が表示されない
description: ACSD-54111 パッチを適用して、すべての画像がデフォルトの製品プレースホルダーイメージに置き換えられるAdobe Commerceの問題を修正します。
feature: Products
role: Admin, Developer
exl-id: 4615ebf6-aa68-4d49-8d91-e9756b3d4a05
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
source-wordcount: '379'
ht-degree: 0%
---
# ACSD-54111：製品のサムネール画像が表示されない

ACSD-54111 パッチでは、すべての画像がデフォルトの製品プレースホルダー画像に置き換えられる問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.38がインストールされている場合に利用できます。 パッチ IDはACSD-54111です。 この問題は、Adobe Commerce 2.4.6で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法）:2.4.5-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法）:2.4.2 ～ 2.4.5-p4

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

製品のサムネール画像が表示されない。

<u>複製する手順</u>:

1. **[!UICONTROL Content]** > **[!UICONTROL Design]** > **[!UICONTROL Configuration]** > **[!UICONTROL Edit Theme]** > **[!UICONTROL Product Image Watermarks]** > **[!UICONTROL Thumbnail]**&#x200B;に移動します。
1. サムネールを含む画像をアップロードし、画像の位置を&#x200B;*[!UICONTROL Center]*&#x200B;に設定します。
1. **[!UICONTROL Save Configuration]**&#x200B;をクリックします。
1. キャッシュをクリアします。
1. ゲスト/顧客としてストアフロントに移動します。
1. 商品をカートに追加する。
1. コンソールから`bin/magento catalog:image:resize`を実行します。
1. フロントエンドのミニカートまたはバックエンドの商品グリッドを開いて、画像のサムネールが表示されているかどうかを確認します。

<u>期待される結果</u>:

製品画像は、プレースホルダー画像に置き換えられません。

<u>実際の結果</u>:

製品画像は、デフォルトの製品プレースホルダー画像に置き換えられます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
