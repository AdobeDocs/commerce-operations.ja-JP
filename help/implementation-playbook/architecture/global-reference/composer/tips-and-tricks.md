---
title: Composer のヒントとテクニック
description: 一般的な Composer 開発タスクと、問題を迅速に解決するためのガイダンスについて説明します。
feature: Best Practices
role: Developer
hide: true
hidefromtoc: true
exl-id: 5ead5fb1-3bb3-4e77-a4f1-8e10c4f91efb
source-git-commit: 80cf4dc2b5c9dd690aee1b224fbe6c766fe8f2ab
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 0%

---

# Composer のヒントとテクニック

Composer でAdobe Commerce モジュールを開発する際に問題が発生する場合があります。 これらのベストプラクティスでは、開発を容易にし、問題を迅速に解決するのに役立つ、いくつかの一般的なタスクについて説明します。

>[!NOTE]
>
>これらのガイドラインは主に次のものに適用されます。 [グローバルリファレンスアーキテクチャ（GRA）](../overview.md) プロジェクト。

## Composer の高速化

インストール [https://github.com/hirak/prestissimo](https://github.com/hirak/prestissimo) 非同期パッケージ ダウンロードで Composer を高速化します。

```bash
composer global require hirak/prestissimo
```

問題が発生した場合は、アンインストールします `prestissimo`:

```bash
composer global remove hirak/prestissimo
```

## バージョン管理に関する曖昧な問題の解決

Composer がパッケージ バージョンでデッドロックされることがあります。 互換性のないバージョンに関するメッセージが、そうでない場合でも表示される場合があります。 互換性の問題をデバッグする前に、Composer をリセットしてみてください。

1. Composer のキャッシュをクリアします。

   ```bash
   composer clearcache
   ```

1. を削除 `composer.lock` すべてのパッケージのファイル。

   ```bash
   rm -rf vendor/* composer.lock
   ```

1. Composer パッケージを再インストールします。

   ```bash
   composer install
   ```

>[!TIP]
>
>次の手順では、すべてのパッケージを利用可能な最新バージョンに更新します。 を復帰させる `composer.lock` git のファイルを開いて、これらのアップグレードを取り消します。

## クライアントパッケージで発生する可能性のあるアップデートを確認します。

1. どのパッケージが古くなっている可能性があるかを調べます。

   ```bash
   composer outdated
   ```

1. ワイルドカードや `--minor-only` 下位互換性のないアップグレードをスキップするオプション：

   ```bash
   composer outdated 'magento/*'
   composer outdated --minor-only 'magento/*'
   ```

## モジュールがインストールされているかどうかを確認する

Git ブランチにインストールされているすべてのパッケージに関する詳細の表示。

```bash
composer info
```

実行 `composer install` git ブランチを切り替えた後、実行する前 `composer info`. それ以外の場合、チェックアウトした前のブランチの詳細が表示されます。

>[!TIP]
>
>フィルターまたは検索するには、次のいずれかのコマンドを使用します。
>
>```bash
>composer info '*magento*'
>composer info | grep magento
>```

## （特定のバージョンの）パッケージがインストールされる理由を調べる

他のパッケージに厳密に依存しているため、Composer によって利用可能な最新バージョンのパッケージがインストールされることがあります。

別のパッケージに厳密な依存関係があるかどうかを確認します。

```bash
composer why client/module-example
```

結果に、メタパッケージのリストや、明示的に必要とされていない別のパッケージが表示された場合は、そのパッケージでコマンドを実行します。

```bash
composer why example/metapackage
```

## パッケージがインストールされていない理由を調べる

他のパッケージと競合する、他のパッケージで置き換える、または依存関係として定義していないなどの理由で、パッケージがインストールされないことがあります。

パッケージがインストールされていない理由を確認します。

```bash
composer why-not client/module-example
```

## Composer のプライベート・リポジトリのホスト

Composer の非公開リポジトリが必要な場合は、 [プライベート パッケージ担当者](https://packagist.com/) または [JFrog アーティファクトリー](https://jfrog.com/integration/php-composer-repository/). を使用しないでください。 [サティス](https://github.com/composer/satis).

- **プライベート パッケージ担当者** は安全で、3 人の管理者ユーザーで年間約 600 USD のコストがかかり、ホストされています。

- **JFrog アーティファクトリー** 開始価格は年間 1,176 米ドルです。 Packagist ほど一般的に使用されているわけではありませんが、PHP よりも多くの言語をサポートしています。

- **サティス** にはセキュリティの組み込みや自動化が含まれておらず、追加のホスティングが必要です。 あなたの時間も無料である場合にのみ無料です。

## バージョン管理パッケージ

使用方法 [セマンティックバージョニング 2.0.0](https://semver.org/spec/v2.0.0.html) Adobe Commerceで説明されているように [バージョン管理スキーマ](https://developer.adobe.com/commerce/php/development/versioning/). 車輪を作り直さないでください。

Adobe Commerce モジュールの依存関係については、次に従います [モジュールバージョンの依存関係](https://developer.adobe.com/commerce/php/development/versioning/dependencies/) ドキュメント。

内でバージョン定義を使用しないでください `composer.json` ファイル。 代わりに、バージョンには Git タグを使用します。 参照： [Composer のバージョンと制約](https://getcomposer.org/doc/articles/versions.md#versions-and-constraints).

## Composer を使用せずに、アーカイブ ファイルに含まれるモジュールを配置する場所

アーカイブ内のモジュールに Git リポジトリを作成し、自分でホストします。 すべてのAdobe Commerce モジュールには、 `composer.json` ファイル。 Git でホストし、Private Packagist と同期したら、Composer を使用してインストールできます。

新しいバージョンのパッケージを受け取ったら、コードを Git にアップロードし、タグ付けして、Composer で新しいバージョンをインストールします。
