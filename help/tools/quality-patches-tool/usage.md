---
title: 使用状況
description: Adobe Commerceのパッチの適用と管理にQuality Patches Toolを使用する方法について説明します。 テスト、アプリケーション、パッチ管理などの手法を紹介します。
exl-id: f9ad37e9-2d0f-4bc8-a98b-6d60b6f56d42
feature: Configuration, Install
type: Troubleshooting
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '863'
ht-degree: 0%

---

# 使用状況

[[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches)は、AdobeとMagento Open Source コミュニティによって開発された個別のパッチを提供します。 インストールされているバージョンのAdobe Commerceで使用できるすべての個々のパッチに関する一般的な情報を適用、取り消し、表示できます。 誰がパッチを開発したかに関係なく、Adobe Commerce プロジェクトにパッチを適用できます。 例えば、コミュニティで開発したパッチをAdobe Commerce プロジェクトに適用できます。

この[ テクニカルビデオ ](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/tools/quality-patch-tool.html)を見て、Adobe Commerceの品質パッチツールの使用方法を学びましょう。

>[!INFO]
>
>Adobe Commerce プロジェクトにパッチを適用する手順については、[個別のパッチを適用](#apply-individual-patches)を参照してください。 「[[!DNL Quality Patches Tool]: パッチを検索](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照して、リリースされたパッチの完全なリストを確認してください。

>[!WARNING]
>
>コードの複雑さが増し、新しいバージョンへのアップグレードがより困難になるため、[!DNL Quality Patches Tool]を使用して多数のパッチを適用することはお勧めしません。

## インストール

>[!INFO]
>
>まだインストールされていない場合は、[[!DNL Git]をインストールする前に、](https://github.com/git-guides/install-git)[または](https://man7.org/linux/man-pages/man1/patch.1.html) パッチ [!DNL Quality Patches Tool]をインストールする必要があります。 `magento/quality-patches` Composer パッケージを`composer.json` ファイルに追加します。

```bash
composer require magento/quality-patches
```

## 個別のパッチを表示

お使いのバージョンのAdobe Commerceで使用可能な個々のパッチのリストを表示するには、次の手順に従います。

```bash
./vendor/bin/magento-patches status
```

次のような出力が表示されます。

| Id | タイトル | タイプ | ステータス | 詳細 |
|--- |--- |--- |--- |--- |
| MAGECLOUD-5069 | デプロイメント中にFPCが無効になる | オプション | 未適用 | 影響を受けるコンポーネント：<br> - magento/module-page-cache |
| MCLOUD-5650 | ファイルから読み取った後でデプロイメント設定を保持する | オプション | 未適用 | 影響を受けるコンポーネント：<br> - magento/framework |
| MCLOUD-5684 | ページネーションが機能しない – product_list_limit=all | オプション | 未適用 | 影響を受けるコンポーネント：- magento/module-elasticsearch |
| MCLOUD-5837 | ロードバランサーの問題を修正 | 非推奨 | 適用 | 推奨される代替品：MC-1 <br>影響を受けるコンポーネント：- magento/framework |
| バンドル–2554 | 決済情報のバグを設定 | オプション | 未適用 | 影響を受けるコンポーネント：<br>- amzn/amazon-pay-module |
| MC-1 | 問題1の修正 | オプション | 適用 | 影響を受けるコンポーネント：<br> - magento/module-cms |
| MC-2 | 問題2の修正 | オプション | 未適用 | 影響を受けるコンポーネント：<br> - magento/module-cms |
| MC-3 | 問題3の修正 | オプション | 未適用 | 必要なパッチ：<br> - MC-2 <br>影響を受けるコンポーネント：<br>- magento/module-cms |
| MC-3-V2 | 問題3の修正を更新し、MC-3 パッチを置き換えました | オプション | 該当なし | 影響を受けるコンポーネント：<br>- magento/module-cms |

Adobe Commerce 2.3.5.

ステータステーブルには次のものが含まれます。

- **種類**:
   - `Optional` — [!DNL Quality Patches Tool]および[Commerce on Cloud Infrastructure ガイド > パッチの適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) パッケージのすべてのパッチは、Adobe Commerce インストールではオプションです。
   - `Deprecated` — Adobeは個別のパッチを非推奨にしました。 パッチを適用した場合は、元に戻すことをお勧めします。 復元操作では、ステータステーブルからもパッチが削除されます。

- **ステータス**:
   - `Applied` — パッチが適用されました。
   - `Not applied` — パッチが適用されていません。
   - `N/A` – 競合のため、パッチのステータスを定義できません。

- **詳細**:
   - `Affected components` – 影響を受けるモジュールのリスト。
   - `Required patches` – 指定されたパッチが正しく動作するために適用する必要があるパッチのリスト（依存関係）。
   - `Recommended replacement` – 非推奨パッチの推奨される代替パッチです。

>[!INFO]
>
>新しいバージョンのAdobe Commerceにアップグレードした後、新しいバージョンにパッチが含まれていない場合は、パッチを再適用する必要があります。 アップグレード後に[ パッチを再適用するを参照してください](#re-apply-patches-after-an-upgrade)。

## 個別のパッチを適用 {#apply-individual-patches}

>[!WARNING]
>
>実稼動にデプロイする前に、ステージング環境または開発環境のすべてのパッチをテストすることをお勧めします。 パッチを適用する前に、データをバックアップすることをお勧めします。 [ ファイルシステム、メディア、データベースのバックアップとロールバック ](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/backup.html)を参照してください。

単一のパッチを適用するには、次のコマンドを実行します。ここで、`MAGETWO-XXXX`はステータステーブルで指定されたパッチ IDです。

```bash
./vendor/bin/magento-patches apply MAGETWO-XXXX
```

複数のパッチを同時に適用するには、追加のパッチ IDをスペースで区切ります。

```bash
./vendor/bin/magento-patches apply MAGETWO-XXXX MAGETWO-YYYY
```

パッチを適用した後にキャッシュをクリーニングして、Adobe Commerce アプリケーションの変更内容を確認する必要があります。

```bash
./bin/magento cache:clean
```

>[!INFO]
>
>適用されたパッチのリストを別の場所に保存することを検討してください。 Adobe Commerceの新しいバージョンにアップグレードした後、一部を再適用する必要がある場合があります。 アップグレード後に[ パッチを再適用するを参照してください](#re-apply-patches-after-an-upgrade)。

## 個々のパッチを元に戻す

>[!WARNING]
>
>実稼動にデプロイする前に、ステージング環境または開発環境のすべてのパッチをテストすることをお勧めします。 パッチを適用する前に、データをバックアップすることをお勧めします。 [ ファイルシステム、メディア、データベースのバックアップとロールバック ](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/backup.html)を参照してください。

1つのパッチを元に戻すには、次のコマンドを実行します。ここで、`MAGETWO-XXXX`はステータステーブルで指定されたパッチ IDです。

```bash
./vendor/bin/magento-patches revert MAGETWO-XXXX
```

また、追加のパッチ IDをスペースで区切ることで、複数のパッチを同時に元に戻すことができます。

```bash
./vendor/bin/magento-patches revert MAGETWO-XXXX MAGETWO-YYYY
```

適用したすべてのパッチを元に戻すには：

```bash
./vendor/bin/magento-patches revert --all
```

パッチを元に戻した後にキャッシュをクリーニングして、Adobe Commerce アプリケーションの変更内容を確認する必要があります。

```bash
./bin/magento cache:clean
```

## アップデートする

Adobe Commerceは、新しい個別パッチを定期的にリリースします。 新しい個別のパッチを取得するには、[!DNL Quality Patches Tool]を更新する必要があります。

```bash
composer update magento/quality-patches
```

追加されたパッチを表示します。

>[!TIP]
>
>新しい追加パッチがテーブルの下部に表示されます。

```bash
./vendor/bin/magento-patches status
```

## アップグレード後にパッチを再適用する {#re-apply-patches-after-an-upgrade}

新しいバージョンのAdobe Commerceにアップグレードする場合、新しいバージョンにパッチが含まれていない場合は、パッチを再適用する必要があります。

パッチを再適用するには：

1. [!DNL Quality Patches Tool]を更新します。

   ```bash
   composer update magento/quality-patches.
   ```

1. 以前に適用されたパッチのリストを開きます。これは、[個別のパッチを適用](#apply-individual-patches)で推奨されました。

1. パッチを適用します。

   ```bash
   ./vendor/bin/magento-patches apply MAGETWO-XXXX
   ```

   ベストプラクティスは、パッチを1つずつ適用することです。

1. キャッシュをクリーニングします。

   ```bash
   ./bin/magento cache:clean
   ```

   >[!INFO]
   >
   >`status` コマンドを実行すると、新しいバージョンに含まれていたパッチは、使用可能なパッチのテーブルに表示されなくなります。

## ログ

[!DNL Quality Patches Tool]は、`<Magento_root>/var/log/patch.log` ファイル内のすべての操作をログに記録します。
