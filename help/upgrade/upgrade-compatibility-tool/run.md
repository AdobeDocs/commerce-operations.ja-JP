---
title: ' [!DNL Upgrade Compatibility Tool] を実行します。'
description: Adobe Commerce プロジェクトのコマンドラ  [!DNL Upgrade Compatibility Tool]  ンインターフェイスでコマンドを実行するには、次の手順に従います。
exl-id: ea467a74-18eb-476b-96e2-23f4fc257d73
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '1077'
ht-degree: 0%

---

# [!DNL Upgrade Compatibility Tool] のダウンロード

{{commerce-only}}

コマンドラインインターフェイスで [!DNL Upgrade Compatibility Tool] の使用を開始するには、次のコマンドを実行してダウンロードします。

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

場合によっては、`chmod` のコマンドを使用して、ツールの実行可能アクセス権を付与する必要があります。

```bash
chmod +x ./uct/bin/uct
```

## コマンドラインインターフェイスの [!DNL Upgrade Compatibility Tool]

[!DNL Upgrade Compatibility Tool] は、Adobe Commerce カスタマイズ済みインスタンスにインストールされているすべてのモジュールを分析して、そのインスタンスを特定のバージョンと照合するツールです。 Adobe Commerceの最新バージョンにアップグレードする前に対処する必要がある重要な問題、エラー、警告のリストを返します。

[!DNL Upgrade Compatibility Tool] について詳しくは、この [ ビデオチュートリアル ](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/upgrade/upgrade-compatibility-tool-overview.html?lang=ja) （06:02）を参照してください。

コマンドラインインターフェイスで [!DNL Upgrade Compatibility Tool] に使用できるコマンド：

| **コマンド** | **説明** |
|----------------|-----------------|
| `upgrade:check` | このコマンドは、インストールされているすべてのモジュールを分析して [!DNL Upgrade Compatibility Tool] を実行します。 |
| `dbschema:diff` | このコマンドは、指定された 2 つのAdobe Commerce バージョン間のデータベーススキーマのすべての違いを表示します。 |
| `core:code:changes` | このコマンドは、現在のAdobe Commerceのインストールを、新規の vanilla インストールと比較します。 |
| `refactor` | このコマンドを使用すると、問題の軽減されたセットが自動的に修正されます。 |
| `graphql:compare` | このコマンドには、2 つのGraphQL エンドポイントをイントロスペクションし、それらのスキーマを比較するオプションが用意されています。 |
| `list` | このコマンドは、使用可能なすべてのコマンドのリスト [!DNL Upgrade Compatibility Tool] 返します。 |
| `help` | このコマンドは、[!DNL Upgrade Compatibility Tool] に使用可能なすべての `help` オプションを返します。 このコマンドは、前のコマンドのオプションと同様に実行できます。 |

## `upgrade:check` コマンドの使用

`upgrade:check` コマンドは、その特定のAdobe Commerce インスタンスのコアコードの変更と、そのインスタンスにインストールされているすべてのカスタムコードの変更を確認します。

`upgrade:check` のコマンドは、ツールを実行する主なコマンドです。

```bash
bin/uct upgrade:check <dir>
```

値 `<dir>`、Adobe Commerce インスタンスがあるディレクトリです。

`upgrade:check` コマンドで使用可能なオプション：

| **コマンド** | **使用可能なオプション** |
|----------------|-----------------|
| `upgrade:check` | <ul><li>—help：使用可能なすべてのオプションを返す。</li><li>—current-version：現在のAdobe Commerceのバージョン。 このパラメーターは必須で、常に使用する必要があります。</li><li>—min-issue-level：最小のイシューレベルに従ってイシューをフィルタリングできます（デフォルト値は WARNING）。</li><li>—ignore-current-version-compatibility-issues （または – i）: レポートに現在のバージョンの重大な問題、エラー、および警告を含めない場合。</li><li>—coming-version （または – c）：特定のAdobe Commerceのバージョンを対象にします。 省略した場合は、利用可能な最新のバージョンが使用されます。</li></ul> |

[!DNL Upgrade Compatibility Tool] を使用すると、`--ignore-current-version-compatibility-issues` オプションを指定して `upgrade:check` コマンドを実行できます。 このオプションは、現在のバージョンから [!DNL Upgrade Compatibility Tool] レポートのターゲットバージョンへの更新で導入される新しいイシューのみを取得する場合に使用します。

```bash
bin/uct upgrade:check --ignore-current-version-compatibility-issues <dir>
```

>[!NOTE]
>
> これは、PHP API の検証にのみ適用されます。

### `--coming-version` オプションの追加

`--coming-version` オプションを使用すると、現在のAdobe CommerceのインストールとAdobe Commerceのバージョン `>=2.3` を比較できます。

`upgrade:check` コマンドを実行する場合は、バージョンをパラメーターとして指定する必要があります。

```bash
bin/uct upgrade:check <dir> -c 2.4.3
```

ここで、`-c, --coming-version[=COMING-VERSION]` はAdobe Commerceのターゲットバージョンを表します。

`--coming-version` を実行する際には、いくつかの制限があります。

- このパラメーターは、Adobe Commerceの特定のバージョンを識別する任意のタグを参照します。
- これを明示的に指定する必要があります。の値のみをを指定しても機能しません。
- 引用符を使用せずに（シングルもダブルも使用せずに） タグバージョンを指定：~~&#39;2.4.1-develop&#39;~~。
- 現在インストールしているバージョンよりも古いバージョンや、現時点でサポートされている最も古い 2.3 よりも古いバージョンを提供しないでください。

## `dbschema:diff` コマンドの使用

2 つのAdobe Commerce バージョンのデータベーススキーマの違いを取得できます。

```bash
bin/uct dbschema:diff <current-version> <target-version>
```

ここで、引数は次のようになります。

- `<current-version>`：比較用の任意のAdobe Commerce バージョン。
- `<target-version>`：比較用に任意のAdobe Commerce バージョンも使用できます。

実行例：

```bash
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

現在インストールされているAdobe Commerceを比較して、Adobe Commerceのコアコードがカスタマイズを実装するように変更されたかどうかを検証できます。 このコマンドは、コア変更のみのリストを表示します。

```bash
bin/uct core:code:changes <dir> <vanilla dir>
```

ここで、引数は次のようになります。

- `<dir>`:Adobe Commerce インストールディレクトリ。
- `<vanilla dir>`:Adobe Commerce vanilla インストールディレクトリ。

`core:code:changes` コマンドで使用可能なオプション：

| **コマンド** | **使用可能なオプション** |
|----------------|-----------------|
| `core:code:changes` | `--help`：使用可能なすべての `--help` オプションを返します。 |

>[!NOTE]
>
> カスタムコードをコアコードから除外することをお勧めします。 アップグレードに関するベストプラクティスについて詳しくは、Adobe Commerce 2.4 [ アップグレードガイド ](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf?lang=ja) を参照してください。

### Vanilla インストール

_バニラ_ インストールは、特定のリリースバージョンの指定されたバージョンタグまたはブランチのクリーンインストールです。

`bin/uct core:code:changes` コマンドは、システムに vanilla インスタンスがあるかどうかを確認します。 バニラインストールを初めて使用する場合は、インタラクティブなコマンドライン質問で、Adobe Commerce リポジトリ（`https://repo.magento.com/`）からバニラプロジェクトをダウンロードするように求められます。

[!DNL Upgrade Compatibility Tool] コマンドを `--vanilla-dir` オプションを使用して実行すると、Adobe Commerce vanilla インストールディレクトリを指定できます。

詳しくは、[vanilla インスタンスのデプロイ ](https://developer.adobe.com/commerce/contributor/guides/code-contributions/#deploy-vanilla-magento-open-source-instance) のトピックを参照してください。

## `refactor` コマンドの使用

[!DNL Upgrade Compatibility Tool] には、削減された問題のセットを自動的に修正する機能があります。

- 引数を渡さずに使用できましたが、現在はそのような使用が非推奨（廃止予定）になっている関数。
- Magentoテンプレートでの `$this` の使用。
- プライベートメソッドでの PHP キーワード `final` の使用。

その場合は、`refactor` コマンドを実行します。

```bash
bin/uct refactor <dir>
```

値 `<dir>`、Adobe Commerce インスタンスがあるディレクトリです。

`refactor` コマンドで使用可能なオプション：

| **コマンド** | **使用可能なオプション** |
|----------------|-----------------|
| `refactor` | `--help`：使用可能なすべての `--help` オプションを返します。 |

## `graphql:compare` コマンドの使用

このコマンドは、2 つのGraphQL エンドポイントをイントロスペク [!DNL Upgrade Compatibility Tool] ョンし、それらのスキーマを比較して、間の重大な変更を探すためのオプションを提供します。

```bash
bin/uct graphql:compare <schema1> <schema2>
```

ここで、引数は次のようになります。

- `<schema1>`：既存のインストールのエンドポイント URL。
- `<schema2>`: バニラインストールのエンドポイント URL。

`graphql:compare` コマンドで使用可能なオプション：

| **コマンド** | **使用可能なオプション** |
|----------------|-----------------|
| `graphql:compare` | `--help`：使用可能なすべての `--help` オプションを返します。 |

## `list` コマンドの使用

使用可能な [!DNL Upgrade Compatibility Tool] のコマンドのリストを返すには、次を実行します。

```bash
bin/uct list
```

## `help` コマンドの使用

[!DNL Upgrade Compatibility Tool] のコマンドの一般的なオプションとヘルプを表示するには、次のコマンドを実行します。

```bash
bin/uct --help
```

これにより、コマンドラインインターフェイスで [!DNL Upgrade Compatibility Tool] ーザーに使用できるすべての `help` オプションのリストが返されます。

```
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

特定のコマンドを実行する際に、`--help` をオプションとして実行することもできます。 指定したコマンド `--help` オプションを返します。

オプションを使用した `upgrade:check` コマンド `--help` 例：

```bash
bin/uct upgrade:check --help
```

これにより、`upgrade:check` のコマンドに対して実行できる特定のオプションが返されます。

```
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

## Adobe Commerceのベストプラクティスに従う

- 2 つのモジュールに同じ名前を付けないでください。
- Adobe Commerce[ コーディング標準 ](https://developer.adobe.com/commerce/php/coding-standards/) に従います。
- Adobe Commerce 2.4[ アップグレードガイド ](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf?lang=ja) のベストプラクティス。
- クラウドインフラストラクチャー上の [Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html?lang=ja){target=_blank} プロジェクトの [[!DNL Site-Wide Analysis Tool]](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/integrate-analysis-tool.html?lang=ja) から [!DNL Upgrade Compatibility Tool] を実行します。

## 結果を最適化

[!DNL Upgrade Compatibility Tool] は、プロジェクトでデフォルトで特定されたすべてのイシューの結果を含んだレポートを提供します。 結果を最適化して、アップグレードを完了するために修正が必要な問題に焦点を当てることができます。

- 現在のバージョンから [!DNL Upgrade Compatibility Tool] レポートのターゲットバージョンへの更新で導入された新しいイシューのみを取得する場合は、オプション `--ignore-current-version-compatibility-issues` を使用します。
- この設定では、「`--min-issue-level`」オプションを追加して、最小問題レベルを設定し、アップグレードで最も重要な問題のみを優先順位付けするのに役立ちます。
- [!DNL Upgrade Compatibility Tool] を実行するには、少なくとも 2 GB の RAM が必要です。 この設定は、メモリ制限が低いことによる問題を回避するために推奨されます。 `upgrade:check` コマンドを低 `memory_limit` 設定で実行すると、[!DNL Upgrade Compatibility Tool] に質問が表示されます。
