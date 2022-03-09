---
title: を実行します。 [!DNL Upgrade Compatibility Tool]
description: 次の手順に従って、 [!DNL Upgrade Compatibility Tool] をAdobe Commerceプロジェクトに追加します。
source-git-commit: bcb8fced43c5d9972291f15a5039dbbc2a692a59
workflow-type: tm+mt
source-wordcount: '1864'
ht-degree: 0%

---


# を実行します。 [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

この [!DNL Upgrade Compatibility Tool] は、Adobe Commerceカスタマイズ済みのインスタンスを、そのインスタンスにインストールされているすべてのモジュールを分析することで、特定のバージョンと照合するコマンドラインツールです。 最新バージョンのAdobe Commerceにアップグレードする前に対処する必要がある重要な問題、エラーおよび警告のリストを返します。

この [!DNL Upgrade Compatibility Tool] は、Adobe Commerceの新しいバージョンにアップグレードする前にコードで修正する必要がある潜在的な問題を特定します。

## 以下を使用： `upgrade:check` command

この `upgrade:check` コマンドは、ツールを実行するメインコマンドです。

```bash
bin/uct upgrade:check <dir>
```

>[!TIP]
>
>この `<dir>` 値は、Adobe Commerceインスタンスが配置されるディレクトリです。

この `upgrade:check` コマンドを実行 [!DNL Upgrade Compatibility Tool] およびは、Adobe Commerceにインストールされているすべてのモジュールを分析することで、カスタマイズされたインスタンスを特定のバージョンと照合します。 Adobe Commerceの最新バージョンにアップグレードする前に対処する必要がある、重要な問題、エラーおよび警告のリストを返します。

>[!WARNING]
>
>プロジェクトのルート（またはメイン）ディレクトリが指定されている場合にのみ実行します。

このコマンドは、その特定のAdobe Commerceインスタンスのコアコードの変更と、そのインスタンスにインストールされているすべてのカスタムコードの変更を確認します。

次を実行できます。 `core:code:changes` コマンドを使用して、特定のAdobe Commerceインスタンスのコアコードの変更のみを分析できます。 詳しくは、 [コアコードの変更点](../upgrade-compatibility-tool/run.md#use-the-core:code:changes-command) 」セクションに入力します。

一方、 `graphql:compare` コマンドを使用して、2 つの GraphQL スキーマを比較し、それら間で変更があるかどうかを確認できます。 詳しくは、 [GraphQL スキーマの互換性の検証](../upgrade-compatibility-tool/run.md#graphql-schema-compatibility-verification) 」セクションに入力します。

### Recommendations `upgrade:check` command

- この [!DNL Upgrade Compatibility Tool] を実行するには、2GB 以上の RAM が必要です。 この設定は、メモリ不足による問題を回避するために推奨されます。 この [!DNL Upgrade Compatibility Tool] を実行すると、質問が表示されます。 `upgrade:check` 低いコマンド `memory_limit` 設定。
- 次を指定： `-m` 特定のモジュールに対してツールを実行するオプション：

   ```bash
   bin/uct upgrade:check <dir> -m[=MODULE-PATH]
   ```

引数は次のようになります。

- `<dir>`:Adobe Commerceインストールディレクトリ。
- `[=MODULE-PATH]`:特定のモジュールパスディレクトリ。

### 以下を使用： `--help` オプション

次の手順で [!DNL Upgrade Compatibility Tool] コマンドの一般的なオプションとヘルプ：

```bash
bin/uct --help
```

ただし、 `--help` 特定のコマンドを実行する際のオプション ( `bin/uct upgrade:check`. これは特定の `--help` そのコマンドのオプション：

```bash
bin/uct upgrade:check --help
```

利用可能 `--help` オプション `upgrade:check` コマンド：

- `-m, --module-path[=MODULE-PATH]`:分析するモジュールのパス
- `-a, --current-version[=CURRENT-VERSION]`:省略した場合は、現在のAdobe CommerceバージョンのAdobe Commerceインストールのバージョンが使用されます。
- `-c, --coming-version[=COMING-VERSION]`:省略した場合は、Target Adobe CommerceバージョンのAdobe Commerceインストールが使用されます。
- `--json-output-path[=JSON-OUTPUT-PATH]`:出力を JSON 形式で書き出すファイルのパス。
- `--html-output-path[=HTML-OUTPUT-PATH]`:出力を書き出すファイルのパスをHTML形式で指定します。
- `--min-issue-level`:レポートに表示する最小問題レベル。 デフォルトはです。 [警告].
- `--ignore-current-version-compatibility-issues`:既知の重要な問題、エラーおよび警告を [!DNL Upgrade Compatibility Tool] レポート。
- `--context=CONTEXT`:実行コンテキスト。 このオプションは統合の目的で使用され、実行結果には影響しません。
- `-h, --help`:特定のコマンドのヘルプを表示します。 コマンドを指定しない場合、 `list` コマンドはデフォルトの結果です。
- `-q, --quiet`:コマンドの実行中にメッセージを出力しない。
- `-v, --version`:アプリケーションのバージョンを表示します。
- `--ansi, --no-ansi`:ANSI 出力を有効にします。
- `-n, --no-interaction`:コマンドの実行中にインタラクティブな質問をしないでください。
- `-v, --vv, --vvv, --verbose`:出力通信の詳細性を高めます。 1 は通常の出力、2 は詳細な出力、3 は DEBUG 出力です。

### 出力

分析を実行した結果、 [!DNL Upgrade Compatibility Tool] は、各ファイルの重大度、エラーコードおよびエラーの説明を指定した問題のリストを含むレポートをエクスポートします。

次の例を参照してください。

```terminal
File: /app/code/Custom/CatalogExtension/Controller/Index/Index.php
------------------------------------------------------------------
 * [WARNING][1131] Line 23: Extending from class 'Magento\Framework\App\Action\Action' that is @deprecated on version '2.4.2'
 * [ERROR][1429] Line 103: Call method 'Magento\Framework\Api\SearchCriteriaBuilder::addFilters' that is non API on version '2.4.2'
 * [CRITICAL][1110] Line 60: Instantiating class/interface 'Magento\Catalog\Model\ProductRepository' that does not exist on version '2.4.2'
```

次を確認します。 [エラーメッセージの参照](error-messages.md) トピックを参照してください。

また、このレポートには、次の内容を示す詳細な概要も含まれます。

- *現在のバージョン*:現在インストールされているバージョン。
- *ターゲットバージョン*:アップグレード先のバージョン。
- *実行時間*:分析がレポートの作成に要した時間 (mm:ss)。
- *更新が必要なモジュール*:互換性の問題があり、更新が必要なモジュールの割合。
- *更新が必要なファイル*:互換性の問題が含まれ、更新が必要なファイルの割合。
- *重大なエラーの合計*:検出された重大なエラーの数。
- *合計エラー数*:見つかったエラーの数。
- *合計警告数*:見つかった警告の数。

次の例を参照してください。

```terminal
 ----------------------------- ------------------
  Current version               2.4.2
  Target version                2.4.3
  Execution time                1m:10s
  Modules that require update   78.33% (47/60)
  Files that require update     21.62% (115/532)
  Total critical issues         35
  Total errors                  201
  Total warnings                103
 ----------------------------- ------------------
```

>[!NOTE]
>
>デフォルトでは、 [!DNL Upgrade Compatibility Tool] では、次の 2 つの異なる形式でレポートがエクスポートされます。 `json` および `html`.

#### JSON

JSON ファイルには、出力に表示される情報とまったく同じものが含まれます。

- 特定された問題のリスト。
- 分析の概要。

発生した問題ごとに、問題の重大度や説明などの詳細情報がレポートに表示されます。

>[!NOTE]
>
>出力フォルダーのデフォルトのパスは、 `var/output/[TIME]-results.json`.

このレポートを別の出力フォルダーにエクスポートするには、次のコマンドを実行します。

```bash
bin/uct upgrade:check <dir> --json-output-path[=JSON-OUTPUT-PATH]
```

引数は次のようになります。

- `<dir>`:Adobe Commerceインストールディレクトリ。
- `[=JSON-OUTPUT-PATH]`:書き出すパスディレクトリ `.json` 出力ファイル。

>[!NOTE]
>
>出力フォルダーのデフォルトのパスは、 `var/output/[TIME]-results.json`.

#### HTML

HTMLファイルには、特定された問題と分析の概要のリストも含まれています。 また、次の 4 つの異なるグラフが含まれます。

- **問題の重要度別のモジュール**:モジュール別の重大度の配分を表示します。
- **問題の重要度別のファイル**:ファイル別の重大度を表示します。
- **問題の総数別に並べられたモジュール**:警告、エラー、重大なエラーを考慮して、最も問題が発生した 10 個のモジュールを表示します。
- **相対的なサイズと問題を持つモジュール**:モジュールに含まれるファイルが多いほど、その円が大きくなります。 モジュールの問題が多いほど、その円が赤く表示されます。

これらのグラフでは、最も問題が発生したパーツや、アップグレードを実行するためにより多くの作業が必要なパーツを（一目で）特定できます。

![HTMLレポート — 概要](../../assets/upgrade-guide/uct-html-summary.png)

![HTMLレポート — 詳細](../../assets/upgrade-guide/uct-html-details.png)

このレポートを別の出力フォルダーにエクスポートするには、次の手順を実行します。

```bash
bin/uct upgrade:check <dir> --html-output-path[=HTML-OUTPUT-PATH]
```

引数は次のようになります。

- `<dir>`:{{site.data.var.ee}} のインストールディレクトリ。
- `[=HTML-OUTPUT-PATH]`:書き出すパスディレクトリ `.html` 出力ファイル。

>[!NOTE]
>
>出力フォルダーのデフォルトのパスは、 `var/output/[TIME]-results.html`.

### 以下を使用： `--ignore-current-version-compatibility-issues` オプション

この [!DNL Upgrade Compatibility Tool] を使用すると、 `upgrade:check` 命令 `--ignore-current-version-compatibility-issues` 」オプションを使用する場合は、新しい問題または不明な重要な問題、エラー、警告のみが表示されます。 既知の重要な問題、エラーおよび警告を [!DNL Upgrade Compatibility Tool] レポート。

```bash
bin/uct upgrade:check --ignore-current-version-compatibility-issues <dir>
```

>[!NOTE]
>
>これは、PHP API の検証にのみ適用されます。

### バニラインストール

A _バニラ_ インストールは、特定のリリースバージョンの指定したバージョンタグまたはブランチのクリーンインストールです。

この `bin/uct core:code:changes` コマンドは、システムに vanilla インスタンスが存在するかどうかを確認します。 バニラインストールを初めて使用する場合は、インタラクティブなコマンドラインの質問が表示され、 [Adobe Commerceリポジトリ](https://repo.magento.com/).

以下を実行すると、 [!DNL Upgrade Compatibility Tool] コマンドを `--vanilla-dir` Adobe Commerce vanilla インストールディレクトリを指定するオプション。

詳しくは、 [バニラインスタンスのデプロイ](https://devdocs.magento.com/contributor-guide/contributing.html#vanilla-pr) トピックを参照してください。

## 以下を使用： `list` command

リストを返すには [!DNL Upgrade Compatibility Tool] 使用可能なコマンド、次のコマンドを実行します。

```bash
bin/uct list
```

この `list` コマンドは、次の値を返します。

- `-h, --help`:特定のコマンドのヘルプを表示します。 コマンドを指定しない場合、 `list` コマンドはデフォルトの結果です。
- `-q, --quiet`:コマンドの実行中にメッセージを出力しない。
- `-v, --version`:アプリのバージョンを表示します。
- `--ansi, --no-ansi`:ANSI 出力を有効にします。
- `-n, --no-interaction`:コマンドの実行中にインタラクティブな質問をしないでください。
- `-v, --vv, --vvv, --verbose`:出力通信の詳細性を高めます。 1 は通常の出力、2 は詳細な出力、3 は DEBUG 出力です。

## 以下を使用： `core:code:changes` command

現在のAdobe Commerceのインストールをクリーンなバニラのインストールと比較して、新しい機能やカスタマイズの実装に対してコアコードに変更が加えられているかどうかを確認できます。 この検証は、変更に基づいて、アップグレードで必要とされる作業を見積もるのに役立ちます。

```bash
bin/uct core:code:changes <dir> <vanilla dir>
```

引数は次のようになります。

- `<dir>`:Adobe Commerceインストールディレクトリ。
- `<vanilla dir>`:Adobe Commerce vanilla インストールディレクトリ。

このコマンドを実行する際には、いくつかの制限があります。

- プロジェクトのルート（またはメイン）ディレクトリが指定されている場合にのみ実行します。
- コアの変更のリストのみを表示します。

### 以下を使用： `core:code:changes` コマンドを `--help` オプション

利用可能 `--help` オプション `core:code:changes` コマンド：

- `-h, --help`:特定のコマンドのヘルプを表示します。 コマンドを指定しない場合、 `list` コマンドはデフォルトの結果です。
- `-q, --quiet`:コマンドの実行中にメッセージを出力しない。
- `-v, --version`:アプリのバージョンを表示します。
- `--ansi, --no-ansi`:ANSI 出力を有効にします。
- `-n, --no-interaction`:コマンドの実行中にインタラクティブな質問をしないでください。
- `-v, --vv, --vvv, --verbose`:出力通信の詳細性を高めます。 1 は通常の出力、2 は詳細な出力、3 は DEBUG 出力です。

## バージョン

現在のAdobe CommerceのインストールをAdobe Commerceのバージョンと比較できます `>=2.3`.

コマンドを実行する際は、バージョンをパラメーターとして指定する必要があります。

```bash
bin/uct upgrade:check <dir> -c 2.4.3
```

ここで、

- `-c, --coming-version[=COMING-VERSION]`:Adobe Commerceのターゲットバージョン。

前のコマンドを実行する際には、いくつかの制限があります。

- このパラメーターは、Adobe Commerceの特定のバージョンを識別する任意のタグを参照します。
- これを明示的に指定する必要があります。この値のみを指定しても、機能しません。
- 引用符を付けずにタグバージョンを指定します（一重引用符も二重引用符も付けません）。 ~~&#39;2.4.1-develop&#39;~~.
- 現在インストールしているバージョンより古いバージョンを提供したり、現在サポートされている最も古いバージョンである 2.3 より古いバージョンを提供したりしないでください。

### 以下を使用： `refactor` command

この [!DNL Upgrade Compatibility Tool] には、以下の一連の問題を自動的に修正する機能があります。

- 引数を渡さずに使用できた関数ですが、このような使用方法では廃止されました。
- の使用方法 `$this` Magento
- PHP キーワードの使用 `final` 非公開メソッドで使用できます。

実行：

```bash
bin/uct refactor <dir>
```

## GraphQL スキーマの互換性の検証

この [!DNL Upgrade Compatibility Tool] また、2 つの GraphQL エンドポイントを紹介し、それらのエンドポイント間で重大な変更や危険な変更を探してスキーマを比較するオプションも提供されています。

```bash
bin/uct graphql:compare <schema1> <schema2>
```

引数は次のようになります。

- `<schema1>`:既存のインストールのエンドポイント URL。
- `<schema2>`:バニラインストールのエンドポイント URL。

次を実行している必要があります： `instance before` および `instance after` アップグレード。

### GraphQL 比較コマンド `--help` options

利用可能 `--help` オプション `graphql:compare` コマンド：

- `-h, --help`:特定のコマンドのヘルプを表示します。 コマンドを指定しない場合、 `list` コマンドはデフォルトの結果です。
- `-q, --quiet`:コマンドの実行中にメッセージを出力しない。
- `-v, --version`:アプリのバージョンを表示します。
- `--ansi, --no-ansi`:ANSI 出力を有効にします。
- `-n, --no-interaction`:コマンドの実行中にインタラクティブな質問をしないでください。
- `-v, --vv, --vvv, --verbose`:出力通信の詳細性を高めます。 1 は通常の出力、2 は詳細な出力、3 は DEBUG 出力です。

### GraphQL の重要な問題、エラー、警告のリストを示す例

```terminal
 *   [WARNING] FIELD_CHANGED_KIND: ConfigurableProduct.gender changed type from Int to String.
 *   [WARNING] OPTIONAL_INPUT_FIELD_ADDED: An optional field sku on input type ProductAttributeSortInput was added.
```

詳しくは、 [開発者情報](../upgrade-compatibility-tool/developer.md) を参照してください。

次を実行できます。 [!DNL Upgrade Compatibility Tool] PhpStorm プラグインを介した run 設定を含む 詳しくは、 [[!DNL Upgrade Compatibility Tool] 設定を実行](https://devdocs.magento.com/guides/v2.3/ext-best-practices/phpstorm/uct-run-configuration.html) トピックを参照してください。

## 推奨されるアクション

### 結果の最適化

この [!DNL Upgrade Compatibility Tool] は、結果と、デフォルトでプロジェクトで特定されたすべての問題を含むレポートを提供します。 結果を最適化して、アップグレードを完了するために修正する必要がある問題に焦点を当てることができます。

- オプションを使用 `--ignore-current-version-compatibility-issues`：現在のAdobe Commerceバージョンに対する既知の重要な問題、エラーおよび警告をすべて抑制します。 アップグレード先のバージョンに対してのみエラーが発生します。
- を `--min-issue-level` オプションを選択すると、最小の問題レベルを設定して、アップグレードに関する最も重要な問題のみを優先するのに役立ちます。 特定のベンダー、モジュール、またはディレクトリのみを分析する場合は、パスをオプションとして指定することもできます。
- を実行します。 `bin` コマンドと追加オプション `-m`. これにより、 [!DNL Upgrade Compatibility Tool] 特定のモジュールを個別に分析し、 [!DNL Upgrade Compatibility Tool].

### Adobe Commerceのベストプラクティスに従う

- 同じ名前の 2 つのモジュールを使用しないでください。
- フォローAdobe Commerce [コーディング規格](https://devdocs.magento.com/guides/v2.4/coding-standards/bk-coding-standards.html).

## トラブルシューティング

### セグメント化障害エラー

2 つのモジュールが同じ名前を持つ場合、 [!DNL Upgrade Compatibility Tool] セグメント化障害エラーを示します。

このエラーを回避するには、 `bin` コマンドと追加オプション `-m`:

```bash
bin/uct upgrade:check /<dir>/<instance-name> --coming-version=2.4.1 -m /vendor/<vendor-name>/<module-name>
```

>[!NOTE]
>
>この `<dir>` 値は、Adobe Commerceインスタンスが配置されるディレクトリです。

この `-m` オプションを使用すると、 [!DNL Upgrade Compatibility Tool] Adobe Commerceインスタンス内で同じ名前の 2 つのモジュールが発生するのを防ぐために、特定の各モジュールを個別に分析する。

このコマンドオプションを使用すると、 [!DNL Upgrade Compatibility Tool] 複数のモジュールを含むフォルダーを分析するには：

```bash
bin/uct upgrade:check /<dir>/<instance-name> --coming-version=2.4.1 -m /vendor/<vendor-name>/
```

この推奨事項は、 [!DNL Upgrade Compatibility Tool].

### 空の出力

>[!NOTE]
>
>この `M2_VERSION` は、Adobe Commerceインスタンスと比較する対象となるAdobe Commerceバージョンです。

次のコマンドを実行した後の場合：

```bash
bin/uct upgrade:check INSTALLATION_DIR -c M2_VERSION
```

出力は次のみです。 `Upgrade compatibility tool`:

```terminal
bin/uct upgrade:check /var/www/project/magento/ -c 2.4.1
Upgrade compatibility tool
```

考えられる原因は、PHP のメモリ制限です。
次の設定でメモリ制限を上書き `memory_limit` から `-1`:

```bash
php -d memory_limit=-1 /bin/uct upgrade:check INSTALLATION_DIR -c M2_VERSION
```
