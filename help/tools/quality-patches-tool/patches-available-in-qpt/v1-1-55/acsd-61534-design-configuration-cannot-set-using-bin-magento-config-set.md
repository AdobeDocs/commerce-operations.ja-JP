---
title: 'ACSD-61534: bin/magento config:set を使用してデザイン設定を設定したり、ロックされた値をフォーム操作で変更したりすることはできません'
description: ACSD-61534 パッチを適用すると、「bin/magento config:set」コマンドを使用してデザイン設定を設定できず、ロックされた値をフォーム操作で変更できるAdobe Commerceの問題を修正できます。
feature: Configuration
role: Admin, Developer
exl-id: 5bba3f05-e017-42b2-8a89-5471afb84ff3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-61534: `bin/magento config:set` を使用してデザイン設定を設定したり、ロックされた値をフォーム操作で変更したりすることはできません

ACSD-61534 パッチは、`bin/magento config:set` コマンドを使用してデザイン設定を設定できず、ロックされた値をフォーム操作で変更できる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 がインストールされている場合に使用できます。 パッチ ID は ACSD-61534 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p2

**Adobe Commerce バージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

デザイン設定は `bin/magento config:set` コマンドを使用して設定できず、ロックされた値はフォーム操作で変更できます。 このパッチを適用すると、`--lock-env` または `--lock-conf` を使用してコマンドラインツール（CLI）から設定されたロックされた値は更新できません。

<u> 再現手順 </u>:

1. クラウド環境変数（`CONFIG_WEBSITESBASEDESIGNHEAD_INCLUDES` など）を使用して設定値をロックします。
1. *[!UICONTROL Admin]* パネルに移動します。
1. **[!UICONTROL Content]**/**[!UICONTROL Design]**/**[!UICONTROL Configuration]** に移動します。
1. 2 行目の **[!UICONTROL Edit]** の近くにある **[!UICONTROL Global/Main website]** をクリックします。
1. ストア表示のテーマを編集します。
1. HTMLのヘッドを開きます。
1. 開発者ツールを使用して、「無効な **[!UICONTROL Scripts and Style Sheets]**」フィールドを有効にします。
1. 値を変更して保存します。

<u> 期待される結果 </u>:

ロックされた値は保存できません。

<u> 実際の結果 </u>:

テーブル `core_config_data` には、`design/head/includes` の更新された値が含まれています。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
