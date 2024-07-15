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
>これらのガイドラインは、主に [GRA （グローバル・リファレンス・アーキテクチャ） ](../overview.md) プロジェクトに適用されます。

## Composer の高速化

非同期パッケージ ダウンロードで Composer を高速化するには ](https://github.com/hirak/prestissimo)0}https://github.com/hirak/prestissimo} をインストールします。[

```bash
composer global require hirak/prestissimo
```

問題が発生した場合は、`prestissimo` をアンインストールします。

```bash
composer global remove hirak/prestissimo
```

## バージョン管理に関する曖昧な問題の解決

Composer がパッケージ バージョンでデッドロックされることがあります。 互換性のないバージョンに関するメッセージが、そうでない場合でも表示される場合があります。 互換性の問題をデバッグする前に、Composer をリセットしてみてください。

1. Composer のキャッシュをクリアします。

   ```bash
   composer clearcache
   ```

1. すべてのパッケージの `composer.lock` ファイルを削除します。

   ```bash
   rm -rf vendor/* composer.lock
   ```

1. Composer パッケージを再インストールします。

   ```bash
   composer install
   ```

>[!TIP]
>
>次の手順では、すべてのパッケージを利用可能な最新バージョンに更新します。 Git から `composer.lock` ファイルを元に戻して、これらのアップグレードを取り消します。

## クライアントパッケージで発生する可能性のあるアップデートを確認します。

1. どのパッケージが古くなっている可能性があるかを調べます。

   ```bash
   composer outdated
   ```

1. ワイルドカードや `--minor-only` オプションを使用してフィルターを適用し、下位互換性のないアップグレードをスキップします。

   ```bash
   composer outdated 'magento/*'
   composer outdated --minor-only 'magento/*'
   ```

## モジュールがインストールされているかどうかを確認する

Git ブランチにインストールされているすべてのパッケージに関する詳細の表示。

```bash
composer info
```

Git ブランチを切り替えた後、`composer info` を実行する前に、`composer install` を実行します。 それ以外の場合、チェックアウトした前のブランチの詳細が表示されます。

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

Composer の非公開リポジトリが必要な場合は、[Private Packagist](https://packagist.com/) または [JFrog Artifactory](https://jfrog.com/integration/php-composer-repository/) を使用します。 [Satis](https://github.com/composer/satis) を使用しないでください。

- **Private Packagist** は安全で、3 人の管理者ユーザーで年間約 600 USD の費用がかかり、ホストされています。

- **JFrog Artifactory** は、年間 1,176 米ドルから始まります。 Packagist ほど一般的に使用されているわけではありませんが、PHP よりも多くの言語をサポートしています。

- **Satis** には、セキュリティの組み込みや自動化が含まれておらず、追加のホスティングが必要となります。 あなたの時間も無料である場合にのみ無料です。

## バージョン管理パッケージ

Adobe Commerce[ バージョン管理スキーマ ](https://semver.org/spec/v2.0.0.html) の説明に従って、[Semantic Versioning 2.0.0](https://developer.adobe.com/commerce/php/development/versioning/) を使用します。 車輪を作り直さないでください。

Adobe Commerce モジュールの依存関係については、[module version dependencies](https://developer.adobe.com/commerce/php/development/versioning/dependencies/) のドキュメントに従ってください。

`composer.json` ファイル内でバージョン定義を使用しないでください。 代わりに、バージョンには Git タグを使用します。 [Composer バージョンと制約 ](https://getcomposer.org/doc/articles/versions.md#versions-and-constraints) を参照してください。

## Composer を使用せずに、アーカイブ ファイルに含まれるモジュールを配置する場所

アーカイブ内のモジュールに Git リポジトリを作成し、自分でホストします。 すべてのAdobe Commerce モジュールには `composer.json` ファイルがあります。 Git でホストし、Private Packagist と同期したら、Composer を使用してインストールできます。

新しいバージョンのパッケージを受け取ったら、コードを Git にアップロードし、タグ付けして、Composer で新しいバージョンをインストールします。
