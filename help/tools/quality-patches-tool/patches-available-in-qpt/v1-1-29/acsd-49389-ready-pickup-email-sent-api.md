---
title: ACSD-49389：受け取り準備ができていない場合にAPIで送信される受け取り用メールの準備
description: ACSD-49389 パッチを適用して、注文が受け取り準備ができていない場合に受け取り準備完了メールがAPIによって送信されるAdobe Commerceの問題を修正します。
feature: REST, Communications
role: Admin
exl-id: d1bc430a-3021-40d1-9091-db8ed9125619
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# ACSD-49389：受け取り準備ができていない場合にAPIで送信される受け取り用メールの準備

ACSD-49389 パッチは、注文が受け取り準備ができていない場合にAPIによって受け取り準備完了メールが送信される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29がインストールされている場合に利用できます。 パッチ IDはACSD-49389です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 - 2.4.6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[QPT ランディングページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

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
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[!DNL Quality Patches Tool] ガイドの[QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で使用可能なパッチを参照してください。
