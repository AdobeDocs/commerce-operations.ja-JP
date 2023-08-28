---
title: コンポーザーのヒントとテクニック
description: 問題をすばやく解決するための、一般的な Composer の開発タスクとガイダンスについて説明します。
feature: Best Practices
role: Developer
source-git-commit: b4213c40fdf903fd962a15fc99b143f31aedbcde
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 0%

---


# コンポーザーのヒントとテクニック

Composer を使用してAdobe Commerceモジュールを開発する際に問題が発生する場合があります。 これらのベストプラクティスでは、開発を容易にし、問題を迅速に解決できるようにする一般的なタスクを説明します。

>[!NOTE]
>
>以下のガイドラインは主に次のものに適用されます。 [グローバルリファレンスアーキテクチャ (GRA)](../overview.md) プロジェクト。

## コンポーザーのスピードアップ

インストール [https://github.com/hirak/prestissimo](https://github.com/hirak/prestissimo) 非同期パッケージのダウンロードを高速化するために、Composer を使用します。

```bash
composer global require hirak/prestissimo
```

問題が発生した場合は、をアンインストールします。 `prestissimo`:

```bash
composer global remove hirak/prestissimo
```

## バージョンのあいまいな問題を解決します

Composer で、パッケージバージョンでデッドロックされる場合があります。 互換性のないバージョンに関するメッセージが表示される場合があります（そうでない場合でも）。 互換性の問題をデバッグする前に、コンポーザーをリセットしてみてください。

1. Composer のキャッシュをクリアします。

   ```bash
   composer clearcache
   ```

1. を削除します。 `composer.lock` ファイルを参照してください。

   ```bash
   rm -rf vendor/* composer.lock
   ```

1. Composer パッケージを再インストールします。

   ```bash
   composer install
   ```

>[!TIP]
>
>以下の手順では、すべてのパッケージを利用可能な最新バージョンに更新します。 を元に戻す `composer.lock` ファイルを Git から削除して、これらのアップグレードを取り消します。

## クライアントパッケージで更新可能な項目を確認します。

1. 古い可能性のあるパッケージを調べます。

   ```bash
   composer outdated
   ```

1. ワイルドカードや `--minor-only` 後方互換性のないアップグレードをスキップするオプション：

   ```bash
   composer outdated 'magento/*'
   composer outdated --minor-only 'magento/*'
   ```

## モジュールがインストールされているかどうかを確認します。

Git ブランチにインストールされているすべてのパッケージの詳細を表示します。

```bash
composer info
```

実行 `composer install` Git ブランチを切り替えてから実行する `composer info`. それ以外の場合は、チェックアウトした前のブランチに関する詳細が Composer に表示されます。

>[!TIP]
>
>フィルタまたは検索を行うには、次のいずれかのコマンドを使用します。
>
>```bash
>composer info '*magento*'
>composer info | grep magento
>```

## （特定のバージョンの a）パッケージがインストールされる理由を確認します。

別のパッケージ内での厳密な依存関係が原因で、Composer が使用可能な最新バージョンのパッケージをインストールする場合があります。

別のパッケージに厳密な依存関係があるかどうかを調べます。

```bash
composer why client/module-example
```

メタパッケージのリスト、または明示的に必要でない別のパッケージが表示される場合は、そのパッケージで次のコマンドを実行します。

```bash
composer why example/metapackage
```

## パッケージがインストールされない理由を確認する

別のパッケージと競合したり、別のパッケージに置き換えられたり、依存関係として定義していない場合に、Composer でパッケージがインストールされないことがあります。

パッケージがインストールされない理由を確認します。

```bash
composer why-not client/module-example
```

## プライベート Composer リポジトリをホストする

プライベートの Composer リポジトリが必要な場合は、 [プライベートパッケージスト](https://packagist.com/) または [JFrog Artifactory](https://jfrog.com/integration/php-composer-repository/). 次を使用しない [無料](https://github.com/composer/satis).

- **プライベートパッケージスト** は安全で、3 人の管理者ユーザーが年間約 600 米ドル (USD) のコストをかけます。また、はホストされています。

- **JFrog Artifactory** は、年間$1,176 USD で始まります。 Packagist と同じくらい一般的に使われているわけではありませんが、PHP より多くの言語をサポートしています。

- **無料** にはセキュリティ機能が組み込まれておらず、自動化もなく、追加のホスティングが必要です。 あなたの時間も自由である場合に限り、無料です。

## パッケージのバージョン管理

用途 [セマンティックバージョン管理 2.0.0](https://semver.org/spec/v2.0.0.html) Adobe Commerce [バージョン管理スキーマ](https://developer.adobe.com/commerce/php/development/versioning/). ホイールを作り直さないでください。

Adobe Commerceモジュールの依存関係については、 [モジュールバージョンの依存関係](https://developer.adobe.com/commerce/php/development/versioning/dependencies/) ドキュメント。

内でバージョン定義を使用しない `composer.json` ファイル。 代わりに、バージョンに Git タグを使用します。 詳しくは、 [Composer のバージョンと制約](https://getcomposer.org/doc/articles/versions.md#versions-and-constraints).

## Composer を使用せずにアーカイブファイルに入ってくるモジュールを配置する場所

アーカイブ内のモジュール用に Git リポジトリを作成し、自身でホストします。 すべてのAdobe Commerceモジュールには `composer.json` ファイル。 Git でホストし、プライベートパッケージリストと同期した後、Composer と共にインストールできます。

新しいバージョンのパッケージを受け取ったら、コードを Git にアップロードし、タグ付けし、Composer で新しいバージョンをインストールします。
