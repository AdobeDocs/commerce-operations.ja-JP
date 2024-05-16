---
title: を実行 [!DNL Upgrade Compatibility Tool]
description: を実行するには、次の手順に従います [!DNL Upgrade Compatibility Tool] Adobe Commerce プロジェクトのコマンドラインインターフェイス。
exl-id: ea467a74-18eb-476b-96e2-23f4fc257d73
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1077'
ht-degree: 0%

---

# をダウンロード [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

の使用を開始するには [!DNL Upgrade Compatibility Tool] コマンドラインインターフェイスで、次のコマンドを実行してダウンロードします。

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

を使用して、ツールに実行可能な権限を付与する必要がある場合があります。 `chmod` コマンド：

```bash
chmod +x ./uct/bin/uct
```

## この [!DNL Upgrade Compatibility Tool] コマンドラインインターフェイスで

この [!DNL Upgrade Compatibility Tool] は、Adobe Commerce カスタマイズ済みインスタンスにインストールされているすべてのモジュールを分析して、そのインスタンスを特定のバージョンと照合するツールです。 Adobe Commerceの最新バージョンにアップグレードする前に対処する必要がある重要な問題、エラー、警告のリストを返します。

これを表示 [ビデオチュートリアル](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/upgrade/upgrade-compatibility-tool-overview.html?lang=en) （06:02） [!DNL Upgrade Compatibility Tool].

で使用可能なコマンド [!DNL Upgrade Compatibility Tool] コマンドラインインターフェイスの場合：

| **コマンド** | **説明** |
|----------------|-----------------|
| `upgrade:check` | このコマンドは、 [!DNL Upgrade Compatibility Tool] それにインストールされているすべてのモジュールを分析することによって。 |
| `dbschema:diff` | このコマンドは、指定された 2 つのAdobe Commerce バージョン間のデータベーススキーマのすべての違いを表示します。 |
| `core:code:changes` | このコマンドは、現在のAdobe Commerceのインストールを、新規の vanilla インストールと比較します。 |
| `refactor` | このコマンドを使用すると、問題の軽減されたセットが自動的に修正されます。 |
| `graphql:compare` | このコマンドには、2 つのGraphQL エンドポイントをイントロスペクションし、それらのスキーマを比較するオプションが用意されています。 |
| `list` | このコマンドは、すべての [!DNL Upgrade Compatibility Tool] 使用可能なコマンド。 |
| `help` | このコマンドは、使用可能なすべての値を返します `help`のオプション [!DNL Upgrade Compatibility Tool]. このコマンドは、前のコマンドのオプションと同様に実行できます。 |

## の使用 `upgrade:check` コマンド

この `upgrade:check` コマンドは、その特定のAdobe Commerce インスタンスのコアコードの変更と、そのインスタンスにインストールされているすべてのカスタムコードの変更を確認します。

この `upgrade:check` コマンドは、ツールを実行する主なコマンドです。

```bash
bin/uct upgrade:check <dir>
```

ここで、 `<dir>` 値は、Adobe Commerce インスタンスが配置されているディレクトリです。

で使用可能なオプション `upgrade:check` コマンド：

| **コマンド** | **使用可能なオプション** |
|----------------|-----------------|
| `upgrade:check` | <ul><li>—help：使用可能なすべてのオプションを返す。</li><li>—current-version：現在のAdobe Commerceのバージョン。 このパラメーターは必須で、常に使用する必要があります。</li><li>—min-issue-level：最小のイシューレベルに従ってイシューをフィルタリングできます（デフォルト値は WARNING）。</li><li>—ignore-current-version-compatibility-issues （または – i）: レポートに現在のバージョンの重大な問題、エラー、および警告を含めない場合。</li><li>—coming-version （または – c）：特定のAdobe Commerceのバージョンを対象にします。 省略した場合は、利用可能な最新のバージョンが使用されます。</li></ul> |

この [!DNL Upgrade Compatibility Tool] を実行できます `upgrade:check` を使用したコマンド `--ignore-current-version-compatibility-issues` オプション。 このオプションは、現在のバージョンからターゲットのバージョンへの更新で導入される新しいイシューのみを取得する場合に使用します [!DNL Upgrade Compatibility Tool] レポート :

```bash
bin/uct upgrade:check --ignore-current-version-compatibility-issues <dir>
```

>[!NOTE]
>
> これは、PHP API の検証にのみ適用されます。

### の追加 `--coming-version` オプション

現在インストールされているAdobe Commerceを任意のAdobe Commerceのバージョンと比較できます `>=2.3` を使用する `--coming-version` オプション。

を実行する場合は、バージョンをパラメーターとして指定する必要があります `upgrade:check` コマンド：

```bash
bin/uct upgrade:check <dir> -c 2.4.3
```

ここで、 `-c, --coming-version[=COMING-VERSION]` は、Adobe Commerceのターゲットバージョンを参照します。

を実行する際にはいくつかの制限があります `--coming-version`:

- このパラメーターは、Adobe Commerceの特定のバージョンを識別する任意のタグを参照します。
- これを明示的に指定する必要があります。の値のみをを指定しても機能しません。
- 引用符を使用せずにタグバージョンを指定します（一重引用符も二重引用符も使用しません）。 ~~&#39;2.4.1-develop&#39;~~.
- 現在インストールしているバージョンよりも古いバージョンや、現時点でサポートされている最も古い 2.3 よりも古いバージョンを提供しないでください。

## の使用 `dbschema:diff` コマンド

2 つのAdobe Commerce バージョンのデータベーススキーマの違いを取得できます。

```bash
bin/uct dbschema:diff <current-version> <target-version>
```

ここで、引数は次のようになります。

- `<current-version>`：比較用の任意のAdobe Commerce バージョン。
- `<target-version>`：比較のため任意のAdobe Commerce バージョンも使用できます。

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

## の使用 `core:code:changes` コマンド

現在インストールされているAdobe Commerceを比較して、Adobe Commerceのコアコードがカスタマイズを実装するように変更されたかどうかを検証できます。 このコマンドは、コア変更のみのリストを表示します。

```bash
bin/uct core:code:changes <dir> <vanilla dir>
```

ここで、引数は次のようになります。

- `<dir>`:Adobe Commerce インストールディレクトリ。
- `<vanilla dir>`:Adobe Commerce vanilla インストールディレクトリ。

で使用可能なオプション `core:code:changes` コマンド：

| **コマンド** | **使用可能なオプション** |
|----------------|-----------------|
| `core:code:changes` | `--help`：使用可能なすべての値を返します `--help` オプション。 |

>[!NOTE]
>
> カスタムコードをコアコードから除外することをお勧めします。 Adobe Commerce 2.4 を参照 [アップグレードガイド](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf) アップグレードに関するその他のベストプラクティスについて説明します。

### Vanilla インストール

A _バニラ_ インストールは、特定のリリースバージョンの指定されたバージョンタグまたはブランチのクリーンインストールです。

この `bin/uct core:code:changes` コマンドは、システムに vanilla インスタンスがあるかどうかを確認します。 バニラインストールを初めて使用する場合は、インタラクティブなコマンドライン質問で、Adobe Commerce リポジトリからバニラプロジェクトをダウンロードするように求められます（`https://repo.magento.com/`）に設定します。

を実行できます [!DNL Upgrade Compatibility Tool] を使用したコマンド `--vanilla-dir` Adobe Commerce vanilla インストールディレクトリを指定するオプション。

を参照してください。 [バニラインスタンスのデプロイ](https://developer.adobe.com/commerce/contributor/guides/code-contributions/#deploy-vanilla-magento-open-source-instance) を参照してください。

## の使用 `refactor` コマンド

この [!DNL Upgrade Compatibility Tool] には、削減された問題のセットを自動的に修正する機能があります。

- 引数を渡さずに使用できましたが、現在はそのような使用が非推奨（廃止予定）になっている関数。
- の使用 `$this` （Magentoテンプレートで）。
- PHP キーワードの使用 `final` プライベートメソッドで。

その場合は、 `refactor` コマンド：

```bash
bin/uct refactor <dir>
```

ここで、 `<dir>` 値は、Adobe Commerce インスタンスが配置されているディレクトリです。

で使用可能なオプション `refactor` コマンド：

| **コマンド** | **使用可能なオプション** |
|----------------|-----------------|
| `refactor` | `--help`：使用可能なすべての値を返します `--help` オプション。 |

## の使用 `graphql:compare` コマンド

このコマンドは、 [!DNL Upgrade Compatibility Tool] 2 つのGraphQL エンドポイントをイントロスペクションし、それらの間の重大な変更を探してスキーマを比較するには：

```bash
bin/uct graphql:compare <schema1> <schema2>
```

ここで、引数は次のようになります。

- `<schema1>`：既存のインストールのエンドポイント URL。
- `<schema2>`：バニラインストールのエンドポイント URL。

で使用可能なオプション `graphql:compare` コマンド：

| **コマンド** | **使用可能なオプション** |
|----------------|-----------------|
| `graphql:compare` | `--help`：使用可能なすべての値を返します `--help` オプション。 |

## の使用 `list` コマンド

を返します [!DNL Upgrade Compatibility Tool] 使用可能なコマンド、次を実行：

```bash
bin/uct list
```

## の使用 `help` コマンド

を表示するには [!DNL Upgrade Compatibility Tool] コマンドの一般的なオプションとヘルプを実行します：

```bash
bin/uct --help
```

これにより、使用可能なすべてのリストが返されます `help` のオプション [!DNL Upgrade Compatibility Tool] コマンドラインインターフェイスの場合：

```terminal
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

実行することは可能です `--help` 特定のコマンドを実行する場合のオプションとして。 を返します `--help` 指定したコマンドのオプション。

の例 `upgrade:check` コマンドと `--help` オプション：

```bash
bin/uct upgrade:check --help
```

これにより、に対して実行できる特定のオプションが返されます `upgrade:check` コマンド：

```terminal
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
- Adobe Commerceをフォロー [コーディング標準](https://developer.adobe.com/commerce/php/coding-standards/).
- Adobe Commerce 2.4 [アップグレードガイド](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf) ベストプラクティス。
- を実行 [!DNL Upgrade Compatibility Tool] から [[!DNL Site-Wide Analysis Tool]](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/integrate-analysis-tool.html) （用） [クラウドインフラストラクチャー上のAdobe Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html){target=_blank} プロジェクト。

## 結果を最適化

この [!DNL Upgrade Compatibility Tool] デフォルトでプロジェクトで特定されたすべてのイシューの結果を含むレポートを提供します。 結果を最適化して、アップグレードを完了するために修正が必要な問題に焦点を当てることができます。

- オプションを使用 `--ignore-current-version-compatibility-issues` の現在のバージョンから対象のバージョンへの更新で導入された新しいイシューのみを取得したい場合 [!DNL Upgrade Compatibility Tool] レポート。
- の追加 `--min-issue-level` この設定では、最小問題レベルを設定して、アップグレードで最も重要な問題にのみ優先順位を付けることができます。
- この [!DNL Upgrade Compatibility Tool] 実行には少なくとも 2 GB の RAM が必要です。 この設定は、メモリ制限が低いことによる問題を回避するために推奨されます。 この [!DNL Upgrade Compatibility Tool] を実行すると質問が表示されます `upgrade:check` 低い値でコマンド `memory_limit` の設定値。
