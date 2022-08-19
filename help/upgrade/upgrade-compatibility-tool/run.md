---
title: 「 [!DNL Upgrade Compatibility Tool]"
description: 次の手順に従って、 [!DNL Upgrade Compatibility Tool] ( Adobe Commerceプロジェクトのコマンドラインインターフェイス ) を使用します。
source-git-commit: c10afb6632fa4e77f46b540c2b89f54b9cab430c
workflow-type: tm+mt
source-wordcount: '1071'
ht-degree: 0%

---


# をダウンロードします。 [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

を使い始めるには、以下を実行します。 [!DNL Upgrade Compatibility Tool] コマンドラインインターフェイスで、次のコマンドを実行してダウンロードします。

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

ツールの実行可能な権限を `chmod` コマンド：

```bash
chmod +x ./uct/bin/uct
```

## この [!DNL Upgrade Compatibility Tool] コマンドラインインターフェイスで

この [!DNL Upgrade Compatibility Tool] は、Adobe Commerceにインストールされているすべてのモジュールを分析することで、カスタマイズされたインスタンスを特定のバージョンと照合するツールです。 最新バージョンのAdobe Commerceにアップグレードする前に対処する必要がある重要な問題、エラーおよび警告のリストを返します。

参照 [ビデオチュートリアル](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/upgrade/upgrade-compatibility-tool-overview.html?lang=en) (06:02): [!DNL Upgrade Compatibility Tool].

使用可能な [!DNL Upgrade Compatibility Tool] コマンドラインインターフェイスで、次の操作を実行します。

| **コマンド** | **説明** |
|----------------|-----------------|
| `upgrade:check` | このコマンドは、 [!DNL Upgrade Compatibility Tool] に含まれるすべてのモジュールを分析する。 |
| `dbschema:diff` | このコマンドは、指定した 2 つのAdobe Commerceバージョン間のデータベーススキーマのすべての違いを表示します。 |
| `core:code:changes` | このコマンドは、現在のAdobe Commerceのインストールと、バニラのクリーンインストールを比較します。 |
| `refactor` | このコマンドを実行すると、一部の問題が自動的に修正されます。 |
| `graphql:compare` | このコマンドは、2 つの GraphQL エンドポイントを紹介し、それらのスキーマを比較するオプションを提供します。 |
| `list` | このコマンドは、 [!DNL Upgrade Compatibility Tool] 使用可能なコマンド |
| `help` | このコマンドは、使用可能なすべての `help`オプション [!DNL Upgrade Compatibility Tool]. このコマンドは、前のコマンドのオプションと同様に実行できます。 |

## 以下を使用： `upgrade:check` command

この `upgrade:check` コマンドは、その特定のAdobe Commerceインスタンスに対するコアコードの変更と、そのインスタンスにインストールされているすべてのカスタムコードの変更を確認します。

この `upgrade:check` コマンドは、ツールを実行するメインコマンドです。

```bash
bin/uct upgrade:check <dir>
```

ここで、 `<dir>` 値は、Adobe Commerceインスタンスが配置されるディレクトリです。

次に使用できるオプション： `upgrade:check` コマンド：

| **コマンド** | **使用可能なオプション** |
|----------------|-----------------|
| `upgrade:check` | <ul><li>—help:使用可能なすべてのオプションを返します。</li><li>—min-issue-level:問題の最小レベルに従って問題をフィルターできます（デフォルト値は WARNING）。</li><li>—ignore-current-version-compatibility-issues （または —i）:現在のバージョンの重要な問題、エラーおよび警告をレポートに含めない場合。</li><li>—comming version （または —c）:特定のAdobe Commerceバージョンをターゲットにします。</li></ul> |

この [!DNL Upgrade Compatibility Tool] を使用すると、 `upgrade:check` 命令 `--ignore-current-version-compatibility-issues` オプション。 現在のバージョンから現在のバージョンの対象バージョンに、アップデートで導入された新しい問題のみを取得する場合にのみ、このオプションを使用します [!DNL Upgrade Compatibility Tool] レポート：

```bash
bin/uct upgrade:check --ignore-current-version-compatibility-issues <dir>
```

>[!NOTE]
>
> これは、PHP API の検証にのみ適用されます。

### の追加 `--coming-version` オプション

現在のAdobe Commerceのインストールを任意のAdobe Commerceバージョンと比較できます `>=2.3` を使用して、 `--coming-version` オプション。

バージョンを `upgrade:check` コマンド：

```bash
bin/uct upgrade:check <dir> -c 2.4.3
```

ここで、 `-c, --coming-version[=COMING-VERSION]` は、Adobe Commerceのターゲットバージョンを指します。

を実行する際には、いくつかの制限があります `--coming-version`:

- このパラメーターは、Adobe Commerceの特定のバージョンを識別する任意のタグを参照します。
- これを明示的に指定する必要があります。この値のみを指定しても、機能しません。
- 引用符を付けずにタグバージョンを指定します（一重引用符も二重引用符も付けません）。 ~~&#39;2.4.1-develop&#39;~~.
- 現在インストールしているバージョンより古いバージョンを提供したり、現在サポートされている最も古いバージョンである 2.3 より古いバージョンを提供したりしないでください。

## 以下を使用： `dbschema:diff` command

2 つのAdobe Commerceバージョンのデータベーススキーマの違いを取得できます。

```bash
bin/uct dbschema:diff <current-version> <target-version>
```

引数は次のようになります。

- `<current-version>`:比較対象の任意のAdobe Commerceバージョン。
- `<target-version>`:また、比較の対象となるAdobe Commerceのバージョンも含まれます。

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

## 以下を使用： `core:code:changes` command

現在のAdobe Commerceのインストールを比較して、Adobe Commerceのコアコードがカスタマイズを実装するように変更されたかどうかを検証できます。 このコマンドは、コアの変更のリストのみを表示します。

```bash
bin/uct core:code:changes <dir> <vanilla dir>
```

引数は次のようになります。

- `<dir>`:Adobe Commerceインストールディレクトリ。
- `<vanilla dir>`:Adobe Commerce vanilla のインストールディレクトリ。

次に使用できるオプション： `core:code:changes` コマンド：

| **コマンド** | **使用可能なオプション** |
|----------------|-----------------|
| `core:code:changes` | `--help`:使用可能なすべてを返します `--help` オプション。 |

>[!NOTE]
>
> カスタムコードをコアコードから除外することをお勧めします。 Adobe Commerce 2.4 を参照してください。 [アップグレードガイド](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf) その他のアップグレードのベストプラクティスを参照してください。

### バニラインストール

A _バニラ_ インストールは、特定のリリースバージョンの指定したバージョンタグまたはブランチのクリーンインストールです。

この `bin/uct core:code:changes` コマンドは、システムに vanilla インスタンスが存在するかどうかを確認します。 バニラインストールを初めて使用する場合は、Adobe Commerceリポジトリ (`https://repo.magento.com/`) をクリックします。

以下を実行すると、 [!DNL Upgrade Compatibility Tool] コマンドを `--vanilla-dir` Adobe Commerce vanilla インストールディレクトリを指定するオプション。

詳しくは、 [バニラインスタンスのデプロイ](https://devdocs.magento.com/contributor-guide/contributing.html#vanilla-pr) トピックを参照してください。

## 以下を使用： `refactor` command

この [!DNL Upgrade Compatibility Tool] には、以下の一連の問題を自動的に修正する機能があります。

- 引数を渡さずに使用できた関数ですが、このような使用方法では廃止されました。
- の使用方法 `$this` Magento
- PHP キーワードの使用 `final` 非公開メソッドで使用できます。

それには、 `refactor` コマンド：

```bash
bin/uct refactor <dir>
```

ここで、 `<dir>` 値は、Adobe Commerceインスタンスが配置されるディレクトリです。

次に使用できるオプション： `refactor` コマンド：

| **コマンド** | **使用可能なオプション** |
|----------------|-----------------|
| `refactor` | `--help`:使用可能なすべてを返します `--help` オプション。 |

## 以下を使用： `graphql:compare` command

このコマンドは、 [!DNL Upgrade Compatibility Tool] 2 つの GraphQL エンドポイントを紹介し、それらのエンドポイント間で重大で危険な変更があるかどうかをスキーマを比較するには、次の手順を実行します。

```bash
bin/uct graphql:compare <schema1> <schema2>
```

引数は次のようになります。

- `<schema1>`:既存のインストールのエンドポイント URL。
- `<schema2>`:バニラインストールのエンドポイント URL。

次に使用できるオプション： `graphql:compare` コマンド：

| **コマンド** | **使用可能なオプション** |
|----------------|-----------------|
| `graphql:compare` | `--help`:使用可能なすべてを返します `--help` オプション。 |

## 以下を使用： `list` command

リストを返すには [!DNL Upgrade Compatibility Tool] 使用可能なコマンド、次のコマンドを実行します。

```bash
bin/uct list
```

## 以下を使用： `--help` command

次の手順で [!DNL Upgrade Compatibility Tool] コマンドの一般的なオプションとヘルプ：

```bash
bin/uct --help
```

これにより、使用可能なすべての `help` オプション [!DNL Upgrade Compatibility Tool] コマンドラインインターフェイスで、次の操作を実行します。

```terminal
- -a, --current-version[=CURRENT-VERSION]: Current Adobe Commerce version, version of the Adobe Commerce installation will be used if omitted.
- -c, --coming-version[=COMING-VERSION]: Target Adobe Commerce version, latest released version of Adobe Commerce will be used if omitted. Provides a list of all available Adobe Commerce versions.
- --json-output-path[=JSON-OUTPUT-PATH]: Path of the file where the output will be exported in json format.
- --html-output-path[=HTML-OUTPUT-PATH]: Path of the file where the output will be exported in HTML format.
- --context=CONTEXT: Execution context. This option is for integration purposes and does not affect the execution result.
- -h, --help: Display help for that specific command. If no command is provided, `list` command is the default result.
- -q, --quiet: Do not output any messages while executing the command.
- -v, --version: Display application version.
- --ansi, --no-ansi: Enable ANSI output.
- -n, --no-interaction: Do not ask any interactive question while executing the command.
- -v, --vv, --vvv, --verbose: Increase verbosity of output communications. 1 for normal output, 2 for verbose output, and 3 for DEBUG output.
```

ただし、 `--help` をオプションとして使用します。 これは、特定の `--help` 特定のコマンドのオプション。

例 `upgrade:check` ～に命令する `--help` オプション：

```bash
bin/uct upgrade:check --help
```

これは、 `upgrade:check` コマンド：

```terminal
--min-issue-level.
-i, --ignore-current-version-compatibility-issues.
```

## Adobe Commerceのベストプラクティスに従う

- 同じ名前の 2 つのモジュールを使用しないでください。
- フォローAdobe Commerce [コーディング規格](https://devdocs.magento.com/guides/v2.4/coding-standards/bk-coding-standards.html).
- Adobe Commerce 2.4 [アップグレードガイド](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf) ベストプラクティス。

## 結果の最適化

この [!DNL Upgrade Compatibility Tool] は、結果と、デフォルトでプロジェクトで特定されたすべての問題を含むレポートを提供します。 結果を最適化して、アップグレードを完了するために修正する必要がある問題に焦点を当てることができます。

- オプションを使用 `--ignore-current-version-compatibility-issues` 現在のバージョンから現在のバージョンの対象バージョンにアップデートで導入された新しい問題のみを取得したい場合 [!DNL Upgrade Compatibility Tool] レポート。
- の追加 `--min-issue-level` オプションを選択すると、最小の問題レベルを設定して、アップグレードに関する最も重要な問題のみを優先するのに役立ちます。
- この [!DNL Upgrade Compatibility Tool] を実行するには、2GB 以上の RAM が必要です。 この設定は、メモリ不足による問題を回避するために推奨されます。 この [!DNL Upgrade Compatibility Tool] を実行すると、質問が表示されます。 `upgrade:check` 低いコマンド `memory_limit` 設定。
