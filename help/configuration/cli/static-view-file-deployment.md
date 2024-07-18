---
title: 静的表示ファイルのデプロイ
description: 実稼動モード中に静的ファイルをCommerce ファイルシステムに書き込む方法を説明します。
exl-id: 51954738-b999-4982-954b-70f7a70c5a17
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '1124'
ht-degree: 0%

---

# 静的表示ファイルのデプロイ

{{file-system-owner}}

static view files deployment コマンドを使用すると、Commerce ソフトウェアが [ 実稼動モード ](../bootstrap/application-modes.md#production-mode) に設定されている場合に、Commerce ファイルシステムに静的ファイルを書き込むことができます。

_静的ビューファイル_ という用語は、以下を指します。

- 「静的」とは、サイトに対してキャッシュできることを意味します（つまり、ファイルは動的に生成されません）。 例としては、LESS から生成された画像や CSS があります。
- 「View」はプレゼンテーションレイヤー（MVC から）を指します。

静的ビューファイルは `<magento_root>/pub/static` ディレクトリにあり、一部は `<magento_root>/var/view_preprocessed` ディレクトリにもキャッシュされます。

静的ビューファイルのデプロイメントは、次のようなアプリケーションモードの影響を受けます。

- [ デフォルト ](../bootstrap/application-modes.md#default-mode) および [ 開発者 ](../bootstrap/application-modes.md#developer-mode) モード：Commerceはオンデマンドでそれらを生成しますが、残りはアクセス速度を向上させるためにファイルにキャッシュされます。
- [ 実稼動 ](../bootstrap/application-modes.md#production-mode) モード：静的ファイルは生成 _れ_ キャッシュされません。

このトピックで説明したコマンドを使用して、静的ビューファイルをCommerce ファイルシステムに手動で書き込む必要があります。その後、脆弱性を制限し、誤ってファイルを上書きしたり悪意のあるファイルを上書きしたりしないように、アクセス許可を制限できます。

>[!WARNING]
>
>_開発者モードのみ_：新しいモジュールをインストールまたは有効にすると、新しいJavaScript、CSS、レイアウトなどが読み込まれる場合があります。 静的ファイルの問題を回避するには、新しいモジュールのすべての変更を確実に取得するために、古いファイルを消去する必要があります。 生成された静的ビューファイルは、いくつかの方法でクリーンアップできます。 詳しくは、[ 静的ファイルのキャッシュのクリーンアップに関するトピック ](https://developer.adobe.com/commerce/frontend-core/guide/caching/#clean-static-files-cache) を参照してください。

**静的表示ファイルをデプロイするには**:

1. Commerce サーバーにとしてログインするか、[ ファイルシステムのオーナーに切り替え ](../../installation/prerequisites/file-system/overview.md) ます。
1. `.htaccess` ファイルを除く `<magento_root>/pub/static` のコンテンツを削除します。 このファイルは削除しないでください。
1. 静的表示ファイル展開ツール `<magento_root>/bin/magento setup:static-content:deploy` を実行します。

   >[!INFO]
   >
   >管理者で静的ビューファイルの結合を有効にした場合、`pub/static` ディレクトリシステムは書き込み可能である必要があります。

   コマンドオプション：

   ```bash
   bin/magento setup:static-content:deploy [<languages>] [-t|--theme[="<theme>"]] [--exclude-theme[="<theme>"]] [-l|--language[="<language>"]] [--exclude-language[="<language>"]] [-a|--area[="<area>"]] [--exclude-area[="<area>"]] [-j|--jobs[="<number>"]]  [--no-javascript] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [--no-parent] [-f|--force]
   ```

次の表に、このコマンドのパラメータと値を示します。

| オプション | 説明 | 必須？ |
| ------ | ----------- | --------- |
| `<languages>` | 静的ビューファイルを出力する [ISO-639](https://www.loc.gov/standards/iso639-2/php/code_list.php) 言語コードのスペース区切りリスト。 （デフォルトは `en_US`）。<br> 次のコマンドを実行してリストを検索します：`bin/magento info:language:list` | 不可 |
| `--language (-l)` | 指定した言語のみのファイルを生成します。 オプションを指定しないデフォルトでは、すべての ISO-639 言語コードのファイルが生成されます。 一度に 1 つの言語コードの名前を指定できます。 デフォルト値は **all** です。<br> 例：`--language en_US --language es_ES` | 不可 |
| `--exclude-language` | 指定した言語コードのファイルを生成します。 オプションを指定しない場合のデフォルトでは、何も除外されません。 1 つの言語コードの名前を指定するか、言語コードのコンマ区切りリストを指定できます。 デフォルト値は **なし** です。 | 不可 |
| `--theme <theme>` | 静的コンテンツをデプロイするテーマ。 デフォルト値は **all** です。<br> 例：`--theme Magento/blank --theme Magento/luma` | 不可 |
| `--exclude-theme <theme>` | 静的コンテンツのデプロイ時に除外するテーマ。 デフォルト値は **なし** です。<br> 例：`--exclude-theme Magento/blank` | 不可 |
| `--area (-a)` | 指定した領域のファイルのみを生成します。 オプションを指定しないデフォルトでは、すべての領域のファイルが生成されます。 有効な値は `adminhtml` および `frontend` です。 デフォルト値は **all** です。<br> 例：`--area adminhtml` | 不可 |
| `--exclude-area` | 指定した領域のファイルを生成しません。 オプションを指定しない場合のデフォルトでは、何も除外されません。 デフォルト値は **なし** です。 | 不可 |
| `--jobs (-j)` | 指定したジョブ数を使用して [ 並列処理 ](manage-indexers.md#reindexing-in-parallel-mode) を有効にします。 デフォルトは 0 です（並列プロセスでは実行しません）。 既定値は **0** です。 | 不可 |
| `--symlink-locale` | これらのロケールのファイルにシンボリックリンクを作成します。これはデプロイメントに渡されますが、カスタマイズは行われません。 | 不可 |
| `--content-version=CONTENT-VERSION` | 複数のノードでデプロイメントを実行する場合は、静的コンテンツのカスタムバージョンを使用して、静的コンテンツのバージョンが同じでキャッシュが正しく機能することを確認できます。 | 不可 |
| `--no-javascript` | JavaScript ファイルをデプロイしない | 不可 |
| `--no-css` | CSS ファイルをデプロイしないでください。 | 不可 |
| `--no-less` | LESS ファイルをデプロイしないでください。 | 不可 |
| `--no-images` | 画像をデプロイしないでください。 | 不可 |
| `--no-fonts` | フォントファイルをデプロイしないでください。 | 不可 |
| `--no-html` | HTMLファイルをデプロイしないでください。 | 不可 |
| `--no-misc` | MD、JBF、CSV、JSON、TXT、HTC、SWFなどの他のタイプのファイルはデプロイしないでください | 不可 |
| `--no-html-minify` | HTMLファイルは縮小しないでください。 | 不可 |
| `-s <quick\|standard\|compact>` | デプロイメント戦略を定義します。 これらのオプションは、複数のローカルがある場合にのみ使用します。<ul><li>[ クイック戦略 ](static-view-file-strategy.md#quick-strategy) を使用すると、デプロイメント時間を最小限に抑えることができます。 指定されていない場合、これはデフォルトのコマンドオプションです。</li><li>[ 標準方法 ](static-view-file-strategy.md#standard-strategy) を使用して、すべてのパッケージのすべての静的ビューファイルをデプロイします。</li><li>[ コンパクト化 ](static-view-file-strategy.md#compact-strategy) を使用して、サーバー上のディスク領域を節約します。</li></ul> | 不可 |
| `--no-parent` | 現在のテーマの親テーマ用のファイルを生成しません。 デプロイしようとしている現在のテーマの親テーマを明示的に使用しない場合は、このフラグを使用することを強くお勧めします。 これにより、プロセスの速度が大幅に向上します。 このフラグは、Commerce 2.4.2 で使用できます。 | 不可 |
| `--force (-f)` | 任意のモードでファイルをデプロイします。 （デフォルトでは、静的コンテンツデプロイメントツールは、実稼動モードでのみ実行できます。 このオプションを使用して、デフォルトまたは開発者モードで実行します。 | 不可 |

>[!INFO]
>
>`<languages>` と `--language` の両方の値を指定した場合は、`<languages>` が優先されます。

## 例

次に、コマンドの例をいくつか示します。

### テーマとHTMLの縮小の除外

次のコマンドは、米国英語（`en_US`）言語用の静的コンテンツをデプロイし、Commerceで提供される Luma テーマを除外し、HTMLファイルを縮小しません。

```bash
bin/magento setup:static-content:deploy en_US --exclude-theme Magento/luma --no-html-minify
```

サンプル出力：

```
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

次のコマンドは、標準のデプロイメント戦略で、4 つのジョブを含むJavaScriptのみをデプロイします。

```bash
bin/magento setup:static-content:deploy -s standard --no-misc --no-html --no-fonts --no-images --no-less --no-css -j 4
```

次のコマンドは、3 つのジョブとクイックデプロイメント戦略を使用して、CSS と LESS のみをデプロイします。

```bash
bin/magento setup:static-content:deploy -s quick --no-misc --no-html --no-fonts --no-images --no-javascript -j 3
```

### 1 つのテーマと 1 つの領域に対する静的ビューファイルの生成

次のコマンドは、フォントを生成せずに、すべての言語、フロントエンド領域のみ、Commerce Luma テーマのみの静的ビューファイルを生成します。

```bash
bin/magento setup:static-content:deploy --area frontend --no-fonts --theme Magento/luma
```

サンプル出力：

```
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

## Commerceをインストールせずに静的ビューファイルをデプロイする

機密性の高い実稼働マシンでのビルドプロセスを回避するために、デプロイメントプロセスを実稼動以外の別の環境で実行する場合があります。

これを行うには、次の手順を実行します。

1. [`bin/magento app:config:dump`](../cli/export-configuration.md) を実行して、実稼動システムから設定をエクスポートします。
1. 書き出したファイルを実稼動以外のコードベースにコピーします。
1. 静的表示ファイルのデプロイ：`bin/magento setup:static-content:deploy`

## 静的表示ファイル展開ツールのトラブルシューティング

[ 最初にCommerce ソフトウェアをインストールします ](../../installation/overview.md)。インストールしないと、静的ビューファイルのデプロイメントツールを実行できません。

**症状**：静的ビューファイル展開ツールを実行すると、次のエラーが表示されます：

```
ERROR: You need to install the Commerce application before running this utility.
```

**解決策**:

次の手順を使用します。

1. [ コマンドライン ](../../installation/composer.md) を使用してCommerce ソフトウェアをインストールします。
1. ファイルシステムの所有者として、または [ 切り替え先 ](../../installation/prerequisites/file-system/overview.md) としてアプリケーションサーバーにログインします。
1. `.htaccess` ファイルを除く `<app_root>/pub/static` ディレクトリのコンテンツを削除します。 このファイルは削除しないでください。
1. 静的表示ファイルのデプロイ：`bin/magento setup:static-content:deploy`

## 静的コンテンツ展開ツールをカスタマイズする開発者向けのヒント

静的コンテンツ展開ツールのカスタム実装を作成する場合は、クライアントで使用可能にするファイルに対してのみアトミックファイル書き込みを使用します。 非アトミック ファイル書き込みを使用する場合、これらのファイルは、部分的なコンテンツを含むクライアントに読み込まれる可能性があります。

アトミックにするためのオプションの 1 つは、一時ディレクトリに格納されたファイルに書き込み、書き込みが終了した後に（ファイルがクライアントに読み込まれた場所から）宛先ディレクトリにコピーまたは移動することです。 ファイルへの書き込みについて詳しくは、[php fwrite](https://www.php.net/manual/en/function.fwrite.php) を参照してください。
