---
title: 静的ビューファイルのデプロイ
description: 実稼働モードで Commerce ファイルシステムに静的ファイルを書き込む方法を説明します。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '1132'
ht-degree: 0%

---


# 静的ビューファイルのデプロイ

{{file-system-owner}}

静的ビューファイル展開コマンドを使用すると、コマースソフトウェアが [実稼動モード](../bootstrap/application-modes.md#production-mode).

用語 _静的ビューファイル_ は、次を指します。

- 「静的」とは、サイトに対してキャッシュできることを意味します（つまり、ファイルが動的に生成されない）。 例としては、LESS から生成された画像や CSS があります。
- 「表示」とは、（MVC からの）プレゼンテーションレイヤーを指します。

静的ビューファイルは、 `<magento_root>/pub/static` ディレクトリ、一部は `<magento_root>/var/view_preprocessed` ディレクトリも同様です。

静的ビューファイルの展開は、次のように、アプリケーションモードの影響を受けます。

- [デフォルト](../bootstrap/application-modes.md#default-mode) および [開発者](../bootstrap/application-modes.md#developer-mode) モード：Commerce ではオンデマンドで生成されますが、残りのデータはファイルにキャッシュされ、アクセス速度が向上します。
- [実稼動](../bootstrap/application-modes.md#production-mode) モード：静的ファイルは _not_ 生成またはキャッシュ済み。

静的ビューファイルは、このトピックで説明するコマンドを使用して、手動で Commerce ファイルシステムに書き込む必要があります。その後は、アクセス許可を制限して、脆弱性を制限し、ファイルの誤った上書きや悪意のある上書きを防ぐことができます。

>[!WARNING]
>
>_開発者モードのみ_:新しいモジュールをインストールまたは有効にすると、新しい JavaScript、CSS、レイアウトなどが読み込まれる場合があります。 静的ファイルの問題を回避するには、古いファイルを消去して、新しいモジュールに対するすべての変更を確実に取得する必要があります。 生成された静的ビューファイルは、いくつかの方法で消去できます。 参照： [静的ファイルのキャッシュトピックをクリーンアップして詳細を確認](https://developer.adobe.com/commerce/frontend-core/guide/caching/#clean-static-files-cache) を参照してください。

**静的ビューファイルを配置するには**:

1. Commerce サーバーに、またはとしてログインします。 [ファイルシステムの所有者に切り替え](../../installation/prerequisites/file-system/overview.md).
1. のコンテンツを削除 `<magento_root>/pub/static`( ただし、 `.htaccess` ファイル。 このファイルは削除しないでください。
1. 静的ビューファイル展開ツールを実行する `<magento_root>/bin/magento setup:static-content:deploy`.

   >[!INFO]
   >
   >管理者で静的ビューファイルのマージを有効にした場合、 `pub/static` ディレクトリシステムは書き込み可能である必要があります。

   コマンドオプション：

   ```bash
   bin/magento setup:static-content:deploy [<languages>] [-t|--theme[="<theme>"]] [--exclude-theme[="<theme>"]] [-l|--language[="<language>"]] [--exclude-language[="<language>"]] [-a|--area[="<area>"]] [--exclude-area[="<area>"]] [-j|--jobs[="<number>"]]  [--no-javascript] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [--no-parent] [-f|--force]
   ```

次の表で、このコマンドのパラメータと値を説明します。

| オプション | 説明 | 必須？ |
| ------ | ----------- | --------- |
| `<languages>` | スペースで区切られた [ISO-639](https://www.loc.gov/standards/iso639-2/php/code_list.php) 静的ビューファイルを出力する言語コード。 ( デフォルトは `en_US`.)<br>次のコマンドを実行してリストを検索します。 `bin/magento info:language:list` | いいえ |
| `--language (-l)` | 指定した言語のファイルのみを生成します。 デフォルトでは、オプションは指定されていませんが、すべての ISO-639 言語コードのファイルを生成します。 一度に 1 つの言語コードの名前を指定できます。 デフォルト値は **すべて**.<br>例： `--language en_US --language es_ES` | いいえ |
| `--exclude-language` | 指定した言語コードのファイルを生成します。 デフォルトでは、オプションが指定されていない場合、何も除外されません。 1 つの言語コードの名前を指定するか、言語コードのコンマ区切りリストを指定できます。 デフォルト値は **なし**. | いいえ |
| `--theme <theme>` | 静的コンテンツをデプロイするテーマ。 デフォルト値は **すべて**.<br>例： `--theme Magento/blank --theme Magento/luma` | いいえ |
| `--exclude-theme <theme>` | 静的コンテンツをデプロイする際に除外するテーマ。 デフォルト値は **なし**.<br>例： `--exclude-theme Magento/blank` | いいえ |
| `--area (-a)` | 指定した領域に対してのみファイルを生成します。 デフォルトでは、オプションは指定されていませんが、すべての領域に対してファイルを生成します。 有効な値は次のとおりです。 `adminhtml` および `frontend`. デフォルト値は **すべて**.<br>例： `--area adminhtml` | いいえ |
| `--exclude-area` | 指定した領域に対してファイルを生成しないでください。 デフォルトでは、オプションが指定されていない場合、何も除外されません。 デフォルト値は **なし**. | いいえ |
| `--jobs (-j)` | 指定したジョブ数を使用して並列処理を有効にします。 デフォルトは 0 です（並列処理では実行しない）。 デフォルト値は **0**. | いいえ |
| `--symlink-locale` | これらのロケールのファイルの symlink を作成します。このファイルはデプロイ用に渡されますが、カスタマイズは行われません。 | いいえ |
| `--content-version=CONTENT-VERSION` | 静的コンテンツのカスタムバージョンは、複数のノードでデプロイメントを実行する場合に使用でき、静的コンテンツのバージョンが同じで、キャッシュが正しく機能することを確認できます。 | いいえ |
| `--no-javascript` | JavaScript ファイルをデプロイしない | いいえ |
| `--no-css` | CSS ファイルをデプロイしないでください。 | いいえ |
| `--no-less` | LESS ファイルをデプロイしないでください。 | いいえ |
| `--no-images` | 画像をデプロイしないでください。 | いいえ |
| `--no-fonts` | フォントファイルを展開しないでください。 | いいえ |
| `--no-html` | HTML・ファイルを展開しない。 | いいえ |
| `--no-misc` | 他のタイプのファイルはデプロイしないでください。MD, JBF, CSV, JSON, TXT, HTC,SWF | いいえ |
| `--no-html-minify` | HTMLファイルを縮小しない。 | いいえ |
| `-s <quick\|standard\|compact>` | デプロイメント戦略を定義します。 これらのオプションは、複数のローカルがある場合にのみ使用します。<ul><li>以下を使用： [クイック戦略](static-view-file-strategy.md#quick-strategy) を使用して、デプロイメント時間を最小限に抑えます。 指定しない場合、これはデフォルトのコマンドオプションです。</li><li>以下を使用： [標準戦略](static-view-file-strategy.md#standard-strategy) をクリックして、すべてのパッケージのすべての静的ビューファイルをデプロイします。</li><li>以下を使用： [コンパクト戦略](static-view-file-strategy.md#compact-strategy) サーバー上のディスク領域を節約する。</li></ul> | いいえ |
| `--no-parent` | 現在のテーマの親テーマのファイルを生成しないでください。 現在のテーマの親テーマを明示的に使用しない場合は、このフラグを使用することを強くお勧めします。 これにより、プロセスの速度が大幅に向上します。 このフラグは、Commerce 2.4.2 で使用できます。 | いいえ |
| `--force (-f)` | 任意のモードでファイルをデプロイします。 ( デフォルトでは、静的コンテンツデプロイメントツールは実稼動モードでのみ実行できます。 このオプションは、デフォルトまたは開発者モードで実行する場合に使用します )。 | いいえ |

>[!INFO]
>
>両方に値を指定した場合 `<languages>` および `--language`, `<languages>` が優先します。

## 例

次に、コマンドの例を示します。

### テーマとHTML縮小の除外

次のコマンドは、米国英語 (`en_US`) 言語のみを使用する場合は、Commerce で提供される Luma テーマを除外し、HTMLファイルを縮小しません。

```bash
bin/magento setup:static-content:deploy en_US --exclude-theme Magento/luma --no-html-minify
```

サンプル出力：

```terminal
Requested languages: en_US
Requested areas: frontend, adminhtml
Requested themes: Magento/blank, Magento/backend
=== frontend -> Magento/blank -> en_US ===
=== adminhtml -> Magento/backend -> en_US ===
...........................................................
... more ...
Successful: 2055 files; errors: 0
---

New version of deployed files: 1466710645
............
Successful: 1993 files; errors: 0
---
```

次のコマンドは、4 つのジョブを持つ JavaScript のみを、標準のデプロイメント戦略でデプロイします。

```bash
bin/magento setup:static-content:deploy -s standard --no-misc --no-html --no-fonts --no-images --no-less --no-css -j 4
```

次のコマンドは、3 つのジョブを持つ CSS と LESS のみをデプロイし、迅速なデプロイ方法をデプロイします。

```bash
bin/magento setup:static-content:deploy -s quick --no-misc --no-html --no-fonts --no-images --no-javascript -j 3
```

### 1 つのテーマと 1 つの領域に対する静的ビューファイルの生成

次のコマンドは、フォントを生成せずに、すべての言語、フロントエンド領域のみ、Commerce Luma テーマのみの静的ビューファイルを生成します。

```bash
bin/magento setup:static-content:deploy --area frontend --no-fonts --theme Magento/luma
```

サンプル出力：

```terminal
Requested languages: en_US
Requested areas: frontend
Requested themes: Magento/luma
=== frontend -> Magento/luma -> en_US ===
...........................................................
... more ...
........................................................................
Successful: 2092 files; errors: 0
---

New version of deployed files: 1466711110
```

## Commerce をインストールせずに静的ビューファイルをデプロイする

機密性の高い実稼動マシン上のビルドプロセスを避けるために、デプロイメントプロセスを別の非実稼動環境で実行する必要がある場合があります。

それには、次の手順に従います。

1. 実行 [`bin/magento app:config:dump`](../cli/export-configuration.md) ：実稼動システムから設定を書き出します。
1. 書き出したファイルを実稼動以外のコードベースにコピーします。
1. 静的ビューファイルのデプロイ： `bin/magento setup:static-content:deploy`

## 静的ビューファイル展開ツールのトラブルシューティング

[最初にコマースソフトウェアをインストールします](../../installation/overview.md);そうしないと、静的ビューファイル展開ツールを実行できません。

**症状**:静的ビューファイル配置ツールを実行すると、次のエラーが表示されます。

```terminal
ERROR: You need to install the Commerce application before running this utility.
```

**解決策**:

次の手順を実行します。

1. 次を使用して Commerce ソフトウェアをインストールします。 [コマンドライン](../../installation/composer.md).
1. アプリケーションサーバーに、またはとしてログインします。 [切り替え](../../installation/prerequisites/file-system/overview.md)：ファイルシステムの所有者。
1. のコンテンツを削除 `<app_root>/pub/static` ディレクトリ（を除く） `.htaccess` ファイル。 このファイルは削除しないでください。
1. 静的ビューファイルのデプロイ： `bin/magento setup:static-content:deploy`

## 静的コンテンツデプロイメントツールをカスタマイズする開発者向けヒント

静的コンテンツデプロイメントツールのカスタム実装を作成する場合は、クライアントで使用可能なファイルに対して、アトミックなファイル書き込みのみを使用します。 非アトミックファイル書き込みを使用する場合、これらのファイルは部分的なコンテンツを持つクライアントに読み込まれる可能性があります。

アトミックにするオプションの 1 つは、一時ディレクトリに格納されたファイルに書き込み、書き込みが終了した後に、それらをコピーしたり、クライアントに読み込む場所から宛先ディレクトリに移動したりすることです。 ファイルへの書き込みについて詳しくは、 [php fwrite](https://www.php.net/manual/en/function.fwrite.php).
