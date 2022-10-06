---
title: 使用状況
description: 使用方法 [!DNL Quality Patches Tool].
source-git-commit: e35469adb1b3278cf787416e1bc829fae9979efc
workflow-type: tm+mt
source-wordcount: '901'
ht-degree: 0%

---

# 使用状況

この [[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) は、AdobeとMagento Open Source・コミュニティが開発した個々のパッチを提供します。 インストールされたAdobe CommerceまたはMagento Open Sourceで使用可能なすべての個々のパッチに関する一般情報を、適用、元に戻し、表示できます。 パッチの開発者に関係なく、Adobe CommerceおよびMagento Open Sourceプロジェクトにパッチを適用できます。 例えば、コミュニティが開発したパッチをAdobe Commerceプロジェクトに適用できます。


ご覧ください [技術ビデオ](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/tools/quality-patch-tool.html?lang=en) Adobe CommerceとMagento Open Sourceの品質パッチツールを使用する方法について説明します。

>[!INFO]
>
>詳しくは、 [個々のパッチの適用](#apply-individual-patches) を参照してください。 詳しくは、 [利用可能なパッチ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) リリース済みのパッチの完全なリストを確認する。

>[!WARNING]
>
>この [!DNL Quality Patches Tool] コードの複雑さが増し、新しいバージョンへのアップグレードがより困難になるので、多数のパッチを適用する場合。

## インストール

>[!INFO]
>
>まだインストールされていない場合は、 [[!DNL Git]](https://github.com/git-guides/install-git) または [パッチ](https://man7.org/linux/man-pages/man1/patch.1.html) インストール前 [!DNL Quality Patches Tool]. を `magento/quality-patches` Composer パッケージを `composer.json` ファイル：

```bash
composer require magento/quality-patches
```

## 個々のパッチの表示

お使いのバージョンのAdobe CommerceまたはMagento Open Sourceで使用可能な個々のパッチのリストを表示するには：

```bash
./vendor/bin/magento-patches status
```

次のような出力が表示されます。

| ID | タイトル | タイプ | ステータス | 詳細 |
|--- |--- |--- |--- |--- |
| MAGECLOUD-5069 | デプロイメント中に FPC が無効になっています | オプション | 未適用 | 影響を受けるコンポーネント：<br> - magento/module-page-cache |
| MCLOUD-5650 | ファイルから読み取った後、デプロイメント設定を保持 | オプション | 未適用 | 影響を受けるコンポーネント：<br> - magento/framework |
| MCLOUD-5684 | ページネーションが機能しない — product_list_limit=all | オプション | 未適用 | 影響を受けるコンポーネント：- magento/module-elasticsearch |
| MCLOUD-5837 | ロードバランサーの問題を修正 | 非推奨 | 適用済み | 推奨される置換：MC-1 <br> 影響を受けるコンポーネント：- magento/framework |
| BUNDLE-2554 | 支払情報の設定のバグ | オプション | 未適用 | 影響を受けるコンポーネント： <br>- amzn/amazon-pay-module |
| MC-1 | 問題 1 を修正しました。 | オプション | 適用済み | 影響を受けるコンポーネント： <br> - magento/module-cms |
| MC-2 | 問題 2 の修正 | オプション | 未適用 | 影響を受けるコンポーネント： <br> - magento/module-cms |
| MC-3 | 問題 3 を修正しました。 | オプション | 未適用 | 必要なパッチ：<br> - MC-2 <br>影響を受けるコンポーネント： <br>- magento/module-cms |
| MC-3-V2 | 問題 3 の修正を更新し、MC-3 パッチに代わるものにしました。 | オプション | 該当なし | 影響を受けるコンポーネント：  <br>- magento/module-cms |

Adobe Commerce 2.3.5。

ステータステーブルには、以下が含まれます。

- **タイプ**:
   - `Optional` — [!DNL Quality Patches Tool] そして [クラウドパッチ](https://devdocs.magento.com/cloud/project/project-patch.html) パッケージは、Adobe CommerceおよびMagento Open Sourceのインストールではオプションです。
   - `Deprecated` —Adobeは個々のパッチを非推奨にしました。 パッチを適用した場合は、そのパッチを元に戻すことをお勧めします。 元に戻す操作では、パッチもステータステーブルから削除されます。

- **ステータス**:
   - `Applied`  — パッチが適用されています。
   - `Not applied`  — パッチが適用されていません。
   - `N/A`  — 競合が発生したため、パッチのステータスを定義できません。

- **詳細**:
   - `Affected components`  — 影響を受けるモジュールのリスト。
   - `Required patches`  — 指定されたパッチが正しく動作するために適用する必要があるパッチのリスト（依存関係）。
   - `Recommended replacement`  — 非推奨のパッチに対する推奨の置き換えであるパッチ。

>[!INFO]
>
>Adobe CommerceまたはMagento Open Sourceの新しいバージョンにアップグレードした後、そのパッチが新しいバージョンに含まれていない場合は、パッチを再適用する必要があります。 詳しくは、 [アップグレード後にパッチを再適用](#re-apply-patches-after-an-upgrade).

## 個々のパッチの適用 {#apply-individual-patches}

>[!WARNING]
>
>実稼動環境にデプロイする前に、ステージング環境または開発環境ですべてのパッチをテストすることをお勧めします。 また、パッチを適用する前にデータをバックアップすることをお勧めします。 詳しくは、 [ファイル・システムのバックアップとロールバック](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-backup.html).

1 つのパッチを適用するには、次のコマンドを実行します。 `MAGETWO-XXXX` は、ステータステーブルで指定されたパッチ ID です。

```bash
./vendor/bin/magento-patches apply MAGETWO-XXXX
```

また、追加の各パッチ ID をスペースで区切ることで、複数のパッチを同時に適用できます。

```bash
./vendor/bin/magento-patches apply MAGETWO-XXXX MAGETWO-YYYY
```

変更をAdobe Commerceアプリケーションで確認するには、パッチを適用した後、キャッシュをクリーンアップする必要があります。

```bash
./bin/magento cache:clean
```

>[!INFO]
>
>適用済みのパッチのリストを別の場所に保持することを検討します。 新しいバージョンのAdobe CommerceまたはMagento Open Sourceにアップグレードした後に、一部のアプリケーションを再適用する必要が生じる場合があります。 詳しくは、 [アップグレード後にパッチを再適用](#re-apply-patches-after-an-upgrade).

## 個々のパッチを元に戻す

>[!WARNING]
>
>実稼動環境にデプロイする前に、ステージング環境または開発環境ですべてのパッチをテストすることをお勧めします。 また、パッチを適用する前にデータをバックアップすることをお勧めします。 詳しくは、 [ファイル・システムのバックアップとロールバック](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-backup.html).

1 つのパッチを元に戻すには、次のコマンドを実行します。 `MAGETWO-XXXX` は、ステータステーブルで指定されたパッチ ID です。

```bash
./vendor/bin/magento-patches revert MAGETWO-XXXX
```

また、追加した各パッチ ID をスペースで区切ることで、複数のパッチを同時に元に戻すこともできます。

```bash
./vendor/bin/magento-patches revert MAGETWO-XXXX MAGETWO-YYYY
```

適用されたすべてのパッチを元に戻すには：

```bash
./vendor/bin/magento-patches revert --all
```

変更をAdobe Commerceアプリケーションで確認するには、パッチを元に戻した後にキャッシュをクリーンアップする必要があります。

```bash
./bin/magento cache:clean
```

## 更新を取得

Adobe Commerceは定期的に新しい個々のパッチをリリースします。 を更新する必要があります [!DNL Quality Patches Tool] 新しい個々のパッチを取得するには：

```bash
composer update magento/quality-patches
```

追加されたパッチを表示します。

>[!TIP]
>
>新しい追加パッチが表の下部に表示されます。

```bash
./vendor/bin/magento-patches status
```

## アップグレード後にパッチを再適用 {#re-apply-patches-after-an-upgrade}

新しいバージョンのAdobe CommerceまたはMagento Open Sourceにアップグレードする場合、新しいバージョンにパッチが含まれていない場合は、パッチを再適用する必要があります。

パッチを再適用するには、次の手順に従います。

1. を更新します。 [!DNL Quality Patches Tool]:

   ```bash
   composer update magento/quality-patches.
   ```

1. 以前に適用したパッチのリストを開きます（で推奨）。 [個々のパッチの適用](#apply-individual-patches).

1. パッチを適用します。

   ```bash
   ./vendor/bin/magento-patches apply MAGETWO-XXXX
   ```

   ベストプラクティスは、パッチを 1 つずつ適用することです。

1. キャッシュをクリーンアップします。

   ```bash
   ./bin/magento cache:clean
   ```

   >[!INFO]
   >
   >実行時に `status` コマンドを使用すると、新しいバージョンに含まれていたパッチは、使用可能なパッチのテーブルに表示されなくなります。

## ログ

この [!DNL Quality Patches Tool] にすべての操作を記録します。 `<Magento_root>/var/log/patch.log` ファイル。
