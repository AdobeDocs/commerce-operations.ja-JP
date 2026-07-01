---
title: パッチを大規模に配布するためのベストプラクティス
description: Adobe Commerceの一元的なパッチ適用が、大規模なプロジェクトの管理にどのように役立つかをご確認ください。
role: Developer
feature: Best Practices
badge: label="Contributed by Tony Evers, シニア・テクニカル・アーキテクト，Adobe" type="Informative" url="https://www.linkedin.com/in/evers-tony/" tooltip="アーティスト：Tony Evers"
exl-id: 08c38dc5-3dc2-49ee-b56f-59e1718e12b5
source-git-commit: 2c9f827326315bc4ef77d511dddce81e059a1092
workflow-type: tm+mt
source-wordcount: '1359'
ht-degree: 0%

---

# Adobe Commerce パッチを大規模に配布するためのベストプラクティス

複数のAdobe Commerce インストールを管理する場合、[&#x200B; パッチ適用](../../../upgrade/patches/apply.md)は複雑なプロセスになる可能性があります。 _一元的なパッチ適用_&#x200B;は、企業にとってベストプラクティスです。 Adobe Commerceのすべてのインストールに適切なパッチを適用するのに役立ちます。 このトピックでは、すべての種類のAdobe Commerce [&#x200B; パッチ &#x200B;](../../../upgrade/patches/overview.md)に対して一元的にパッチを配布する方法について説明します。

>[!NOTE]
>
>以下の内容は、当初Adobe Tech ブログの[Adobe Commerce パッチの大規模な配布](https://blog.developer.adobe.com/distributing-adobe-commerce-patches-at-scale-137412e05a20)記事に掲載されました。 一元化されたパッチ戦略を実装するための手順とコードサンプルに焦点を当てるように変更されました。 ここで説明する様々な種類のパッチについて詳しくは、元の投稿を参照してください。

## 影響を受ける製品とバージョン

[&#x200B; サポートされているすべてのバージョン &#x200B;](../../../release/versions.md) /:

- Adobe Commerce on cloud infrastructure
- Adobe Commerce オンプレミス

## 戦略

パッチには様々な種類があり、適用する方法も多いので、最初に適用するパッチを知るにはどうすればよいでしょうか？ パッチが多ければ多いほど、同じファイルや同じコード行に適用される可能性が高くなります。 パッチは次の順序で適用されます。

1. **セキュリティパッチ**&#x200B;は、Adobe Commerce リリースの静的コードベースの一部です。
1. **コンポーザーのパッチ** ～ `composer install`および[cweagans/composer-patches](https://packagist.org/packages/cweagans/composer-patches)などの`composer update`個のプラグイン。
1. すべての&#x200B;**必要なパッチ**&#x200B;は、[Cloud Patches for Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches.html?lang=ja) パッケージに含まれています。
1. [[!DNL [Quality Patches Tool]]](../../../tools/quality-patches-tool/usage.md)に含まれる高品質のパッチ **を選択しました。**
1. **カスタムパッチ**&#x200B;とAdobe Commerceは、パッチ名でアルファベット順に`/m2-hotfixes` ディレクトリのパッチをサポートします。

   >[!IMPORTANT]
   >
   >パッチを適用すればするほど、コードが複雑になります。 複雑なコードを使用すると、新しいバージョンのAdobe commerceへのアップグレードがより困難になり、総所有コストが増加する可能性があります。

Adobe Commerceの複数のインストールを管理する責任がある場合、すべてのインスタンスに同じパッチセットがインストールされていることを確認することは困難です。 各インストールには、独自のGit リポジトリ、`/m2-hotfixes` ディレクトリ、および`composer.json` ファイルがあります。 お客様が持っている唯一の保証は、クラウドユーザーに必要な&#x200B;**セキュリティパッチ**&#x200B;と&#x200B;**パッチ**&#x200B;がすべて、メインのAdobe Commerce版の一部としてインストールされていることです。

現在、この問題に対する一元的な解決策はありませんが、Composerはギャップを埋める方法を提供します。 [`cweagans/composer-patches`](https://packagist.org/packages/cweagans/composer-patches) パッケージでは、依存関係[&#128279;](https://github.com/cweagans/composer-patches/tree/1.x#allowing-patches-to-be-applied-from-dependencies)から パッチを適用できます。 すべてのパッチをインストールするComposer パッケージを作成し、そのパッケージをすべてのプロジェクトに必要とすることができます。

**セキュリティパッチ**、**必要なパッチ**、**コンポーザーのパッチ**&#x200B;について説明しますが、品質パッチと`/m2-hotfixes` ディレクトリの内容については何でしょうか？

## 高品質のパッチとホットフィックスの適用

`vendor/bin/magento-patches apply` コマンドを使用して、クラウドインフラストラクチャとオンプレミスの両方のインストールに高品質のパッチをインストールできます。 `vendor/bin/magento-patches apply` コマンドが`composer install`操作の後に実行されていることを確認する必要があります。

>[!NOTE]
>
>クラウド インフラストラクチャでは、プロジェクトの`.magento.env.yaml` ファイルに品質パッチをリストしてインストールすることもできます。 ここで説明する例では、`vendor/bin/magento-patches apply` コマンドを使用する必要があります。

カスタム Composer コンポーネントパッケージの`composer.json` ファイルに適用するパッチを指定し、`composer install`操作の後にコマンドを実行するプラグインパッケージを作成できます。

要約すると、この一元化されたパッチ適用の例では、2つのカスタムコンポーザーパッケージを作成する必要があります。

- **コンポーネントパッケージ：** `centralized-patcher`

   - インストールする品質パッチと`m2-hotfixes`のリストを定義します
   - `centralized-patcher-composer-plugin` パッケージが必要です。`composer install`操作の後に`vendor/bin/magento-patches apply` コマンドを実行します

- **プラグインパッケージ：** `centralized-patcher-composer-plugin`

   - `centralized-patcher` パッケージから品質パッチリストを読み取る`CentralizedPatcher` PHP クラスを定義します
   - `vendor/bin/magento-patches apply` コマンドを実行して、`composer install`操作の後に品質パッチのリストをインストールします

### `centralized-patcher`

Composer コンポーネントパッケージ （`centralized-patcher`）を作成して、すべてのAdobe Commerce インストールで高品質のパッチと`/m2-hotfixes`を一元管理できます。

コンポーネントパッケージは次の必要があります。

- デプロイメント時に、`/m2-hotfixes` ディレクトリの内容をすべてのインストールにコピーします。
- インストールする品質パッチのリストを定義します。
- `vendor/bin/magento-patches` コマンドを実行して、すべてのインストールに同じ品質パッチのリストをインストールします（[`centralized-patcher-composer-plugin`](#centralized-patcher-composer-plugin) プラグインパッケージを依存関係として使用）。

`centralized-patcher` コンポーネントパッケージを作成するには：

1. 次の内容の`composer.json` ファイルを作成します。

   >[!NOTE]
   >
   >次の例の`require`属性は、この例の後で作成する必要がある[&#x200B; プラグインパッケージ &#x200B;](#centralized-patcher-composer-plugin)に対する`require`依存関係を示しています。

   ```json
   {
    "name": "magento-services/centralized-patcher",
    "version": "0.0.1",
    "description": "Centralized patcher for patching multiple web stores from a central place",
    "type": "magento2-component",
    "license": [
        "OSL-3.0",
        "AFL-3.0"
    ],
    "require": {
        "magento-services/centralized-patcher-composer-plugin": "~0.0.1"
    },
    "require-dev": {
        "composer/composer": "^2.0"
    },
    "extra": {
        "map": [
        ],
   }
   ```

1. パッケージ内に`/m2-hotfixes` ディレクトリを作成し、`composer.json` ファイルの`map`属性に追加します。 `map`属性には、このパッケージからパッチを適用するターゲットプロジェクトのルートにコピーするファイルが含まれています。

   ```json
   {
    ...
    "extra": {
        "map": [
            [
                "/m2-hotfixes",
                "/m2-hotfixes"
            ]
        ],
   }
   ```

   >[!NOTE]
   >
   >`centralized-patcher` パッケージは、`/m2-hotfixes` ディレクトリの内容を`composer install`のターゲット プロジェクトのm2-hotfixes ディレクトリにコピーします。  クラウド展開スクリプトは`composer install`の後にm2-hotfixを適用するので、すべてのホットフィックスは展開メカニズムによってインストールされます。

1. `quality-patches`属性にインストールする品質パッチを定義します。

   ```json
   {
   ...
    "extra": {
        "map": [
            [
                "/m2-hotfixes",
                "/m2-hotfixes"
            ]
        ],
        "quality-patches": [
            "MDVA-30106",
            "MDVA-12304"
        ]
   }
   ```


前述のコードサンプルの`quality-patches`属性には、例として[&#x200B; フルパッチリスト &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)の2つのパッチが含まれています。  これらの品質のパッチは、`vendor/bin/magento-patches apply` コマンドを使用して`centralized-patcher` パッケージを必要とするすべてのプロジェクトにインストールされます。

テストの目的で、サンプル パッチ （`/m2-hotfixes/EXAMPLE-PATCH_2.4.6.patch`）を作成できます。

>[!NOTE]
>
>Adobe Commerce サポートから直接受け取ったパッチと共に、独自のパッチを`m2-hotfixes` ディレクトリに配置する必要があります。

パッチ ファイルの例（`/m2-hotfixes/EXAMPLE-PATCH_2.4.6.patch`）:

```diff
diff --git a/vendor/magento/framework/Mview/View/Subscription.php b/vendor/magento/framework/Mview/View/Subscription.php
index 03a3bf9..681e0b0 100644
--- a/vendor/magento/framework/Mview/View/Subscription.php
+++ b/vendor/magento/framework/Mview/View/Subscription.php
@@ -16,6 +16,7 @@ use Magento\Framework\Mview\ViewInterface;
 
 /**
  * Mview subscription.
+ * Test Patch File
  */
 class Subscription implements SubscriptionInterface
 {
```

### `centralized-patcher-composer-plugin`

この例では、オンプレミス メソッドを使用して品質のパッチをインストールするため、`composer install`操作の後に`vendor/bin/magento-patches apply` コマンドが実行されていることを確認する必要があります。 このプラグインは、`vendor/bin/magento-patches apply` コマンドを実行する`composer install`操作の後にトリガーされます。

`centralized-patcher-compose-plugin` コンポーネントパッケージを作成するには：

1. 次の内容の`composer.json` ファイルを作成します。

   ```json
   {
    "name": "magento-services/centralized-patcher-composer-plugin",
    "version": "0.0.1",
    "description": "Centralized patcher composer plugin to apply quality patches from the centralized patcher",
    "type": "composer-plugin",
    "license": [
        "OSL-3.0",
        "AFL-3.0"
    ],
    "require": {
        "symfony/process": "^4.1 || ^5.1",
        "magento/magento-cloud-patches": "~1.0.20",
        "magento/framework": "~103.0.5-p1",
        "composer-plugin-api": "^2.0"
    },
    "require-dev": {
        "composer/composer": "^2.0"
    },
    "suggest": {
        "magento-services/centralized-patcher": "~0.0.1"
    },
    "autoload": {
        "psr-4": {
            "MagentoServices\\CentralizedPatcherComposerPlugin\\": ""
        }
    },
    "extra": {
        "class": "MagentoServices\\CentralizedPatcherComposerPlugin\\Patcher"
    }
   }
   ```

1. PHP ファイルを作成し、`CentralizedPatcher` クラスを定義して、[`centralized-patcher`](#centralized-patcher) コンポーネントパッケージから品質パッチリストを読み取り、`composer install`操作の直後にインストールします。

   ```php
   <?php
   declare(strict_types=1);
   
   namespace MagentoServices\CentralizedPatcherComposerPlugin;
   
   use Composer\Composer;
   use Composer\EventDispatcher\EventSubscriberInterface;
   use Composer\IO\IOInterface;
   use Composer\Plugin\PluginInterface;
   use Composer\Script\ScriptEvents;
   use Symfony\Component\Process\Exception\ProcessFailedException;
   use Symfony\Component\Process\Process;
   
   class Patcher implements PluginInterface, EventSubscriberInterface
   {
    /**
     * @var Composer $composer
     */
    protected $composer;
   
    /**
     * @var IOInterface $io
     */
    protected $io;
   
    /**
     * @param Composer $composer
     * @param IOInterface $io
     * @return void
     */
    public function activate(Composer $composer, IOInterface $io)
    {
        $this->composer = $composer;
        $this->io = $io;
    }
   
    /**
     * @param Composer $composer
     * @param IOInterface $io
     * @return void
     */
    public function deactivate(Composer $composer, IOInterface $io)
    {
        // Method must exist
    }
   
    /**
     * @param Composer $composer
     * @param IOInterface $io
     * @return void
     */
    public function uninstall(Composer $composer, IOInterface $io)
    {
        // Method must exist
    }
   
    /**
     * @return string[]
     */
    public static function getSubscribedEvents()
    {
        return [
            ScriptEvents::POST_UPDATE_CMD => 'installPatches',
            ScriptEvents::POST_INSTALL_CMD => 'installPatches',
        ];
    }
   
    /**
     * Apply patches from magento-services/centralized-patcher
     *
     * @param \Composer\Script\Event $event
     * @return void
     */
    public function installPatches(\Composer\Script\Event $event)
    {
        $patches = [];
        $this->io->write('Applying centralized quality patches');
        $packages = $this->composer->getLocker()->getLockData()['packages'];
        foreach ($packages as $package) {
            if ($package['name'] !== 'magento-services/centralized-patcher') {
                continue;
            }
            $patches = $package['extra']['quality-patches'] ?? [];
        }
        if (empty($patches)) {
            $this->io->error("No centralized quality patches to install");
            exit(0);
        }
        $command = array_merge(
            ['php','./vendor/bin/magento-patches','apply','--no-interaction'],
             $patches
        );
        $process = new Process($command);
        try {
            $this->io->debug($process->getCommandLine());
            $process->mustRun();
            $this->io->write(
                str_replace("\n\n", "\n", trim($process->getErrorOutput() ?: $process->getOutput(), "\n"))
            );
        } catch (ProcessFailedException $e) {
            $process = $e->getProcess();
            $error = sprintf(
                'The command "%s" failed. %s',
                $process->getCommandLine(),
                trim($process->getErrorOutput() ?: $process->getOutput(), "\n")
            );
            throw new \RuntimeException($error, $process->getExitCode());
        }
    }
   }
   ```

>[!TIP]
>
>この例で説明されている2つのパッケージの実際については、[code-examples](#code-examples)を参照してください。


## プロジェクト固有のパッチの処理方法

すべてのプロジェクトで必要なパッチの95%のみが適用され、一部のパッチは特定のインスタンスにのみ適用されるシナリオがある場合があります。 パッチを適用する通常の方法は引き続き機能します。 プロジェクト固有のパッチは`/m2-hotfixes` ディレクトリに保存し、プロジェクトごとに品質のパッチをインストールできます。

このアプローチを使用する場合、**は`centralized-patcher` コンポーネントパッケージによってプロジェクトにコピーされた`/m2-hotfixes` ディレクトリのパッチを** コミットしません。 `/m2-hotfixes`を`.gitignore` ファイルに追加することで、誤ったコミットを防ぐことができます。 `.gitignore` ファイルを更新した後、`git add –force` コマンドを使用して、プロジェクト固有の`/m2-hotfixes`を追加する必要があることを忘れないでください。

## Adobe Commerceの様々なバージョンを実行

`centralized-patcher` コンポーネントパッケージで適切な依存関係を設定していることを確認してください。 例えば、パッケージの特定のバージョンに対してAdobe Commerce 2.4.5-p2が必要になる場合があり、Adobe Commerce 2.4.5-p2と互換性のあるパッチのみが提供されます。 このパッケージの別のバージョンが、Adobe Commerce 2.4.4と互換性がある場合があります。

## 結果の把握

Adobe Commerce on cloud infrastructureと同様に、この記事では、デプロイメントプロセスで`composer update`または`git pull`ではなく`composer install` コマンドを使用して新しいコードをサーバーにデプロイすることを前提としています。 一元化されたパッチのインストールのフローは次のようになります。

1. Composer インストール

   - -p1または – p2のセキュリティおよび機能パッチを含むAdobe Commerceをインストールします
   - 一元化された`/m2-hotfixes`とサポートパッチをプロジェクト固有の`/m2-hotfixes`とサポートパッチと組み合わせる
   - `cweagans/composer-patches` Composer パッケージと共にインストールされているすべてのパッチを適用します

1. `composer install`以降

   - Composer プラグインは、一元化された品質パッチをインストールします

1. 展開

   - 必要なパッチとプロジェクト固有の品質パッチは、`.magento.env.yaml` ファイルに基づいてインストールされます（Adobe Commerce クラウドインフラストラクチャプロジェクトのみ）。
   - `/m2-hotfixes` ディレクトリのカスタムパッチとサポートパッチは、パッチ名でアルファベット順にインストールされます。

これにより、すべてのインストールのすべてのパッチを一元管理でき、Adobe Commerce ストアのセキュリティと安定性をより確実に保証できます。 パッチのステータスを確認するには、次の方法を使用します。

- [クラウドインフラプロジェクト](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja#view-available-patches-and-status)
- [オンプレミスプロジェクト](../../../tools/quality-patches-tool/usage.md#view-individual-patches)

## コード例

- [Magento Open Sourceの一元化されたパッチ](https://github.com/AntonEvers/centralized-patches-on-magento-open-source)
- [Adobe Commerce on cloud infrastructureの一元化されたパッチ](https://github.com/AntonEvers/centralized-patches-on-adobe-commerce-cloud)
- [一元化されたパッチャー構成プラグイン](https://github.com/AntonEvers/centralized-patcher-composer-plugin)
- [一元化されたパッチャーコンポーネント](https://github.com/AntonEvers/centralized-patcher)
