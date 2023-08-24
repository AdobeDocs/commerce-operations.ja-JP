---
title: 大規模なパッチ配布のベストプラクティス
description: エンタープライズプロジェクトの管理にAdobe Commerce向けの一元化されたパッチ適用が役立つ方法を説明します。
role: Developer
feature: Best Practices
badge: label="貢献：Anton Evers 氏、シニアテクニカルアーキテクト、Adobe" type="Informative" url="https://www.linkedin.com/in/anton-evers/" tooltip="Anton Evers による貢献"
source-git-commit: d8ee656b4b1741b39f2eef1f5628a299377e774c
workflow-type: tm+mt
source-wordcount: '1309'
ht-degree: 0%

---


# Adobe Commerceパッチを大規模に配布するためのベストプラクティス

複数のAdobe Commerceインストールを管理する場合は、 [パッチ適用](../../../upgrade/patches/apply.md) は複雑なプロセスになる場合があります。 _一元化されたパッチ適用_ ～の重要な部分である [グローバルリファレンスアーキテクチャ](../../architecture/global-reference.md) 企業にとってのベスト・プラクティス これにより、すべてのAdobe Commerceインストールに適切なパッチを適用できます。 このトピックでは、すべてのタイプのAdobe Commerceに対して一元化されたパッチ配布を実現する方法を説明します [パッチ](../../../upgrade/patches/overview.md).

>[!NOTE]
>
>次のコンテンツは、元々 [Adobe Commerceパッチの大規模な配布](https://blog.developer.adobe.com/distributing-adobe-commerce-patches-at-scale-137412e05a20) Tech BlogAdobeに投稿します。 一元化されたパッチ適用戦略を実装するための手順とコードサンプルに焦点を当てるように変更されました。 ここで説明する各種パッチの詳細については、元の投稿を参照してください。

## 影響を受ける製品およびバージョン

[サポートされているすべてのバージョン](../../../release/versions.md) /:

- Adobe Commerce an cloud infrastructure
- Adobe Commerceオンプレミス

## 方法

さまざまな種類のパッチがあり、それらを適用する方法が多いので、どのパッチが最初に適用されるかを知るにはどうしたらよいですか。 パッチが多いほど、同じファイルやコード行に適用される可能性が高くなります。 パッチは次の順序で適用されます。

1. **セキュリティパッチ** は、Adobe Commerceリリースの静的コードベースの一部です。
1. **Composer パッチ** 経由 `composer install` および `composer update` プラグイン ( [cweagans/composer-patches](https://packagist.org/packages/cweagans/composer-patches).
1. すべて **必要なパッチ** 次に含まれる [コマース用クラウドパッチ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches.html) パッケージ。
1. 選択済み **品質パッチ** 次に含まれる [!DNL [Quality Patches Tool]](../../../tools/quality-patches-tool/usage.md).
1. **カスタムパッチ** およびAdobe Commerce Support パッチ ( `/m2-hotfixes` ディレクトリをパッチ名順にアルファベット順に表示します。

   >[!IMPORTANT]
   >
   >適用するパッチが増えると、コードがより複雑になります。 複雑なコードを使用すると、新しいバージョンのAdobeコマースへのアップグレードがより難しくなり、TCO（総所有コスト）が増加します。

Adobe Commerceの複数のインストールの管理を担当する場合は、すべてのインスタンスに同じパッチセットがインストールされていると、困難な場合があります。 インストールごとに、独自の Git リポジトリがあり、 `/m2-hotfixes` ディレクトリ、および `composer.json` ファイル。 あなたが持っている唯一の保証は、 **セキュリティパッチ** および **必要なパッチ** クラウドユーザーの場合は、すべてAdobe Commerceのメインバージョンの一部としてインストールされます。

現在、この問題に対する単一の一元化されたソリューションはありませんが、Composer はギャップを埋める方法を提供します。 The [`cweagans/composer-patches`](https://packagist.org/packages/cweagans/composer-patches) パッケージを使用すると、次のことが可能です。 [依存関係からパッチを適用する](https://github.com/cweagans/composer-patches/tree/1.x#allowing-patches-to-be-applied-from-dependencies). すべてのパッチをインストールし、そのパッケージをすべてのプロジェクトで必要とする Composer パッケージを作成できます。

対象： **セキュリティパッチ**, **必要なパッチ**、および **Composer パッチ**&#x200B;でも、品質パッチとその中身はどうなるの？ `/m2-hotfixes` ディレクトリ？

## 品質パッチとホットフィックスの適用

クラウドインフラストラクチャとオンプレミスインストールの両方に、 `vendor/bin/magento-patches apply` コマンドを使用します。 必ず `vendor/bin/magento-patches apply` 次のコマンドを実行： `composer install` 操作。

>[!NOTE]
>
>クラウドインフラストラクチャ上で、品質パッチをプロジェクトの `.magento.env.yaml` ファイル。 ここで説明する例では、 `vendor/bin/magento-patches apply` コマンドを使用します。

適用するパッチは、 `composer.json` カスタム Composer コンポーネントパッケージのファイルを作成し、次に、の後にコマンドを実行するプラグインパッケージを作成します。 `composer install` 操作。

要約すると、この一元化されたパッチ適用の例では、次の 2 つのカスタム Composer パッケージを作成する必要があります。

- **コンポーネントパッケージ：** `centralized-patcher`

   - 品質パッチのリストと `m2-hotfixes` インストールする
   - が必要です。 `centralized-patcher-composer-plugin` パッケージ（実行） `vendor/bin/magento-patches apply` 次のコマンド： `composer install` 操作

- **プラグインパッケージ：** `centralized-patcher-composer-plugin`

   - を定義します。 `CentralizedPatcher` PHP クラスで、 `centralized-patcher` パッケージ
   - を実行します。 `vendor/bin/magento-patches apply` 次の後に品質パッチのリストをインストールするコマンド `composer install` 操作

### `centralized-patcher`

コンポーザーコンポーネントパッケージ (`centralized-patcher`) すべての品質パッチを一元管理し、 `/m2-hotfixes` すべてのAdobe Commerceインストールをまたいで。

コンポーネントパッケージでは、次の要件を満たす必要があります。

- の内容をコピーします。 `/m2-hotfixes` ディレクトリを、デプロイ時にすべてのインストールに追加します。
- インストールする品質パッチのリストを定義します。
- を実行します。 `vendor/bin/magento-patches` すべてのインストールで同じ品質パッチのリストをインストールするコマンド ( [`centralized-patcher-composer-plugin`](#centralized-patcher-composer-plugin) プラグインパッケージを依存関係として使用 )。

次の手順で `centralized-patcher` コンポーネントパッケージ：

1. の作成 `composer.json` ファイルに次の内容を含めます。

   >[!NOTE]
   >
   >The `require` 次の例の属性は、 `require` 依存関係 [プラグインパッケージ](#centralized-patcher-composer-plugin) 後でこの例を作成する必要があります。

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

1. の作成 `/m2-hotfixes` パッケージ内のディレクトリに追加します。 `map` 属性 `composer.json` ファイル。 The `map` 属性には、このパッケージから、パッチを適用するターゲットプロジェクトのルートにコピーするファイルが含まれます。

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
   >The `centralized-patcher` パッケージは、 `/m2-hotfixes` ターゲットプロジェクトの m2-hotfixs ディレクトリ ( `composer install`.  クラウドデプロイメントスクリプトは、次の後に m2-hotfix を適用するので、 `composer install`に設定されている場合、すべてのホットフィックスはデプロイメントメカニズムによってインストールされます。

1. でインストールする品質パッチを定義する `quality-patches` 属性。

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


The `quality-patches` 前述のコードサンプルの属性には、 [完全パッチリスト](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) を例として示します。  これらの品質パッチは、 `centralized-patcher` パッケージを `vendor/bin/magento-patches apply` コマンドを使用します。

テストの目的で、サンプルのパッチ (`/m2-hotfixes/EXAMPLE-PATCH_2.4.6.patch`) をクリックします。

>[!NOTE]
>
>独自のパッチを `m2-hotfixes` ディレクトリに、Adobe Commerce Support から直接受け取るパッチと共に保存します。

サンプルのパッチファイル (`/m2-hotfixes/EXAMPLE-PATCH_2.4.6.patch`):

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

この例では、オンプレミス方式を使用して品質パッチをインストールするので、 `vendor/bin/magento-patches apply` 次のコマンドを実行： `composer install` 操作。 このプラグインは、次の後にトリガーされます： `composer install` 操作（実行） `vendor/bin/magento-patches apply` コマンドを使用します。

次の手順で `centralized-patcher-compose-plugin` コンポーネントパッケージ：

1. の作成 `composer.json` ファイルに次の内容を含めます。

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

1. PHP ファイルを作成し、 `CentralizedPatcher` クラスを使用して、 [`centralized-patcher`](#centralized-patcher) コンポーネントパッケージを作成し、 `composer install` 操作。

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
>詳しくは、 [code-examples](#code-examples) を使用して、この例で説明している 2 つのパッケージを実際の動作で確認できます。


## プロジェクト固有のパッチの処理

すべてのプロジェクトで必要なパッチは 95%に過ぎず、特定のインスタンスにのみ適用されるパッチもいくつかあります。 パッチを適用する通常の方法は、引き続き機能します。 プロジェクト固有のパッチは、 `/m2-hotfixes` プロジェクトごとの品質パッチをディレクトリにインストールします。

この方法を使用する場合、 **しない** 内のパッチをコミットする `/m2-hotfixes` によってプロジェクトにコピーされたディレクトリ `centralized-patcher` コンポーネントパッケージ。 コミットを誤って防ぐには、 `/m2-hotfixes` を `.gitignore` ファイル。 更新後 `.gitignore` ファイルを使用する場合は、プロジェクト固有の `/m2-hotfixes` は、 `git add –force` コマンドを使用します。

## 異なるAdobe Commerceバージョンの実行

正しい依存関係を `centralized-patcher` コンポーネントパッケージ。 例えば、Adobe Commerce 2.4.5-p2 と互換性のあるパッチのみを提供する、特定のバージョンのパッケージにAdobe Commerce 2.4.5-p2 が必要な場合があります。 このパッケージの別のバージョンがAdobe Commerce 2.4.4 と互換性がある場合があります。

## 結果の理解

クラウドインフラストラクチャ上のAdobe Commerceと同様に、この記事では、デプロイメントプロセスで `composer install` コマンドおよび not `composer update` または `git pull` をクリックして、新しいコードをサーバーにデプロイします。 次に、一元化されたパッチインストールのフローを次に示します。

1. Composer のインストール

   - Adobe Commerce（ —p1 または —p2 のセキュリティおよび機能パッチを含む）をインストールします。
   - 中央集中型 `/m2-hotfixes` プロジェクト固有のパッチをサポート `/m2-hotfixes` およびサポートパッチ
   - でインストールされているパッチを適用します。 `cweagans/composer-patches` Composer パッケージ

1. 後 `composer install`

   - Composer プラグインは、一元化された品質パッチをインストールします

1. 導入

   - 必要なパッチとプロジェクト固有の品質パッチは、 `.magento.env.yaml` ファイル (Adobe Commerce on cloud infrastructure projects のみ )
   - カスタムパッチとサポートパッチは、 `/m2-hotfixes` ディレクトリは、パッチ名のアルファベット順にインストールされます。

これにより、すべてのインストールに関するすべてのパッチを一元的に管理でき、Adobe Commerceストアのセキュリティと安定性をより確実に保証できます。 次の方法を使用して、パッチのステータスを確認します。

- [クラウドインフラストラクチャプロジェクト](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html#view-available-patches-and-status)
- [オンプレミスプロジェクト](../../../tools/quality-patches-tool/usage.md#view-individual-patches)

## コードの例

- [一元化されたパッチのMagento Open Source](https://github.com/AntonEvers/centralized-patches-on-magento-open-source)
- [クラウドインフラストラクチャ上のAdobe Commerceの一元化されたパッチ](https://github.com/AntonEvers/centralized-patches-on-adobe-commerce-cloud)
- [Centralized Patcher Composer プラグイン](https://github.com/AntonEvers/centralized-patcher-composer-plugin)
- [集中型パッチャーコンポーネント](https://github.com/AntonEvers/centralized-patcher)
