---
title: 'ACSD-46815: コンパクトな戦略を使用すると、静的コンテンツのデプロイに失敗する'
description: コンパクトな方法を使用すると、静的コンテンツデプロイが失敗するAdobe Commerceの問題を修正するには、ACSD-46815 パッチを適用します。
feature: Deploy, Page Content, SCD
role: Admin
exl-id: 66941a83-daf8-4bb2-a575-b615e1c5dc7c
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# ACSD-46815: コンパクトな戦略を使用すると、静的コンテンツのデプロイが失敗する

ACSD-46815 パッチは、コンパクトな戦略を使用すると静的コンテンツのデプロイメントが失敗する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://support.magento.com/hc/en-us/articles/360047139492) 1.1.20がインストールされている場合に利用できます。 パッチ IDはACSD-46815です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

コンパクトな戦略でデプロイすると、静的コンテンツのデプロイに失敗します。

<u>複製する手順</u>:

1. 次のコマンドを実行して、コンパクトな戦略で静的コンテンツをデプロイします。

```shell
bin/magento setup:static-content:deploy -f -s compact
```

<u>期待される結果</u>:

静的コンテンツのデプロイメントはエラーなしで完了します。

<u>実際の結果</u>:

コンパクトな戦略では、静的コンテンツの展開に失敗します。 デプロイメントプロセス中に次のエラーが発生します。*/app/pub/static/adminhtml/Magento/base/default/./node_modules/@spectrum-css/vars/dist/spectrum-global.css ファイルの内容を読み取ることができません。*

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce: [ アップグレードとパッチ > パッチの適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) （開発者用ドキュメント）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
