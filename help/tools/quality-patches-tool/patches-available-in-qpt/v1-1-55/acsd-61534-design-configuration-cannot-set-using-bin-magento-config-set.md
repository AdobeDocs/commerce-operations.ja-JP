---
title: 'ACSD-61534: bin/magento config:setを使用してデザイン設定を設定できず、ロックされた値をフォーム操作で変更できます'
description: 「bin/magento config:set」コマンドを使用してデザイン設定を設定できず、ロックされた値をフォーム操作で変更できるAdobe Commerceの問題を修正するには、ACSD-61534 パッチを適用します。
feature: Configuration
role: Admin, Developer
exl-id: 5bba3f05-e017-42b2-8a89-5471afb84ff3
type: Troubleshooting
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# ACSD-61534: `bin/magento config:set`を使用してデザイン設定を設定できず、ロックされた値をフォーム操作で変更できます

ACSD-61534 パッチは、`bin/magento config:set` コマンドを使用してデザイン設定を設定できず、ロックされた値をフォーム操作で変更できる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55がインストールされている場合に利用できます。 パッチ IDはACSD-61534です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p2

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

デザイン設定は`bin/magento config:set` コマンドを使用して設定できず、ロックされた値はフォーム操作で変更できます。 このパッチでは、`--lock-env`または`--lock-conf`のコマンドラインツール（CLI）から設定されたロックされた値を更新できません。

<u>複製する手順</u>:

1. `CONFIG_WEBSITESBASEDESIGNHEAD_INCLUDES`などのクラウド環境変数を使用して、設定値をロックします。
1. *[!UICONTROL Admin]* パネルに移動します。
1. **[!UICONTROL Content]** > **[!UICONTROL Design]** > **[!UICONTROL Configuration]**&#x200B;に移動します。
1. 2行目の&#x200B;**[!UICONTROL Global/Main website]**&#x200B;付近の&#x200B;**[!UICONTROL Edit]**&#x200B;をクリックします。
1. ストアビューのテーマを編集します。
1. HTML ヘッドを開きます。
1. 開発者ツールを使用して、無効な&#x200B;**[!UICONTROL Scripts and Style Sheets]** フィールドを有効にします。
1. 値を変更して保存します。

<u>期待される結果</u>:

ロックされた値は保存できません。

<u>実際の結果</u>:

テーブル `core_config_data`には、`design/head/includes`の更新された値が含まれています。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
