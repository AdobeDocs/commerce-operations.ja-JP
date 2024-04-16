---
title: 使用方法
description: の使用方法を学ぶ [!DNL Quality Patches Tool].
exl-id: f9ad37e9-2d0f-4bc8-a98b-6d60b6f56d42
feature: Configuration, Install
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '869'
ht-degree: 0%

---

# 使用方法

この [[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) は、AdobeとMagento Open Sourceコミュニティが開発した個別のパッチを提供します。 インストールされたバージョンのAdobe CommerceまたはMagento Open Sourceで使用可能なすべての個別パッチに関する一般情報を適用、元に戻して表示できます。 パッチの開発者に関係なく、Adobe Commerce プロジェクトにパッチを適用できます。 例えば、コミュニティが開発したパッチをAdobe Commerce プロジェクトに適用できます。

これを見る [テクニカルビデオ](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/tools/quality-patch-tool.html?lang=en) Adobe Commerce用の品質向上パッチツールの使用方法についても説明します。

>[!INFO]
>
>参照： [個別パッチの適用](#apply-individual-patches) Adobe CommerceまたはMagento Open Sourceプロジェクトにパッチを適用する方法については、を参照してください。 参照： [[!DNL Quality Patches Tool]：パッチの検索](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) リリースされたパッチの完全なリストを確認します。

>[!WARNING]
>
>を使用しないことをお勧めします [!DNL Quality Patches Tool] コードが複雑になり新しいバージョンへのアップグレードが難しくなるので、多数のパッチを適用する場合。

## インストール

>[!INFO]
>
>まだインストールしていない場合は、インストールする必要があります [[!DNL Git]](https://github.com/git-guides/install-git) または [パッチ](https://man7.org/linux/man-pages/man1/patch.1.html) のインストール前に [!DNL Quality Patches Tool]. を追加 `magento/quality-patches` Composer パッケージを `composer.json` ファイル：

```bash
composer require magento/quality-patches
```

## 個々のパッチの表示

Adobe CommerceまたはMagento Open Sourceのバージョンで使用可能な個々のパッチのリストを表示するには：

```bash
./vendor/bin/magento-patches status
```

次のような出力が表示されます。

| Id | タイトル | タイプ | ステータス | 詳細 |
|--- |--- |--- |--- |--- |
| MAGECLOUD-5069 | 展開中に FPC が無効になります | オプション | 適用なし | 影響を受けたコンポーネント：<br> - magento/module-page-cache |
| MCLOUD-5650 | ファイルから読み取った後でデプロイメント設定を保持 | オプション | 適用なし | 影響を受けたコンポーネント：<br> - magento/framework |
| MCLOUD-5684 | ページネーションが機能しない – product_list_limit=all | オプション | 適用なし | 影響を受けるコンポーネント：- magento/module-elasticsearch |
| MCLOUD-5837 | ロードバランサーの問題を修正 | 非推奨 | 適用日 | 推奨交換品：MC-1 <br> 影響を受けるコンポーネント：- magento/framework |
| バンドル–2554 | 支払情報バグの設定 | オプション | 適用なし | 影響を受けたコンポーネント： <br>- amzn/amazon-pay-module |
| MC-1 | 修正点（問題 1） | オプション | 適用日 | 影響を受けたコンポーネント： <br> - magento/module-cms |
| MC-2 | 修正点（問題 2） | オプション | 適用なし | 影響を受けたコンポーネント： <br> - magento/module-cms |
| MC-3 | 修正点（問題 3） | オプション | 適用なし | 必要なパッチ：<br> - MC-2 <br>影響を受けたコンポーネント： <br>- magento/module-cms |
| MC-3-V2 | 問題 3 の修正を更新し、MC-3 パッチを置き換えました。 | オプション | 該当なし | 影響を受けたコンポーネント：  <br>- magento/module-cms |

Adobe Commerce 2.3.5。

ステータステーブルには、以下が含まれます。

- **タイプ**:
   - `Optional`  – すべてのパッチは、 [!DNL Quality Patches Tool] および [Commerce on Cloud Infrastructure ガイド > パッチの適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) パッケージは、Adobe Commerceのインストールではオプションです。
   - `Deprecated` — Adobeは個々のパッチを非推奨（廃止予定）にしました。 パッチを適用した場合は、元に戻すことをお勧めします。 元に戻す操作では、ステータステーブルからパッチも削除されます。

- **ステータス**:
   - `Applied` — パッチが適用されました。
   - `Not applied` — パッチが適用されていません。
   - `N/A`  – 競合のため、パッチのステータスを定義できません。

- **詳細**:
   - `Affected components`  – 影響を受けるモジュールのリスト。
   - `Required patches`  – 指定されたパッチが正しく動作するために適用する必要があるパッチのリスト（依存関係）。
   - `Recommended replacement`  – 非推奨（廃止予定）のパッチの代わりとして推奨されるパッチ。

>[!INFO]
>
>新しいバージョンのAdobe CommerceまたはMagento Open Sourceにアップグレードした後、パッチが新しいバージョンに含まれていない場合は、パッチを再適用する必要があります。 参照： [アップグレード後のパッチの再適用](#re-apply-patches-after-an-upgrade).

## 個別パッチの適用 {#apply-individual-patches}

>[!WARNING]
>
>実稼動環境にデプロイする前に、ステージング環境または開発環境ですべてのパッチをテストすることをお勧めします。 また、パッチを適用する前に、データをバックアップすることをお勧めします。 参照： [ファイル・システム、メディア、データベースのバックアップとロールバック](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/backup.html).

単一のパッチを適用するには、次のコマンドを実行します。 `MAGETWO-XXXX` は、ステータステーブルで指定されたパッチ ID です。

```bash
./vendor/bin/magento-patches apply MAGETWO-XXXX
```

また、追加の各パッチ ID をスペースで区切ることで、複数のパッチを同時に適用することもできます。

```bash
./vendor/bin/magento-patches apply MAGETWO-XXXX MAGETWO-YYYY
```

Adobe Commerce アプリケーションで変更内容を確認するには、パッチを適用した後でキャッシュをクリーンアップする必要があります。

```bash
./bin/magento cache:clean
```

>[!INFO]
>
>適用されたパッチのリストを別の場所に保持することを検討してください。 Adobe CommerceまたはMagento Open Sourceの新しいバージョンにアップグレードした後で、一部の機能を再適用する必要が生じる場合があります。 参照： [アップグレード後のパッチの再適用](#re-apply-patches-after-an-upgrade).

## 個々のパッチを元に戻す

>[!WARNING]
>
>実稼動環境にデプロイする前に、ステージング環境または開発環境ですべてのパッチをテストすることをお勧めします。 また、パッチを適用する前に、データをバックアップすることをお勧めします。 参照： [ファイル・システム、メディア、データベースのバックアップとロールバック](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/backup.html).

1 つのパッチを元に戻すには、次のコマンドを実行します。 `MAGETWO-XXXX` は、ステータステーブルで指定されたパッチ ID です。

```bash
./vendor/bin/magento-patches revert MAGETWO-XXXX
```

また、追加の各パッチ ID をスペースで区切ることで、複数のパッチを同時に元に戻すこともできます。

```bash
./vendor/bin/magento-patches revert MAGETWO-XXXX MAGETWO-YYYY
```

適用したすべてのパッチを元に戻すには、次の手順に従います。

```bash
./vendor/bin/magento-patches revert --all
```

Adobe Commerce アプリケーションで変更内容を確認するには、パッチを元に戻した後でキャッシュをクリーンアップする必要があります。

```bash
./bin/magento cache:clean
```

## 最新情報を取得

Adobe Commerceでは、新しい個別パッチを定期的にリリースしています。 を更新する必要があります [!DNL Quality Patches Tool] 新しい個別パッチを取得するには：

```bash
composer update magento/quality-patches
```

追加されたパッチを表示します。

>[!TIP]
>
>新しいパッチの追加が表の下部に表示されます。

```bash
./vendor/bin/magento-patches status
```

## アップグレード後のパッチの再適用 {#re-apply-patches-after-an-upgrade}

新しいバージョンのAdobe CommerceまたはMagento Open Sourceにアップグレードした場合、パッチが新しいバージョンに含まれていなければ、パッチを再適用する必要があります。

パッチを再適用するには：

1. を更新 [!DNL Quality Patches Tool]:

   ```bash
   composer update magento/quality-patches.
   ```

1. で推奨された、以前に適用したパッチのリストを開きます。 [個別パッチの適用](#apply-individual-patches).

1. パッチを適用します。

   ```bash
   ./vendor/bin/magento-patches apply MAGETWO-XXXX
   ```

   パッチを 1 つずつ適用することをお勧めします。

1. キャッシュのクリーンアップ：

   ```bash
   ./bin/magento cache:clean
   ```

   >[!INFO]
   >
   >を実行する場合 `status` コマンドを実行すると、新しいバージョンに含まれていたパッチは、使用可能なパッチの表に表示されなくなります。

## ログ

この [!DNL Quality Patches Tool] は、内のすべての操作を記録します。 `<Magento_root>/var/log/patch.log` ファイル。
