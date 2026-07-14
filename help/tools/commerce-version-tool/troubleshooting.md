---
title: '[!DNL Commerce Version Tool]のトラブルシューティング'
description: ' [!DNL Commerce Version Tool] Composer検出、内部ドライラン チェック、レジストリ キャッシュ、JSON出力、監査ログの問題のトラブルシューティング方法について説明します。'
TQID: 'https://experienceleague.adobe.com/JwRSy7pfM89WoifYUzTVPhR-WrDIvj2A2B8SaEnmyWM'
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dcid: c1579802-ddd4-4214-8a91-97b2066abe11id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: eafe79321da03f4778dd9e1b290141ef082a5eaf
workflow-type: tm+mt
source-wordcount: 1222
ht-degree: 0%

---

# [!DNL Commerce Version Tool]のトラブルシューティング

このページでは、Composer検出、レジストリの読み込み、内部ドライラン パッチ検出、出力生成、監査ログに関する一般的な[!DNL Commerce Version Tool] （[!DNL CVT]）の問題のトラブルシューティングを行います。

## クイックトラブルシューティング手順

[!DNL CVT] ツールが期待されるパッチ ステータス レポートを返さない場合：

- 対象のインストールで、サポートされているAdobe Commerce バージョンとエディションが使用されていることを確認します。
- `composer.lock`が存在し、検査する環境と一致することを確認してください。
- PHPとシステム `patch` バイナリが使用可能であることを確認します。
- [!DNL CVT]がパッチ レジストリ ファイルを読み取れることを確認します。
- 出力の`warnings`、`missing_patches`および`unknown_patches`を確認してください。
- ログ ファイルが作成されている場合は、実行の監査概要を`var/log/patch_status.log`で確認してください。

>[!TIP]
>
> ログファイルは、パッチを分類できなかった理由を理解する必要がある場合に最も役立ちます。 不明なパッチごとに、ログには、エラーやハンクの失敗など、前方実行と後方実行の未加工の出力が記録されます。
>
> レジストリ ファイルまたはパッチ ファイルの取得に問題がある場合は、レポートの警告フィールドを確認してください。 その詳細はログに表示されません。

## 一般的な問題と解決策

### 基本バージョンを検出できません

[!DNL CVT] ツールでAdobe Commerceの基本バージョンが見つからない場合は、次の条件を確認します。

**確認：**

- `composer.lock`が見つかりません。
- `patch-status` コマンドがAdobe Commerce プロジェクトのルート外で実行されているため（または`--root`が間違ったパスを指しています）、`composer.lock`が見つかりません。
- `composer.lock`は存在しますが、有効なJSONでないか、読み取ることができません。
- `composer.lock`には、認識された基本パッケージ （`magento/product-enterprise-edition`、`magento/product-community-edition`、`magento/magento2-base`）が含まれていません。

**警告メッセージ：**

`composer.lock`が存在するが、読み取り不可能であるか、解析できないか、認識された基本パッケージを含まない場合、ツールは警告出力フィールドに次のいずれかの文字列を出力します。

```shell-session
No recognized Commerce base package found in composer.lock
composer.lock exists but could not be read
composer.lock could not be parsed as JSON
```

>[!NOTE]
>
> `composer.lock`が完全に見つからない場合、ツールは`base_version: "unknown"`を報告し、**警告メッセージはまったくありません**。 常に出力の`base_version`を直接確認してください。 この問題を見つけるために警告の存在に依存しないでください。

前述の条件のいずれかは、ツールが基本バージョンを検出できないことを示します。 ツールはコード `1`で終了し、パッチ検出は実行されません。

**アクション：**

- [!DNL Adobe Commerce] プロジェクト ルートから`patch-status` コマンドを実行するか、正しい`--root`を渡します。
- `composer.lock`が存在し、現在の有効なJSONであることを確認します。
- インストールでサポートされているAdobe Commerce エディションを使用して、`composer.lock`に認識された基本パッケージの1つが含まれていることを確認してください。

### インストールされたバージョンにはパッチは適用されません

[!DNL CVT]が有効な`base_version`を報告していますが、`applied_patches`、`missing_patches`、`unknown_patches`が空の場合、インストールされているバージョンは現在のパッチレジストリの対象にはなりません。

**確認：**

- インストールされている[!DNL Adobe Commerce] バージョンは、パッチ レジストリ ファイルに表示されません。 例えば、レジストリの最新のエントリよりも新しいリリースを指定します。

**警告メッセージ：**

```shell-session
No patches found in registry for installed component versions (CE=2.4.7-p9)
```

この警告は、「基本バージョンを検出できません」と異なります。 `base_version`は正しく、ツールは`0`を終了し、レジストリには比較するものがありません。

**アクション：**

- 出力の`base_version`が期待どおりであることを確認してください。
- `registry_source`が古いものではなく、`remote`または最近の`cache`であることを確認してください。
- このバージョンを既にカバーする必要がある場合は、Adobe Commerce サポートにお問い合わせください。

### パッチレジストリを取得できません

[!DNL CVT] ツールが最新のパッチ レジストリ ファイルを取得できない場合は、ネットワークとキャッシュの設定を確認します。

**確認：**

- ネットワークは利用できません。
- Adobe パッチエンドポイントリクエストがタイムアウトします。
- `--no-cache`が使用されたため、リモート レジストリにアクセスできません。
- `PATCH_REGISTRY_URL`は、使用できないレジストリを指しているか、有効なHTTPS URLではありません。
- [!DNL CVT] ツールが最新のパッチ レジストリ ファイルを取得できない場合は、ネットワークとキャッシュの設定を確認します。

>[!NOTE]
>
>レジストリファイルが見つからないか期限切れになっている場合、ツールはリモートホストから最新のレジストリをダウンロードします。

**警告メッセージ：**

このツールは、このシナリオの警告出力フィールドに次の文字列を出力します。

```shell-session
Remote registry fetch failed (HTTP 403). Check PATCH_REGISTRY_URL (if set) and network connectivity.
Remote registry response was not valid JSON; ignoring.
Could not load remote registry. Using cached registry (3 hours old). CVE coverage may be incomplete.
Patch registry could not be loaded.
Could not fetch remote registry and --no-cache was set; aborting.
```

古いキャッシュメッセージには、実際の経過時間（時間）が含まれます（例：`(3 hours old)`）。

`patch registry could not be loaded`と`could not fetch remote registry`の警告は、パッチ検出を実行せずにツールが終了したことを示します。

**アクション：**

- ネットワーク接続が利用可能な場合は、`patch-status` コマンドを再実行します。
- 古いキャッシュ警告がスキャンで許容される場合は、[!DNL CVT] ツールでキャッシュ レジストリを使用できるようにします。
- 新しいリモートフェッチが必要でない限り、`--no-cache`を削除します。
- レジストリ キャッシュを再利用する場合は、[!DNL CVT] ツールが`var/patch_metadata/`に書き込むことができることを確認してください。

### パッチの差分を取得または検証できません

[!DNL CVT] ツールで1つ以上の適用可能なパッチをテストできない場合は、パッチ差分アクセスを確認します。

**確認：**

- Adobe パッチエンドポイントからパッチの差分をダウンロードできません。
- 認証されたパッチのダウンロードに必要な資格情報が見つからないか、無効です。
- `PATCH_DIFF_BASE_URL`は、利用できないパッチの差分ソースを指しているか、有効なHTTPS URLではありません。
- キャッシュされたパッチの差分が見つからないか、読み取れません。
- ダウンロードしたパッチの差分に対するSHA-256検証が失敗します。
- [!DNL CVT] ツールは`var/patch_metadata/.patch_diffs/`に書き込めません。

**警告メッセージ：**

このツールは、このシナリオの警告出力フィールドに次の文字列を出力します。

```shell-session
Patch 247p9-2026-05-001-EE requires authentication. Set credentials via COMPOSER_AUTH or auth.json.
Could not fetch patch 247p9-2026-05-001-EE (HTTP 401). Check credentials (COMPOSER_AUTH / auth.json).
Could not fetch patch 247p9-2026-05-001-EE (HTTP 404).
Could not fetch or verify patch 247p9-2026-05-001-EE. Check network connectivity and credentials (COMPOSER_AUTH / auth.json).
Could not fetch patch file for 247p9-2026-05-001-EE.
SHA-256 verification failed for patch 247p9-2026-05-001-EE; discarding download.
```

各メッセージのパッチ IDは、実際のレジストリ エントリ ID （例：`247p9-2026-05-001-EE`）です。 `SHA-256 verification failed`は、新しくダウンロードされたパッチファイルが、想定されるチェックサムと一致しなかったことを意味します。 ツールはキャッシュせずに破棄し、この実行のパッチ `unknown`を分類します。 破損した&#x200B;*ローカル* キャッシュ エントリが検出され、警告なしで同じ実行内でサイレントに再フェッチされます。 どちらの場合も、手動によるキャッシュのクリーンアップは必要ありません。

**アクション：**

- ネットワーク接続を確認し、コマンドを再試行してください。
- 認証されたパッチのダウンロードに必要な資格情報が設定されていることを確認します。
- [!DNL CVT] ツールが`var/patch_metadata/.patch_diffs/`に書き込むことができることを確認します。
- パッチが不明として分類されたままの場合は、警告と出力の詳細を保持します。

### 環境にないパッチまたは不明なパッチが報告される

レポートに予期しない`missing_patches`または`unknown_patches`値が含まれる場合は、インストールと出力の詳細を確認します。

**確認：**

- 毎月のパッチが順番に適用されました。
- Adobe Commerce Business-to-Business （B2B）やAdobe Commerce Page Builderなどのコンポーネント固有のパッチがありません。
- `composer.lock`は、パッチが必要なインストール済みコンポーネントバージョンを報告します。
- パッチの差分が利用できないか、検出結果が決定的ではありません。

**警告メッセージ：**

このツールは、このシナリオの警告出力フィールドに次の文字列を出力します。

```shell-session
No file_name or sha256 for 247p9-2026-05-001-EE
Registry entry '247p9-2026-05-001-EE' requires unknown patch '247p9-2026-04-001-EE'; skipping.
descendant diffs unavailable for 247p9-2026-06-001-EE; dry-run for 247p9-2026-05-001-EE may be inaccurate
Failed to reverse-apply 247p9-2026-06-001-EE when preparing dry-run for 247p9-2026-05-001-EE; result may be inaccurate
Failed to forward-apply prerequisite 247p9-2026-04-001-EE when preparing dry-run for 247p9-2026-05-001-EE; result may be inaccurate
```

警告で`may be inaccurate`が発生した場合、ドライラン チェックは実行されますが、信頼性は低下します。 パッチは引き続き`applied_patches`または`missing_patches`に分類でき、必ずしも`unknown_patches`とは限りません。

不明なパッチの場合、具体的には、`var/log/patch_status.log`は生のパッチドライラン出力（前方及び逆）を記録し、どのファイルとチャンクが一致しなかったかを示します。

「パッチが見つかりません」という警告が表示された場合は、[ インストールされているバージョンにパッチが適用されない](#no-patches-apply-to-the-installed-version)を参照してガイダンスを受けてください。

**アクション：**

- `applied_patches`、`missing_patches`、`unknown_patches`のフィールドを確認します。
- インストールされているエディションとコンポーネントに欠落しているパッチが適用されるかどうかを確認します。
- その結果と、関連するセキュリティ パッチのリリースノートを比較します。
- 検査したコードベースが、レポート対象のデプロイ済み環境と一致することを確認します。
- 不明なステータスが是正計画をブロックする場合は、Adobe Commerce サポートにお問い合わせください。

### 出力が生成されない

[!DNL CVT] ツールが完了しても、予期されるJSONまたはCSV出力が見つからない場合は、コマンドの構文とターミナル出力を確認します。

**アクション：**

- CSV出力が必要ない場合は、デフォルトのJSON出力を使用します。
- `--format=csv`を使用してCSV出力を生成します。
- コマンド出力が、[!DNL CVT] ツールを実行するシェル、スクリプト、またはスキャナーによってリダイレクトまたは破棄されないことを確認します。
- `stderr`で`patch-status:`個のエラーメッセージを確認してください。
- 出力をファイル （例：`patch-status > report.json`）にリダイレクトする場合は、シェルがその宛先に対する書き込み権限を持っていることを確認します。 ツールは`stdout`にのみ書き込みます。
- [!DNL CVT] ツールが`var/log/patch_status.log`に書き込むことができることを確認します。
- コマンドを再実行し、端末出力をキャプチャしてトラブルシューティングを行います。

## ヘルプの取得

Adobe Commerce サポートに連絡する場合は、問題を調査するために必要な詳細情報のみを提供してください。

次を含める：

- Adobe Commerceのバージョンとエディション
- [!DNL CVT] ツール バージョン
- [!DNL CVT] ツール出力のレジストリ ソース
- 関連する`applied_patches`、`missing_patches`および`unknown_patches`値
- 関連する警告
- エラーメッセージまたはコマンド出力

共有ログまたは添付ファイルに、シークレット、資格情報、秘密鍵、または関連しない顧客データを含めないでください。

## 関連トピック

- [概要](intro.md)
- [パッチステータスレポートの生成](generate-report.md)
- [リリースノート](release-notes.md)
