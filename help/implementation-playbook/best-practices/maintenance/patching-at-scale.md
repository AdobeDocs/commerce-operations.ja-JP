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

複数のAdobe Commerce インストールを管理する場合、 [パッチ](../../../upgrade/patches/apply.md) 複雑なプロセスになる場合があります。 _一元的なパッチ適用_ ～の重要な部分である [グローバル参照アーキテクチャ](../../architecture/global-reference/overview.md) 企業にとってのベストプラクティスです。 これにより、すべてのAdobe Commerce インストールに適切なパッチを適用できます。 このトピックでは、すべてのタイプのAdobe Commerceで一元的なパッチ配布を実現する方法について説明します [パッチ](../../../upgrade/patches/overview.md).

>[!NOTE]
>
>次のコンテンツは、最初にで公開されました [大規模なAdobe Commerce パッチの配布](https://blog.developer.adobe.com/distributing-adobe-commerce-patches-at-scale-137412e05a20) Adobeテクニカルブログに投稿します。 一元的なパッチ適用戦略を実装するための手順とコードサンプルに重点を置くように変更されました。 ここで説明する様々なタイプのパッチの詳細については、元の投稿を参照してください。

## 影響を受ける製品とバージョン

[サポートされているすべてのバージョン](../../../release/versions.md) （件中）:

- クラウドインフラストラクチャー上のAdobe Commerce
- Adobe Commerceオンプレミス

## 方法

パッチには様々な種類があり、適用する方法も多数あるので、最初に適用されるパッチを把握するにはどうすればよいでしょうか。 パッチの数が多いほど、同じファイルや同じコード行に適用される可能性が高くなります。 パッチは次の順序で適用されます。

1. **セキュリティパッチ** は、Adobe Commerce リリースの静的コードベースの一部です。
1. **Composer パッチ** から `composer install` および `composer update` プラグイン（例：） [cweagans/composer-patches](https://packagist.org/packages/cweagans/composer-patches).
1. すべて **必要なパッチ** 次に含まれる [Commerceのクラウドパッチ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches.html) パッケージ。
1. 個選択済み **品質向上パッチ** 次に含まれる [!DNL [Quality Patches Tool]](../../../tools/quality-patches-tool/usage.md).
1. **カスタムパッチ** および内のAdobe Commerce サポートパッチ `/m2-hotfixes` パッチ名のアルファベット順のディレクトリ。

   >[!IMPORTANT]
   >
   >適用するパッチが多いほど、コードがより複雑になります。 複雑なコードを使用すると、Adobeコマースの新しいバージョンへのアップグレードがより難しくなり、総所有コストが増加する場合があります。

Adobe Commerceの複数のインストールを管理する必要がある場合は、すべてのインスタンスに同じパッチセットをインストールするのは困難なことがあります。 インストールごとに専用の Git リポジトリがあります。 `/m2-hotfixes` ディレクトリおよび `composer.json` ファイル。 唯一の保証は **セキュリティパッチ** および **必要なパッチ** cloud ユーザーの場合、すべてメインのAdobe Commerce バージョンの一部としてインストールされます。

現在のところ、この問題に対する一元的なソリューションはありませんが、Composer はギャップを埋める方法を提供しています。 この [`cweagans/composer-patches`](https://packagist.org/packages/cweagans/composer-patches) パッケージでは、次のことが可能です [依存関係からパッチを適用する](https://github.com/cweagans/composer-patches/tree/1.x#allowing-patches-to-be-applied-from-dependencies). すべてのパッチをインストールする Composer パッケージを作成し、すべてのプロジェクトでそのパッケージを必要とすることができます。

対象 **セキュリティパッチ**, **必要なパッチ**、および **Composer パッチ**&#x200B;ただし、品質パッチとその内容についてはどうでしょうか。 `/m2-hotfixes` ディレクトリ？

## 品質向上パッチおよびホットフィックスの適用

を使用して、クラウドインフラストラクチャとオンプレミスのインストールの両方にクオリティパッチをインストールできます。 `vendor/bin/magento-patches apply` コマンド。 必ずを実行する必要があります `vendor/bin/magento-patches apply` 次の後にコマンドを実行 `composer install` の操作。

>[!NOTE]
>
>クラウドインフラストラクチャでは、プロジェクトのにクオリティパッチをリストしてインストールすることもできます。 `.magento.env.yaml` ファイル。 ここで説明する例では、を使用する必要があります `vendor/bin/magento-patches apply` コマンド。

に適用するパッチを指定できます。 `composer.json` カスタム Composer コンポーネント パッケージのファイルを作成し、の後にコマンドを実行するプラグイン パッケージを作成します `composer install` の操作。

まとめると、この一元的なパッチ適用の例では、次の 2 つのカスタム Composer パッケージを作成する必要があります。

- **コンポーネントパッケージ：** `centralized-patcher`

   - 品質向上パッチのリストと `m2-hotfixes` インストールする
   - には次が必要です `centralized-patcher-composer-plugin` を実行するパッケージ `vendor/bin/magento-patches apply` 次の後のコマンド `composer install` の操作

- **プラグインパッケージ：** `centralized-patcher-composer-plugin`

   - を定義します `CentralizedPatcher` 品質向上パッチリストを読み取る PHP クラス `centralized-patcher` package
   - を実行します `vendor/bin/magento-patches apply` 品質向上パッチのリストのインストール後に実行するコマンド `composer install` の操作

### `centralized-patcher`

Composer コンポーネントパッケージ（`centralized-patcher`）を使用して、すべての品質向上パッチを一元管理できます。 `/m2-hotfixes` すべてのAdobe Commerce インストールをまたいで実行できます。

コンポーネントパッケージには次の条件があります。

- の内容をコピーします `/m2-hotfixes` 配置時にすべてのインストールにディレクトリを配置します。
- インストールする品質向上パッチのリストを定義します。
- を実行 `vendor/bin/magento-patches` すべてのインストールで同じ品質パッチのリストをインストールするコマンド（ [`centralized-patcher-composer-plugin`](#centralized-patcher-composer-plugin) プラグインパッケージ （依存関係として）。

を作成するには `centralized-patcher` コンポーネントパッケージ：

1. を作成 `composer.json` 次の内容のファイル。

   >[!NOTE]
   >
   >この `require` 次の例の属性は、 `require` への依存 [プラグインパッケージ](#centralized-patcher-composer-plugin) この例は後で作成する必要があります。

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

1. を作成 `/m2-hotfixes` パッケージ内のディレクトリを選択して、に追加します。 `map` の属性 `composer.json` ファイル。 この `map` 属性には、このパッケージからパッチを適用するターゲットプロジェクトのルートにコピーするファイルが含まれます。

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
   >この `centralized-patcher` パッケージでは、の内容をコピーします `/m2-hotfixes` ディレクトリから、ターゲットプロジェクトの m2-hotfixes ディレクトリ `composer install`.  クラウドデプロイメントスクリプトは、m2-hotfix をの後に適用するので、 `composer install`の場合、すべてのホットフィックスはデプロイメントメカニズムによってインストールされます。

1. にインストールする品質向上パッチの定義 `quality-patches` 属性。

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


この `quality-patches` 上記のコードサンプルの属性には、から 2 つのパッチが含まれています [完全なパッチリスト](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) 例えば、次のようになります。  これらの品質向上パッチは、 `centralized-patcher` を使用したパッケージ `vendor/bin/magento-patches apply` コマンド。

テストを目的として、サンプルのパッチ（`/m2-hotfixes/EXAMPLE-PATCH_2.4.6.patch`）に設定します。

>[!NOTE]
>
>パッチは、 `m2-hotfixes` ディレクトリと、Adobe Commerce サポートから直接受け取るパッチ。

パッチファイルの例（`/m2-hotfixes/EXAMPLE-PATCH_2.4.6.patch`）:

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

この例ではオンプレミス方式を使用して品質パッチをインストールするため、次のことを確認する必要があります `vendor/bin/magento-patches apply` 次の後にコマンドを実行 `composer install` の操作。 このプラグインは次の場合にトリガーされます `composer install` を実行する操作 `vendor/bin/magento-patches apply` コマンド。

を作成するには `centralized-patcher-compose-plugin` コンポーネントパッケージ：

1. を作成 `composer.json` 次の内容のファイル。

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

1. PHP ファイルを作成し、 `CentralizedPatcher` 品質パッチリストを読み取るクラス [`centralized-patcher`](#centralized-patcher) コンポーネントをパッケージ化し、次の間隔で直ちにインストールする： `composer install` 操作。

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
>を参照してください。 [コード例](#code-examples) をクリックして、この例で説明している 2 つのパッケージを実際に確認します。


## プロジェクト固有のパッチの対処方法

すべてのプロジェクトでパッチの 95% のみが必要で、いくつかのパッチが特定のインスタンスにのみ適用されるというシナリオが考えられます。 パッチ適用を適用する通常の方法は、引き続き機能します。 プロジェクト固有のパッチは、 `/m2-hotfixes` プロジェクトごとのディレクトリおよびインストール品質パッチ

この方法を使用する場合、 **実行しない** 内のパッチをコミットする `/m2-hotfixes` によってプロジェクトにコピーされたディレクトリ `centralized-patcher` コンポーネントパッケージ。 を追加することで、誤ったコミットを防ぐことができます。 `/m2-hotfixes` 宛先： `.gitignore` ファイル。 の更新後 `.gitignore` ファイル、プロジェクト固有であることに注意してください `/m2-hotfixes` を使用して追加する必要があります `git add –force` コマンド。

## 異なるバージョンのAdobe Commerceの実行

で適切な依存関係を設定していることを確認してください。 `centralized-patcher` コンポーネントパッケージ。 例えば、パッケージの特定のバージョンに対してAdobe Commerce 2.4.5-p2 が必要な場合、Adobe Commerce 2.4.5-p2 と互換性のあるパッチのみが提供されます。 このパッケージには、Adobe Commerce 2.4.4 と互換性のある別のバージョンが含まれている場合があります。

## 結果について

クラウドインフラストラクチャー上のAdobe Commerceと同様に、この記事では、デプロイメントプロセスではを使用することを前提としています `composer install` command と not `composer update` または `git pull` サーバーに新しいコードをデプロイする場合。 一元化されたパッチインストールのフローは、次のようになります。

1. Composer のインストール

   - -p1 または – p2 のセキュリティおよび機能パッチを含むAdobe Commerceをインストールします。
   - 一元化された `/m2-hotfixes` およびプロジェクト固有のパッチをサポート `/m2-hotfixes` およびサポートパッチ
   - と共にインストールされたパッチを適用します `cweagans/composer-patches` Composer パッケージ

1. 後 `composer install`

   - Composer プラグインは、集中管理品質パッチをインストールします

1. デプロイメント

   - 必要なパッチおよびプロジェクト固有の品質パッチは、 `.magento.env.yaml` ファイル （クラウドインフラストラクチャプロジェクト上のAdobe Commerceのみ）。
   - カスタムパッチおよびサポートパッチ `/m2-hotfixes` ディレクトリは、パッチ名のアルファベット順にインストールされます。

これにより、すべてのインストールに対するすべてのパッチを一元的に管理でき、Adobe Commerce ストアのセキュリティと安定性をより確実に保証できます。 次の方法を使用して、パッチステータスを確認します。

- [クラウドインフラストラクチャプロジェクト](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html#view-available-patches-and-status)
- [オンプレミス プロジェクト](../../../tools/quality-patches-tool/usage.md#view-individual-patches)

## コードの例

- [Magento Open Sourceでのパッチの一元化](https://github.com/AntonEvers/centralized-patches-on-magento-open-source)
- [クラウドインフラストラクチャー上のAdobe Commerceにパッチを一元化](https://github.com/AntonEvers/centralized-patches-on-adobe-commerce-cloud)
- [一元化された Patcher Composer プラグイン](https://github.com/AntonEvers/centralized-patcher-composer-plugin)
- [一元化された Patcher コンポーネント](https://github.com/AntonEvers/centralized-patcher)
