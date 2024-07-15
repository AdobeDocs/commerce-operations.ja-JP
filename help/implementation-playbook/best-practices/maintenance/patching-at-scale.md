---
title: パッチを大規模に配布するためのベストプラクティス
description: Adobe Commerceのパッチ適用の一元化がエンタープライズプロジェクトの管理にどのように役立つかを説明します。
role: Developer
feature: Best Practices
badge: label="執筆：Adobe、シニアテクニカルアーキテクト、Anton Evers" type="Informative" url="https://www.linkedin.com/in/anton-evers/" tooltip="執筆：Anton Evers"
exl-id: 08c38dc5-3dc2-49ee-b56f-59e1718e12b5
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '1259'
ht-degree: 0%

---

# Adobe Commerce パッチの大規模な配布のベストプラクティス

複数のAdobe Commerceのインストールを管理する場合、[ パッチ適用 ](../../../upgrade/patches/apply.md) は複雑なプロセスになる場合があります。 _一元的なパッチ適用_ は、[ グローバルな参照アーキテクチャ ](../../architecture/global-reference/overview.md) の不可欠な部分であり、企業にとってのベストプラクティスです。 これにより、すべてのAdobe Commerce インストールに適切なパッチを適用できます。 ここでは、すべてのタイプのAdobe Commerce[ パッチ ](../../../upgrade/patches/overview.md) に対して一元的なパッチ配布を実現する方法について説明します。

>[!NOTE]
>
>以下の内容は、元々Adobeテクニカルブログの [ 大規模なAdobe Commerce パッチの配布 ](https://blog.developer.adobe.com/distributing-adobe-commerce-patches-at-scale-137412e05a20) 投稿で公開されたものです。 一元的なパッチ適用戦略を実装するための手順とコードサンプルに重点を置くように変更されました。 ここで説明する様々なタイプのパッチの詳細については、元の投稿を参照してください。

## 影響を受ける製品とバージョン

[ サポートされているすべてのバージョン ](../../../release/versions.md):

- クラウドインフラストラクチャー上のAdobe Commerce
- Adobe Commerceオンプレミス

## 方法

パッチには様々な種類があり、適用する方法も多数あるので、最初に適用されるパッチを把握するにはどうすればよいでしょうか。 パッチの数が多いほど、同じファイルや同じコード行に適用される可能性が高くなります。 パッチは次の順序で適用されます。

1. **セキュリティパッチ** は、Adobe Commerce リリースの静的コードベースの一部です。
1. **cweagans/composer-patches** などの `composer install` および `composer update` プラグインを使用した [Composer パッチ ](https://packagist.org/packages/cweagans/composer-patches)。
1. **Commerce用クラウドパッチ** パッケージに含まれるすべての [ 必須パッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches.html)。
1. 選択した **品質パッチ** が [!DNL [Quality Patches Tool]](../../../tools/quality-patches-tool/usage.md) に含まれています。
1. **カスタムパッチ** およびAdobe Commerceは、パッチ名のアルファベット順に `/m2-hotfixes` ディレクトリ内のパッチをサポートします。

   >[!IMPORTANT]
   >
   >適用するパッチが多いほど、コードがより複雑になります。 複雑なコードを使用すると、Adobeコマースの新しいバージョンへのアップグレードがより難しくなり、総所有コストが増加する場合があります。

Adobe Commerceの複数のインストールを管理する必要がある場合は、すべてのインスタンスに同じパッチセットをインストールするのは困難なことがあります。 インストールごとに、独自の Git リポジトリ、`/m2-hotfixes` ディレクトリ、`composer.json` ファイルが用意されています。 唯一の保証は、クラウドユーザー向けの **セキュリティパッチ** および **必要なパッチ** がすべてメインのAdobe Commerce バージョンの一部としてインストールされることです。

現在のところ、この問題に対する一元的なソリューションはありませんが、Composer はギャップを埋める方法を提供しています。 [`cweagans/composer-patches`](https://packagist.org/packages/cweagans/composer-patches) パッケージを使用すると、[ 依存関係からパッチを適用 ](https://github.com/cweagans/composer-patches/tree/1.x#allowing-patches-to-be-applied-from-dependencies) できます。 すべてのパッチをインストールする Composer パッケージを作成し、すべてのプロジェクトでそのパッケージを必要とすることができます。

**セキュリティパッチ**、**必須パッチ**、および **Composer パッチ** について説明しますが、品質パッチおよび `/m2-hotfixes` ディレクトリの内容についてはどうですか？

## 品質向上パッチおよびホットフィックスの適用

`vendor/bin/magento-patches apply` コマンドを使用すると、クラウドインフラストラクチャとオンプレミスの両方のインストールにクオリティパッチをインストールできます。 `composer install` の操作後に `vendor/bin/magento-patches apply` コマンドが実行されることを確認する必要があります。

>[!NOTE]
>
>クラウドインフラストラクチャーでは、プロジェクトの `.magento.env.yaml` ファイルに品質向上パッチを一覧表示してインストールすることもできます。 ここで説明する例では、`vendor/bin/magento-patches apply` コマンドを使用する必要があります。

カスタム Composer コンポーネント パッケージの `composer.json` ファイルに適用するパッチを指定し、`composer install` の操作後にコマンドを実行するプラグイン パッケージを作成できます。

まとめると、この一元的なパッチ適用の例では、次の 2 つのカスタム Composer パッケージを作成する必要があります。

- **コンポーネントパッケージ：** `centralized-patcher`

   - インストールする品質向上パッチおよび `m2-hotfixes` のリストを定義します。
   - `composer install` の操作後に `vendor/bin/magento-patches apply` コマンドを実行する `centralized-patcher-composer-plugin` パッケージが必要です

- **プラグイン パッケージ：** `centralized-patcher-composer-plugin`

   - `centralized-patcher` パッケージから品質向上パッチリストを読み取る `CentralizedPatcher` PHP クラスを定義します。
   - `vendor/bin/magento-patches apply` コマンドを実行して、`composer install` 操作後に品質向上パッチのリストをインストールします

### `centralized-patcher`

Composer コンポーネントパッケージ（`centralized-patcher`）を作成して、すべてのAdobe Commerce インストールにわたって、すべての品質向上のパッチおよび `/m2-hotfixes` ールを一元的に管理できます。

コンポーネントパッケージには次の条件があります。

- デプロイ時に、`/m2-hotfixes` ディレクトリの内容をすべてのインストールにコピーします。
- インストールする品質向上パッチのリストを定義します。
- `vendor/bin/magento-patches` コマンドを実行して、すべてのインストールで同じ品質パッチのリストをインストールします（[`centralized-patcher-composer-plugin`](#centralized-patcher-composer-plugin) プラグインパッケージを依存関係として使用）。

`centralized-patcher` コンポーネントパッケージを作成するには：

1. 次の内容の `composer.json` ファイルを作成します。

   >[!NOTE]
   >
   >次の例の `require` 属性は、この例で後で作成する必要がある [plugin パッケージ ](#centralized-patcher-composer-plugin) への `require` しい依存関係を示しています。

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

1. パッケージ内に `/m2-hotfixes` ディレクトリを作成し、`composer.json` ファイルの `map` 属性に追加します。 `map` 属性には、このパッケージからパッチを適用するターゲットプロジェクトのルートにコピーするファイルが含まれます。

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
   >`centralized-patcher` パッケージは、`/m2-hotfixes` ディレクトリの内容を、`composer install` 上のターゲットプロジェクトの m2-hotfixes ディレクトリにコピーします。  クラウドのデプロイメントスクリプトは `composer install` 後に m2-hotfix を適用するので、すべてのホットフィックスはデプロイメントメカニズムによってインストールされます。

1. インストールする品質向上パッチを `quality-patches` 属性で定義します。

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


前述のコードサンプルの `quality-patches` 属性には、例として [ 完全なパッチリスト ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) の 2 つのパッチが含まれています。  これらの品質向上パッチは、`vendor/bin/magento-patches apply` コマンドを使用して、`centralized-patcher` パッケージを必要とするすべてのプロジェクトにインストールされます。

テストを目的として、サンプルのパッチ（`/m2-hotfixes/EXAMPLE-PATCH_2.4.6.patch`）を作成できます。

>[!NOTE]
>
>独自のパッチを、Adobe Commerce サポートから直接受け取ったパッチと共に、`m2-hotfixes` ディレクトリに配置する必要があります。

パッチファイル（`/m2-hotfixes/EXAMPLE-PATCH_2.4.6.patch`）の例は次のとおりです。

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

この例ではオンプレミス方式を使用して品質向上パッチをインストールするため、`composer install` の操作後に `vendor/bin/magento-patches apply` コマンドが実行されていることを確認する必要があります。 このプラグインは、`vendor/bin/magento-patches apply` コマンドを実行する `composer install` 操作の後にトリガーされます。

`centralized-patcher-compose-plugin` コンポーネントパッケージを作成するには：

1. 次の内容の `composer.json` ファイルを作成します。

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

1. PHP ファイルを作成し、`CentralizedPatcher` クラスを定義して、[`centralized-patcher`](#centralized-patcher) コンポーネントパッケージから品質向上パッチリストを読み取り、`composer install` の操作のたびに直ちにインストールします。

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
>この例で説明している 2 つのパッケージを実際に表示するには、[code-examples](#code-examples) を参照してください。


## プロジェクト固有のパッチの対処方法

すべてのプロジェクトでパッチの 95% のみが必要で、いくつかのパッチが特定のインスタンスにのみ適用されるというシナリオが考えられます。 パッチ適用を適用する通常の方法は、引き続き機能します。 プロジェクト固有のパッチを `/m2-hotfixes` ディレクトリに保持し、プロジェクトごとに品質パッチをインストールできます。

この方法を使用する場合は、`centralized-patcher` コンポーネントパッケージによってプロジェクトにコピーされた `/m2-hotfixes` ディレクトリ内のパッチを **コミットしない** でください。 `.gitignore` ファイルに `/m2-hotfixes` を追加することで、誤ったコミットを防ぐことができます。 `.gitignore` ファイルを更新した後は、`git add –force` コマンドを使用してプロジェクト固有の `/m2-hotfixes` を追加する必要があることに注意してください。

## 異なるバージョンのAdobe Commerceの実行

`centralized-patcher` コンポーネントパッケージに正しい依存関係を設定していることを確認します。 例えば、パッケージの特定のバージョンに対してAdobe Commerce 2.4.5-p2 が必要な場合、Adobe Commerce 2.4.5-p2 と互換性のあるパッチのみが提供されます。 このパッケージには、Adobe Commerce 2.4.4 と互換性のある別のバージョンが含まれている場合があります。

## 結果について

クラウドインフラストラクチャー上のAdobe Commerceの場合と同様に、この記事では、デプロイメントプロセスで新しいコードをサーバーにデプロイする際に `composer update` や `git pull` ではなく、`composer install` コマンドを使用することを前提としています。 一元化されたパッチインストールのフローは、次のようになります。

1. Composer のインストール

   - -p1 または – p2 のセキュリティおよび機能パッチを含むAdobe Commerceをインストールします。
   - 一元化された `/m2-hotfixes` およびサポートパッチと、プロジェクト固有の `/m2-hotfixes` およびサポートパッチを組み合わせる
   - `cweagans/composer-patches` Composer パッケージとともにインストールされるパッチを適用します。

1. `composer install` 後

   - Composer プラグインは、集中管理品質パッチをインストールします

1. デプロイメント

   - 必要なパッチおよびプロジェクト固有の高品質のパッチは、`.magento.env.yaml` ファイルに基づいてインストールされます（クラウドインフラストラクチャプロジェクト上のAdobe Commerceのみ）。
   - `/m2-hotfixes` ディレクトリにあるカスタムパッチおよびサポートパッチは、パッチ名のアルファベット順にインストールされます。

これにより、すべてのインストールに対するすべてのパッチを一元的に管理でき、Adobe Commerce ストアのセキュリティと安定性をより確実に保証できます。 次の方法を使用して、パッチステータスを確認します。

- [ クラウドインフラストラクチャプロジェクト ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html#view-available-patches-and-status)
- [オンプレミス プロジェクト](../../../tools/quality-patches-tool/usage.md#view-individual-patches)

## コードの例

- [Magento Open Sourceでのパッチの一元化 ](https://github.com/AntonEvers/centralized-patches-on-magento-open-source)
- [ クラウドインフラストラクチャー上のAdobe Commerceにパッチを一元化 ](https://github.com/AntonEvers/centralized-patches-on-adobe-commerce-cloud)
- [Centralized Patcher Composer プラグイン ](https://github.com/AntonEvers/centralized-patcher-composer-plugin)
- [ 一元化された Patcher コンポーネント ](https://github.com/AntonEvers/centralized-patcher)
