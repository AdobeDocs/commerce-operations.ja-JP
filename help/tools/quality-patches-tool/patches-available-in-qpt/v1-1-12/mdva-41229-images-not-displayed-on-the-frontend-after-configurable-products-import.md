---
title: MDVA-41229：バックエンドで利用できる画像が、設定可能な製品の読み込み後にフロントエンドに表示されない
description: MDVA-41229 パッチは、設定可能な製品のインポート後に、バックエンドで使用可能な画像がフロントエンドに表示されない問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.12がインストールされている場合に利用できます。 パッチ IDはMDVA-41229です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。
feature: Data Import/Export, Configuration, Products
role: Admin
exl-id: 894fdc5b-545c-4ed8-ae1b-573d1d8d3cd6
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '712'
ht-degree: 2%

---

# MDVA-41229：バックエンドで利用できる画像が、設定可能な製品の読み込み後にフロントエンドに表示されない

MDVA-41229 パッチは、設定可能な製品のインポート後に、バックエンドで使用可能な画像がフロントエンドに表示されない問題を解決します。 このパッチは、[品質パッチツール（QPT） &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.12がインストールされている場合に使用できます。 パッチ IDはMDVA-41229です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.3.2-p2および2.4.3-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

バックエンドで使用可能な画像は、設定可能な製品を読み込んだ後にフロントエンドに表示されません。

<u>複製する手順</u>:

1. クリーンなAdobe Commerceのインストール。
1. カスタム属性を追加するには、次の設定で&#x200B;**ストア** > **属性** > **製品** > **新規属性を追加**&#x200B;します。

   * プロパティ：
     * 属性のプロパティ：

       * デフォルトラベル：サイズを設定
       * ストア所有者のカタログ入力タイプ：テキストスウォッチ
       * 必要な値：いいえ
       * 製品プレビュー画像を更新：はい

     * スウォッチの管理（属性の値）:

       | デフォルトです | 管理者スウォッチ | 管理者の説明 | デフォルトのストアビュースウォッチ | デフォルトのストアビューの説明 |
       |---|---|---|---|---|
       | いいえ | 4 | 4 | 4 | 4 |
       | いいえ | 24 | 24 | 24 | 24 |
       | いいえ | 30 | 30 | 30 | 30 |
       | いいえ | 60 | 60 | 60 | 60 |
       | いいえ | 68 | 68 | 68 | 68 |

     * 高度な属性プロパティ：

       * 属性コード：set_size
       * 範囲：グローバル
       * 一意の値：いいえ
       * ストア所有者の入力検証：なし
       * 列に追加オプション：いいえ
       * フィルターオプションで使用：いいえ

   * ラベルを管理：

     * タイトル（サイズ、カラーなど）を管理

       * デフォルトのストアビュー：設定サイズ

   * ストアフロントのプロパティ：

     * 検索での使用：はい
     * 検索の重み：1
     * 詳細検索で表示：いいえ
     * ストアフロントで比較：はい
     * レイヤーナビゲーションでの使用：フィルタリング可能（結果あり）
     * 検索結果の階層化ナビゲーションでの使用：はい
     * プロモーションルール条件に使用：いいえ
     * ストアフロントのカタログページに表示：はい
     * 製品リストで使用：はい
     * 製品リストの並べ替えに使用される：いいえ

1. この属性を、製品詳細グループ（**ストア** > **属性** > **属性セット**）内のデフォルト属性セットに追加します。
1. Adobe Commerceのルートディレクトリ内のvar フォルダーに設定された画像をダウンロードします。
1. **システム**/**データ転送**>に移動し、次のオプションを使用してファイルを読み込みます。

   * 読み込み設定：

     * エンティティの種類：製品

   * 読み込み動作：

     * 読み込み動作：追加/更新
     * 検証戦略：エラー時に停止
     * 許可されるエラー数：1
     * フィールド区切り記号：`;`
     * 複数の値の区切り記号：`,`
     * 属性値定数：EMPTYVALUE
     * フィールドエンクロージャ：オフ

   * インポートするファイル：

     * 読み込むファイルを選択
     * 画像ファイルディレクトリ：空のままにします

1. ストアフロントに移動して`/product-set.html` ページを開き、異なるセットサイズを切り替えます。 Set Size 24の場合、ギャラリーはありません。

<u>期待される結果</u>:

設定可能な製品内のすべてのシンプルな製品のギャラリーは、関連するすべての画像で表示されます。

<u>実際の結果</u>:

商品のギャラリーはありません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
