---
title: 'MDVA-39605: Redis キャッシュ TTL （有効期限）の値が正しくありません'
description: MDVA-39605 パッチは、Redis キャッシュ TTL （有効期限）の値が間違っている問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.13がインストールされている場合に利用できます。 パッチ IDはMDVA-39605です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。
feature: Cache, Console, Services
role: Admin
exl-id: 65f5d50a-e49e-4155-9d1a-3758f0c723a8
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---

# MDVA-39605: Redis キャッシュ TTL （有効期限）の値が正しくありません

MDVA-39605 パッチは、Redis キャッシュ TTL （有効期限）の値が間違っている問題を解決します。 このパッチは、[品質パッチツール（QPT） &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.13がインストールされている場合に使用できます。 パッチ IDはMDVA-39605です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.4 - 2.4.4

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

Redis キャッシュ TTL （有効期限）の値が正しくありません。

<u>複製する手順</u>:

修正をテストするには、キャッシュをフラッシュして、ストアフロントで設定可能な製品を開きます。 次に、ターミナル（コンソール）を開き、次の手順に従います。

1. 次のコマンドを実行します：`redis-cli`。
1. `KEYS "*PRICE"`を実行します（結果にはキーが1つだけ必要です（例：`zc:ti:e54_PRICE`）。 キーをコピーします。
1. `SMEMBERS`を実行し、その後に前の手順のキーを実行します（例：`SMEMBERS zc:ti:e54_PRICE`）。 結果から任意のキーをコピーします（例：e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421）。
1. 前の手順のキー名で`KEYS "*<key>"`を実行して、完全なキー名を取得します（例：`KEYS "*e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421"`）。 結果には1つのキーのみが必要です（例：`zc:k:e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421`）。 フルキー名は、プレフィックス「`zc:k:`」を持つキー名です。 次に、完全なキー名をコピーします。
1. `HGETALL`の後に手順4の完全なキー名を実行して、値を確認します。 値には、関連する設定可能な製品の関連製品のシリアル化されたデータを含める必要があります。
1. 手順4の完全なキー名の後に`TTL`を実行して、キーに有効期限があるかどうかを確認します。 結果は&#x200B;**-1**&#x200B;および&#x200B;**-2**&#x200B;とは異なり、約2592000 （30日）である必要があります。 コードの有効期限セットは1年ですが、Adobe Commerceで使用されるRedis ライブラリの最大有効期限は2592000です。

<u>期待される結果</u>:

有効期限は2592000です

<u>実際の結果</u>:

有効期限の制限は&#x200B;**-1**&#x200B;または&#x200B;**-2**&#x200B;に設定されています。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
