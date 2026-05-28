---
title: 静的ビューファイルのデプロイ
description: 静的ビューファイルを実稼動モードでAdobe Commerce ファイルシステムにデプロイする方法について説明します。 デプロイメントコマンドと最適化手法の詳細。
exl-id: 51954738-b999-4982-954b-70f7a70c5a17
source-git-commit: 319f3232d1ba5f5ed7cdd10ce85b9d7ffbeec89a
workflow-type: tm+mt
source-wordcount: '1157'
ht-degree: 0%

---

# 静的ビューファイルのデプロイ

{{file-system-owner}}

静的ビューファイルのデプロイメントコマンドを使用すると、Commerce ソフトウェアが[実稼動モード ](../bootstrap/application-modes.md#production-mode)に設定されている場合に、静的ファイルをCommerce ファイルシステムに書き込むことができます。

_静的ビューファイル_&#x200B;という用語は、次のことを指します。

- 「静的」とは、サイトに対してキャッシュできることを意味します（つまり、ファイルは動的に生成されません）。 例としては、LESSから生成された画像やCSSが含まれます。
- 「ビュー」とは、プレゼンテーション層（MVCから）を指します。

静的ビューファイルは`<magento_root>/pub/static` ディレクトリにあり、一部は`<magento_root>/var/view_preprocessed` ディレクトリにもキャッシュされています。

静的ビューファイルのデプロイメントは、次のようなアプリケーションモードの影響を受けます。

- [Default](../bootstrap/application-modes.md#default-mode)および[developer](../bootstrap/application-modes.md#developer-mode) モード：Commerceはオンデマンドで生成しますが、残りはアクセス速度のためにファイルにキャッシュされます。
- [実稼動](../bootstrap/application-modes.md#production-mode) モード：静的ファイルは&#x200B;_ではなく_&#x200B;生成またはキャッシュされます。

このトピックで説明するコマンドを使用して、静的ビューファイルをCommerce ファイルシステムに手動で書き込む必要があります。その後、権限を制限して脆弱性を制限し、ファイルの誤った上書きや悪意のある上書きを防ぐことができます。

>[!WARNING]
>
>_開発者モードのみ_：新しいモジュールをインストールまたは有効にすると、新しいJavaScript、CSS、レイアウトなどが読み込まれる場合があります。 静的ファイルの問題を回避するには、古いファイルを削除して、新しいモジュールのすべての変更を確実に取得する必要があります。 生成された静的ビューファイルは、いくつかの方法でクリーニングできます。 詳しくは、[静的ファイルのキャッシュのクリーンに関するトピック ](https://developer.adobe.com/commerce/frontend-core/guide/caching#clean-static-files-cache)を参照してください。

**静的ビューファイルをデプロイするには**:

1. としてCommerce サーバーにログインするか、[ ファイルシステムオーナー](../../installation/prerequisites/file-system/overview.md)に切り替えます。
1. `.htaccess` ファイルを除き、`<magento_root>/pub/static`の内容を削除します。 このファイルは削除しないでください。
1. 静的ビューファイル展開ツール `<magento_root>/bin/magento setup:static-content:deploy`を実行します。

   >[!INFO]
   >
   >管理画面で静的ビューファイルの結合を有効にする場合、`pub/static` ディレクトリシステムは書き込み可能である必要があります。

   コマンドオプション：

   ```shell
   bin/magento setup:static-content:deploy [<languages>] [-t|--theme[="<theme>"]] [--exclude-theme[="<theme>"]] [-l|--language[="<language>"]] [--exclude-language[="<language>"]] [-a|--area[="<area>"]] [--exclude-area[="<area>"]] [-j|--jobs[="<number>"]]  [--no-javascript] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [--no-parent] [-f|--force]
   ```

次の表に、このコマンドのパラメーターと値を示します。

| オプション | 説明 | 必要ですか？ |
| ------ | ----------- | --------- |
| `<languages>` | 静的ビューファイルを出力する[ISO-639](https://www.loc.gov/standards/iso639-2/php/code_list.php)言語コードのスペース区切りリスト。 （デフォルトは`en_US`） <br>次のコマンドを実行してリストを検索します：`bin/magento info:language:list` | いいえ |
| `--language (-l)` | 指定した言語のファイルのみを生成します。 オプションを指定しないデフォルトでは、すべてのISO-639言語コードのファイルを生成します。 一度に1つの言語コードの名前を指定できます。 デフォルト値は&#x200B;**all**&#x200B;です。<br>例：`--language en_US --language es_ES` | いいえ |
| `--exclude-language` | 指定した言語コードのファイルを生成します。 デフォルトでは、オプションが指定されていないため、何も除外しません。 1つの言語コードの名前または言語コードのコンマ区切りリストを指定できます。 デフォルト値は&#x200B;**none**&#x200B;です。 | いいえ |
| `--theme <theme>` | 静的コンテンツをデプロイするテーマ。 デフォルト値は&#x200B;**all**&#x200B;です。<br>例：`--theme Magento/blank --theme Magento/luma` | いいえ |
| `--exclude-theme <theme>` | 静的コンテンツをデプロイする際に除外するテーマ。 デフォルト値は&#x200B;**none**&#x200B;です。<br>例：`--exclude-theme Magento/blank` | いいえ |
| `--area (-a)` | 指定した領域のファイルのみを生成します。 デフォルトでは、オプションを指定せずに、すべての領域のファイルを生成します。 有効な値は`adminhtml`と`frontend`です。 デフォルト値は&#x200B;**all**&#x200B;です。<br>例：`--area adminhtml` | いいえ |
| `--exclude-area` | 指定した領域のファイルは生成しないでください。 デフォルトでは、オプションが指定されていないため、何も除外しません。 デフォルト値は&#x200B;**none**&#x200B;です。 | いいえ |
| `--jobs (-j)` | 指定されたジョブ数を使用して[並列処理](manage-indexers.md#reindexing-in-parallel-mode)を有効にします。 デフォルトは0です（並行プロセスでは実行しないでください）。 デフォルト値は&#x200B;**0**&#x200B;です。 | いいえ |
| `--symlink-locale` | これらのロケールのファイルのシンボリックリンクを作成します。このロケールはデプロイメント用に渡されますが、カスタマイズはありません。 | いいえ |
| `--content-version=CONTENT-VERSION` | 複数のノードでデプロイメントを実行して、静的コンテンツバージョンが同じで、キャッシュが適切に動作することを確認する場合は、静的コンテンツのカスタムバージョンを使用できます。 | いいえ |
| `--no-javascript` | JavaScript ファイルをデプロイしない | いいえ |
| `--no-css` | CSS ファイルはデプロイしないでください。 | いいえ |
| `--no-less` | LESS ファイルはデプロイしないでください。 | いいえ |
| `--no-images` | 画像はデプロイしないでください。 | いいえ |
| `--no-fonts` | フォントファイルはデプロイしないでください。 | いいえ |
| `--no-html` | HTML ファイルはデプロイしないでください。 | いいえ |
| `--no-misc` | 他の種類のファイルはデプロイしないでください：MD、JBF、CSV、JSON、TXT、HTC、SWF | いいえ |
| `--no-html-minify` | HTML ファイルを縮小しないでください。 | いいえ |
| `-s <quick\|standard\|compact>` | デプロイメント戦略の策定： これらのオプションは、複数のローカル環境がある場合にのみ使用します。<ul><li>[ クイック戦略](static-view-file-strategy.md#quick-strategy)を使用して、デプロイメント時間を最小限に抑えます。 これは、指定されていない場合のデフォルトのコマンドオプションです。</li><li>すべてのパッケージのすべての静的ビューファイルをデプロイするには、[標準戦略](static-view-file-strategy.md#standard-strategy)を使用します。</li><li>サーバー上のディスク領域を節約するには、[ コンパクト戦略](static-view-file-strategy.md#compact-strategy)を使用します。</li></ul> | いいえ |
| `--no-parent` | 現在のテーマの親テーマのファイルは生成しないでください。 デプロイしようとしている現在のテーマの親テーマを明示的に使用しない場合は、このフラグを使用することを強くお勧めします。 これにより、プロセスの速度が大幅に向上します。 このフラグは、Commerce 2.4.2で使用できます | いいえ |
| `--force (-f)` | 任意のモードでファイルをデプロイします。 （デフォルトでは、静的コンテンツデプロイメントツールは実稼動モードでのみ実行できます。 デフォルトまたは開発者モードで実行する場合は、このオプションを使用します）。 | いいえ |

>[!INFO]
>
>`<languages>`と`--language`の両方の値を指定した場合、`<languages>`が優先されます。

## 例

次に、いくつかのコマンドの例を示します。

### テーマの除外とHTMLの縮小

次のコマンドは、米国英語（`en_US`）言語の静的コンテンツをデプロイし、Commerceで提供されるLuma テーマを除外し、HTML ファイルを縮小しません。

```shell
bin/magento setup:static-content:deploy en_US --exclude-theme Magento/luma --no-html-minify
```

出力サンプル：

```text
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

次のコマンドは、標準のデプロイメント戦略を使用して、4つのジョブを含むJavaScriptのみをデプロイします。

```shell
bin/magento setup:static-content:deploy -s standard --no-misc --no-html --no-fonts --no-images --no-less --no-css -j 4
```

次のコマンドは、3つのジョブとクイックデプロイメント戦略でCSSとLESSのみをデプロイします。

```shell
bin/magento setup:static-content:deploy -s quick --no-misc --no-html --no-fonts --no-images --no-javascript -j 3
```

### 1つのテーマと1つの領域の静的ビューファイルの生成

次のコマンドは、すべての言語の静的ビューファイル（フロントエンド領域のみ、Commerce Luma テーマのみ）を生成します。フォントは生成されません。

```shell
bin/magento setup:static-content:deploy --area frontend --no-fonts --theme Magento/luma
```

出力サンプル：

```text
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

機密性の高い実稼動マシン上のビルドプロセスを回避するために、デプロイメントプロセスを実稼動以外の個別の環境で実行する場合があります。

これを行うには、次の手順を実行します。

1. 実稼動システムから設定をエクスポートするには、[`bin/magento app:config:dump`](../cli/export-configuration.md)を実行します。
1. 書き出されたファイルを実稼動以外のコードベースにコピーします。
1. 静的ビューファイルをデプロイ：`bin/magento setup:static-content:deploy`

## 静的表示ファイルのデプロイメントツールのトラブルシューティング

[Commerce ソフトウェアを最初にインストールします](../../installation/overview.md)。インストールしない場合は、静的ビューファイルのデプロイメントツールを実行できません。

**現象**：静的ビューファイルのデプロイメントツールを実行すると、次のエラーが表示されます。

```text
ERROR: You need to install the Commerce application before running this utility.
```

**解決策**:

次の手順を使用します。

1. [ コマンドライン ](../../installation/composer.md)を使用してCommerce ソフトウェアをインストールします。
1. アプリケーションサーバーにファイルシステム所有者としてログインするか、[ ファイル所有者として](../../installation/prerequisites/file-system/overview.md)に切り替えます。
1. `.htaccess` ファイルを除く`<app_root>/pub/static` ディレクトリの内容を削除します。 このファイルは削除しないでください。
1. 静的ビューファイルをデプロイ：`bin/magento setup:static-content:deploy`

## 静的コンテンツ展開ツールをカスタマイズする開発者向けのヒント

静的コンテンツデプロイメントツールのカスタム実装を作成する場合は、クライアントで使用可能なファイルに対するアトミックファイルの書き込みのみを使用します。 非アトミックファイルの書き込みを使用する場合、それらのファイルは部分的なコンテンツを持つクライアントに読み込まれる可能性があります。

これをアトミック化するオプションの1つは、一時ディレクトリに保存されているファイルに書き込み、書き込みが終わった後に、それらをコピーしたり、宛先ディレクトリ（クライアントに読み込まれる場所）に移動したりすることです。 ファイルへの書き込みについて詳しくは、[php fwrite](https://www.php.net/manual/en/function.fwrite.php)を参照してください。
