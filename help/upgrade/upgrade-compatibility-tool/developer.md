---
title: '"[!DNL Upgrade Compatibility Tool] 開発者情報»'
description: のカスタマイズ [!DNL Upgrade Compatibility Tool] API インデックスの統合を使用する。
source-git-commit: 317a044e66fe796ff66b9d8cf7b308f741eb82c1
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---


# [!DNL Upgrade Compatibility Tool] 開発者情報

{{commerce-only}}

このトピックには、Adobe Commerceコードを緊密に連携し、 [!DNL Upgrade Compatibility Tool]. この知識を使用して、ツールのコンポーネントをカスタマイズできます。

## Adobe Commerce API インデックスの統合

Adobe Commerce API インデックス統合は、静的コード分析に基づいてAdobe、Adobe Commerceパートナー、サードパーティベンダーが開発したAdobe Commerce拡張機能を調査するための一連のツールを含む内部統合ソリューションです。

Adobe Commerce API インデックスとの統合は、次の方法でおこないます。

`sut\Domain\MRay\MRayInterface`

これは、 `config/services.yaml` ファイル。 メソッドの応答を決定する値です `api()` および `modules()` はから取得されます。

このファイルを編集し、インストールに応じて応答をカスタマイズします。 割り当て先の値を置き換える `sut\Domain\MRay\MRayInterface`:

### カスタム値の例

`sut\Domain\MRay\MRayInterface : "@sut_mray_mock"`

前の例では、 [!DNL Upgrade Compatibility Tool] uses `@sut_mray_mock` を `MRayInterface` 実装。 次の `api()` および `modules()` メソッドは次のファイルから取得されます。

- `dev/mray_mock_files/api.json`
- `dev/mray_mock_files/modules.json`

>[!NOTE]
>
>次の `services.yaml` ファイル、 `var/cache/` フォルダーを使用して、変更を正しく適用できます。

## 単体テスト

単体テストを実行するには、次のいずれかのコマンドを実行します。

- `vendor/bin/phpunit tests/unit`
- `vendor/bin/phpunit -c tests/unit/phpunit.xml.dist tests/unit`
- `vendor/bin/phpunit -c tests/unit/phpunit.xml.dist --testsuite=unit-tests`

## 統合テスト

統合テストを実行するには、次のいずれかのコマンドを実行します。

- `vendor/bin/phpunit -c tests/integration/phpunit.xml.dist tests/integration`
- `vendor/bin/phpunit -c tests/integration/phpunit.xml.dist --testsuite=integration-tests`

## 受け入れテスト

1. 受け入れテストを実行する前に、Adobe Commerceの URL を `phpunit` 設定ファイル。
1. デフォルトの `tests/acceptance/phpunit.xml` ファイル（ .dist サフィックスを除く）
1. を `TESTS_BASE_URL` の値は、テストするAdobe Commerce URL を指しています。
1. 受け入れテストを実行するには、次のいずれかのコマンドを実行します。

   - `vendor/bin/phpunit -c tests/acceptance/phpunit.xml tests/acceptance`
   - `vendor/bin/phpunit -c tests/acceptance/phpunit.xml --testsuite=acceptance-tests`

## GraphQL ユニットテストと ESLint コード分析

### 要件

>[!NOTE]
>
>システムに Node.js が必要です。詳しくは、 [Node.js のドキュメント](https://nodejs.dev/learn/how-to-install-nodejs).

次の手順は、MacOSシステム向けです。

1. ターミナルを開き、プロジェクトのルートディレクトリに移動します。
1. プロジェクトの依存関係をインストール：

   ```bash
   npm install
   ```

### GraphQL 単体テスト

この [Jest](https://jestjs.io/docs/getting-started) フレームワークは、次の JS 単体テストを作成するために使用されました。

テストは次の中に含まれます。 `dev/tests/Js`.

テスト用の文字列スキーマは内部にあります `dev/tests/Acceptance/_files/graphql_schemas`.

単体テストの実行または `jest` 次のように指定します。

```bash
./node_modules/.bin/jest --verbose --rootDir=dev/tests/Js/
```

### ESLint コード分析

[ESLint](https://eslint.org/docs/user-guide/getting-started) は、コードの一貫性を高め、バグを回避することを目的として、JavaScript コードで見つかった問題のあるパターンを識別する静的コード分析ツールです。

実行 `eslint` コード分析を次のように指定します。

```bash
./node_modules/.bin/eslint -c dev/tests/Static/.eslintrc --rulesdir vendor/magento/magento-coding-standard/eslint/rules path/to/analyse
```

## 複雑性スコア

この **複雑性スコア** は、現在のバージョンから新しいバージョンへのアップグレードがどの程度難しいかを示す図です。 数字を小さくすると、アップグレードが容易になります。

>[!NOTE]
>
>複雑度スコアの範囲は 0 ～ ∞です。

このスコアは、分析から抽出された結果に基づきます。

- 特定された問題の数
- 特定された問題の重大度

この [!DNL Upgrade Compatibility Tool] 以下の複雑度スコアの数式に従って、このスコアを計算します。

### 複雑性スコアの式

`Complexity Score = (Critical issues * 3) + (Errors *2) + Warnings`

>[!WARNING]
>
>これらは絶対値です。
