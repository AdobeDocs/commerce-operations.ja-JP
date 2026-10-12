---
title: ACSD-49389：受け取り準備ができていない場合にAPIで送信される受け取り用メールの準備
description: ACSD-49389 パッチを適用して、注文が受け取り準備ができていない場合に受け取り準備完了メールがAPIによって送信されるAdobe Commerceの問題を修正します。
feature: REST, Communications
role: Admin
exl-id: d1bc430a-3021-40d1-9091-db8ed9125619
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bb03f6c4-cab9-560e-9d02-5816e1808d17
    internal-label: Communications
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
subfeature_v2:
  - id: e0ca0e7a-9738-48d1-b98b-615468ab4aaf
    internal-label: REST API
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%
---
# ACSD-49389：受け取り準備ができていない場合にAPIで送信される受け取り用メールの準備

ACSD-49389 パッチは、注文が受け取り準備ができていない場合にAPIによって受け取り準備完了メールが送信される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.29がインストールされている場合に利用できます。 パッチ IDはACSD-49389です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 - 2.4.6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[QPT ランディングページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

注文の受け取り準備が整っていない場合、APIによって受け取り準備完了メールが送信されます。

<u>複製する手順</u>:

1. *[!UICONTROL In-Store Delivery]* メソッドを有効にします。
1. 受け取り場所が有効になっているストックソースを作成します。
1. 上記のソースでメイン web サイトを使用して新しいストックを作成します。
1. 同じソースを割り当てる製品を作成します。
1. 在庫数量を設定= 1。
1. ストアフロントの&#x200B;*[!UICONTROL In-Store Delivery]* メソッドを使用して、手順4で作成した製品をチェックアウトします。
1. 注文の請求書を作成します。
1. 商品の数量を&#x200B;*0*&#x200B;に設定し、在庫切れにします。
1. 次のAPI リクエストを投稿します。

```json
{
    "orderIds": [
        1
    ]
}
```

<u>期待される結果</u>:

受け取り準備完了の電子メールは送信されません。

<u>実際の結果</u>:

APIが&#x200B;*注文は受け取り準備ができていませんが*&#x200B;電子メールを受け取る準備ができていることを返します。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[!DNL Quality Patches Tool] ガイドの[QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で使用可能なパッチを参照してください。
