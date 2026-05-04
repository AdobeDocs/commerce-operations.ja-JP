---
title: ' [!DNL Upgrade Compatibility Tool]を実行'
description: Adobe Commerce プロジェクトのコマンドラインインターフェイスで [!DNL Upgrade Compatibility Tool] を実行するには、次の手順に従います。
exl-id: ea467a74-18eb-476b-96e2-23f4fc257d73
source-git-commit: f9a135fc63574ccbecd3f564a87fc5c4ac03f009
workflow-type: tm+mt
source-wordcount: '1164'
ht-degree: 0%

---

# [!DNL Upgrade Compatibility Tool]をダウンロード

{{commerce-only}}

コマンドライン インターフェイスで[!DNL Upgrade Compatibility Tool]を使用するには、次のコマンドを実行してダウンロードします。

```shell
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

ツールに実行可能な権限を`chmod` コマンドで付与する必要がある場合があります。

```shell
chmod +x ./uct/bin/uct
```

## コマンドライン インターフェイスの[!DNL Upgrade Compatibility Tool]

[!DNL Upgrade Compatibility Tool]は、Adobe Commerce カスタマイズされたインスタンスにインストールされているすべてのモジュールを分析して、特定のバージョンと比較するツールです。 最新バージョンのAdobe Commerceにアップグレードする前に対処する必要がある重大な問題、エラー、警告のリストが返されます。

[!DNL Upgrade Compatibility Tool]の詳細については、この[&#x200B; ビデオチュートリアル &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-learn/tutorials/extensibility/backend-development/upgrade/upgrade-compatibility-tool-overview) （06:02）を参照してください。

コマンドラインインターフェイスで[!DNL Upgrade Compatibility Tool]に使用できるコマンド：

| **コマンド** | **説明** |
|----------------|-----------------|
| `upgrade:check` | このコマンドは、インストールされているすべてのモジュールを分析して[!DNL Upgrade Compatibility Tool]を実行します。 |
| `dbschema:diff` | このコマンドは、指定された2つのAdobe Commerce バージョン間のデータベース スキーマのすべての違いを表示します。 |
| `core:code:changes` | このコマンドは、現在のAdobe Commerce インストールとクリーンなVanilla インストールを比較します。 |
| `refactor` | このコマンドは、減らされた問題セットを自動的に修正します。 |
| `graphql:compare` | このコマンドは、2つのGraphQL エンドポイントをイントロスペクトし、それらのスキーマを比較するオプションを提供します。 |
| `list` | このコマンドは、使用可能なすべての[!DNL Upgrade Compatibility Tool] コマンドのリストを返します。 |
| `help` | このコマンドは、[!DNL Upgrade Compatibility Tool]で使用可能なすべての`help` オプションを返します。 このコマンドは、以前のコマンドを使用したオプションと同様に実行できます。 |

## `upgrade:check` コマンドの使用

`upgrade:check` コマンドは、特定のAdobe Commerce インスタンスのコアコードの変更と、そのインスタンスにインストールされているすべてのカスタムコードの変更を確認します。

`upgrade:check` コマンドは、ツールを実行する主なコマンドです。

```shell
bin/uct upgrade:check <dir>
```

ここで、`<dir>`値は、Adobe Commerce インスタンスが配置されているディレクトリです。

`upgrade:check` コマンドで使用できるオプション：

| **コマンド** | **使用可能なオプション** |
|----------------|-----------------|
| `upgrade:check` | <ul><li>—help：使用可能なすべてのオプションを返します。</li><li>—current-version：現在のAdobe Commerce バージョン。 省略した場合は、Adobe Commerce インストールのバージョンが使用されます。</li><li>—min-issue-level：最小イシューレベルに応じてイシューをフィルタリングできます（デフォルト値はWARNING）。</li><li>—ignore-current-version-compatibility-issues （または – i）: レポートに現在のバージョンの重大な問題、エラー、警告を含めたくない場合。</li><li>—coming-version （または – c）：特定のAdobe Commerce バージョンをターゲットにします。 省略した場合は、使用可能な最新の値が使用されます。</li></ul> |

[!DNL Upgrade Compatibility Tool]では、`--ignore-current-version-compatibility-issues` オプションを指定して`upgrade:check` コマンドを実行できます。 このオプションは、現在のバージョンから[!DNL Upgrade Compatibility Tool] レポートの対象バージョンへの更新で導入された新しい問題のみを取得する場合に使用します。

```shell
bin/uct upgrade:check --ignore-current-version-compatibility-issues <dir>
```

>[!NOTE]
>
> これは、PHP API検証にのみ適用されます。

### `--coming-version` オプションの追加

`--coming-version` オプションを使用すると、現在のAdobe Commerce インストールを任意のAdobe Commerce バージョン `>=2.3`と比較できます。

`upgrade:check` コマンドを実行する場合は、バージョンをパラメーターとして指定する必要があります。

```shell
bin/uct upgrade:check <dir> -c 2.4.3
```

ここで、`-c, --coming-version[=COMING-VERSION]`はAdobe Commerce ターゲットバージョンを指します。

`--coming-version`の実行時にはいくつかの制限があります。

- このパラメーターは、Adobe Commerceの特定のバージョンを識別する任意のタグを参照します。
- これを明示的に指定する必要があります。その値のみを指定すると機能しません。
- 引用符なしでタグバージョンを指定します（シングルもダブルもありません）: ~~&#39;2.4.1-develop&#39;~~。
- 現在インストールされているバージョンよりも古いバージョンや、現時点でサポートされている最も古いバージョンである2.3より古いバージョンを提供しないでください。

## `dbschema:diff` コマンドの使用

2つのAdobe Commerce バージョンのデータベーススキーマの違いを取得できます。

```shell
bin/uct dbschema:diff <current-version> <target-version>
```

引数は次のとおりです。

- `<current-version>`：比較する任意のAdobe Commerce バージョン。
- `<target-version>`：比較用の任意のAdobe Commerce バージョンも使用します。

実行例：

```text
bin/uct dbschema:diff 2.4.3 2.4.3-p3

DB schema differences between versions 2.4.3 and 2.4.3-p3:

Table klarna_payments_quote constraint QUOTE_ID_KLARNA_PAYMENTS_QUOTE_QUOTE_ID_QUOTE_ENTITY_ID is present only in version 2.4.3-p3
Table klarna_payments_quote index KLARNA_PAYMENTS_QUOTE_SESSION_ID is present only in version 2.4.3-p3
Table customer_entity column session_cutoff is present only in version 2.4.3-p3
Table customer_visitor column session_id length value is different. 2.4.3: "64", 2.4.3-p3: "1"
Table customer_visitor column session_id comment value is different. 2.4.3: "Session ID", 2.4.3-p3: "Deprecated: Session ID value no longer used"
Table customer_visitor column created_at is present only in version 2.4.3-p3
Table oauth_consumer column secret length value is different. 2.4.3: "32", 2.4.3-p3: "128"
Table oauth_token column secret length value is different. 2.4.3: "32", 2.4.3-p3: "128"
Table admin_user_session column session_id nullable value is different. 2.4.3: "false", 2.4.3-p3: "true"
Table admin_user_session column session_id length value is different. 2.4.3: "128", 2.4.3-p3: "1"
Table admin_user_session column session_id comment value is different. 2.4.3: "Session ID value", 2.4.3-p3: "Deprecated: Session ID value no longer used"

Total detected differences between version 2.4.3 and 2.4.3-p3: 11
```

## `core:code:changes` コマンドの使用

現在のAdobe Commerce インストールを比較して、Adobe Commerceのコアコードがカスタマイズを実装するために変更されたかどうかを検証できます。 次のコマンドは、コア修正のリストのみを表示します。

```shell
bin/uct core:code:changes <dir> <vanilla dir>
```

引数は次のとおりです。

- `<dir>`: Adobe Commerce インストールディレクトリ。
- `<vanilla dir>`: Adobe Commerce Vanilla インストールディレクトリ。

`core:code:changes` コマンドで使用できるオプション：

| **コマンド** | **使用可能なオプション** |
|----------------|-----------------|
| `core:code:changes` | `--help`：使用可能なすべての`--help` オプションを返します。 |

>[!NOTE]
>
> コアコードからカスタムコードを除外することをお勧めします。 アップグレードのベストプラクティスについて詳しくは、Adobe Commerce 2.4 [&#x200B; アップグレードガイド &#x200B;](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf)を参照してください。

### バニラのインストール

_vanilla_&#x200B;のインストールは、特定のリリースバージョンの指定されたバージョンタグまたはブランチのクリーンインストールです。

`bin/uct core:code:changes` コマンドは、システムにバニラ インスタンスがあるかどうかを確認します。 Vanilla インストールを初めて使用する場合は、インタラクティブなコマンドラインの質問で、Adobe Commerce リポジトリ（`https://repo.magento.com/`）からVanilla プロジェクトをダウンロードするよう求められます。

`--vanilla-dir` オプションを指定して[!DNL Upgrade Compatibility Tool] コマンドを実行し、Adobe Commerce Vanilla インストールディレクトリを指定できます。

詳しくは、[&#x200B; バニラインスタンスのデプロイ &#x200B;](https://developer.adobe.com/commerce/contributor/guides/install/) トピックを参照してください。

## `refactor` コマンドの使用

[!DNL Upgrade Compatibility Tool]には、削減された一連の問題を自動的に修正する機能があります。

- 引数を渡さずに使用することが許可されていたが、そのような使用を伴う関数は廃止された。
- Magento テンプレートでの`$this`の使用状況。
- プライベートメソッドでのPHP キーワード `final`の使用。

そのために、`refactor` コマンドを実行します。

```shell
bin/uct refactor <dir>
```

ここで、`<dir>`値は、Adobe Commerce インスタンスが配置されているディレクトリです。

`refactor` コマンドで使用できるオプション：

| **コマンド** | **使用可能なオプション** |
|----------------|-----------------|
| `refactor` | `--help`：使用可能なすべての`--help` オプションを返します。 |

## `graphql:compare` コマンドの使用

このコマンドは、2つのGraphQL エンドポイントをイントロスペクトし、それらの間の壊れた変化と危険な変化を探しているスキーマを比較するオプションを[!DNL Upgrade Compatibility Tool]に提供します。

```shell
bin/uct graphql:compare <schema1> <schema2>
```

引数は次のとおりです。

- `<schema1>`：既存のインストールのエンドポイント URL。
- `<schema2>`: Vanilla インストールのエンドポイント URL。

`graphql:compare` コマンドで使用できるオプション：

| **コマンド** | **使用可能なオプション** |
|----------------|-----------------|
| `graphql:compare` | `--help`：使用可能なすべての`--help` オプションを返します。 |

## `list` コマンドの使用

使用可能な[!DNL Upgrade Compatibility Tool]個のコマンドのリストを返すには、次を実行します。

```shell
bin/uct list
```

## `help` コマンドの使用

[!DNL Upgrade Compatibility Tool] コマンドの一般的なオプションとヘルプを表示するには、次を実行します。

```shell
bin/uct --help
```

これにより、コマンドラインインターフェイスで[!DNL Upgrade Compatibility Tool]に対して使用可能なすべての`help` オプションを含むリストが返されます。

```text
- --raw             To output raw command list
- --format=FORMAT   The output format (txt, xml, json, or md) [default: "txt"]
- --short           To skip describing commands' arguments
- -h, --help            Display help for the given command. When no command is given display help for the list command
- -q, --quiet           Do not output any message
- -V, --version         Display this application version
- --ansi|--no-ansi  Force (or disable --no-ansi) ANSI output
- -n, --no-interaction  Do not ask any interactive question
- -v|vv|vvv, --verbose  Increase the verbosity of messages: 1 for normal output, 2 for more verbose output and 3 for debug
```

特定のコマンドを実行する場合は、オプションとして`--help`を実行できます。 指定したコマンドの`--help` オプションを返します。

`--help` オプションを使用した`upgrade:check` コマンドの例：

```shell
bin/uct upgrade:check --help
```

これは、`upgrade:check` コマンドに対して実行できる特定のオプションを返します。

```shell
- -a, --current-version[=CURRENT-VERSION]: Current Adobe Commerce version, version of the Adobe Commerce installation will be used if omitted.
- -c, --coming-version[=COMING-VERSION]: Target Adobe Commerce version, latest released version of Adobe Commerce will be used if omitted. Provides a list of all available Adobe Commerce versions.
- --json-output-path[=JSON-OUTPUT-PATH]: Path of the file where the output will be exported in json format.
- --html-output-path[=HTML-OUTPUT-PATH]: Path of the file where the output will be exported in HTML format.
- --min-issue-level[=MIN-ISSUE-LEVEL]            Minimal issue level you want to see in the report (warning, error or critical). [default: "warning"]
- -i, --ignore-current-version-compatibility-issues  Ignore common issues for current and coming version
- --context=CONTEXT: Execution context. This option is for integration purposes and does not affect the execution result.
- -h, --help: Display help for that specific command. If no command is provided, `list` command is the default result.
- -q, --quiet: Do not output any messages while executing the command.
- -v, --version: Display application version.
- --ansi, --no-ansi: Enable ANSI output.
- -n, --no-interaction: Do not ask any interactive question while executing the command.
- -v, --vv, --vvv, --verbose: Increase verbosity of output communications. 1 for normal output, 2 for verbose output, and 3 for DEBUG output.
```

## Adobe Commerceのベストプラクティス

- 同じ名前の2つのモジュールを使用しないでください。
- Adobe Commerce [&#x200B; コーディング標準](https://developer.adobe.com/commerce/php/coding-standards)に従います。
- Adobe Commerce 2.4 [&#x200B; アップグレード ガイド &#x200B;](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf)のベストプラクティス。
- [&#128279;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html)Adobe Commerceの[[!DNL Site-Wide Analysis Tool]](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/integrate-analysis-tool.html){target=_blank}から[!DNL Upgrade Compatibility Tool]をクラウドインフラストラクチャ &#x200B; プロジェクトで実行します。

## 成果の最適化

[!DNL Upgrade Compatibility Tool]は、デフォルトでプロジェクトで特定されたすべての問題を含む結果を含むレポートを提供します。 アップグレードを完了するために修正する必要がある問題に焦点を当てるように、結果を最適化できます。

- 現在のバージョンから[!DNL Upgrade Compatibility Tool] レポートの対象バージョンへの更新で導入された新しい問題のみを取得する場合は、オプション `--ignore-current-version-compatibility-issues`を使用します。
- `--min-issue-level` オプションを追加すると、この設定で最小問題レベルを設定できるので、アップグレードに関する最も重要な問題のみに優先的に対処できます。
- [!DNL Upgrade Compatibility Tool]を実行するには、少なくとも2 GBのRAMが必要です。 この設定は、メモリ不足による問題を回避するために推奨されます。 `memory_limit`の設定が低い`upgrade:check` コマンドを実行すると、[!DNL Upgrade Compatibility Tool]に質問が表示されます。
