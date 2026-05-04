---
title: アップグレード範囲について
description: Adobe Commerce カスタムモジュールまたはサードパーティの拡張機能に影響を与える可能性のあるリリースの下位互換性のない変更について説明します。
exl-id: dab2a14f-dbf0-422e-afb4-642e2220ec7a
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '946'
ht-degree: 0%

---

# アップグレードの範囲について

[ リリースノート ](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/overview)を確認して、サードパーティおよびカスタムモジュールに影響を与える可能性のある機能強化、バグ修正、既知の問題など、リリースの範囲を理解します。

## 後方互換性のない変更

Adobe Commerce リリースには、下位互換性のない変更が含まれている場合があります。 下位互換性のない変更に関するドキュメントを確認するには、次を参照してください。

- **[重大な変更のハイライト ](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/)** – 大きな影響を与える変更で、サードパーティモジュールが引き続き機能するようにするために、詳細な説明と特別な指示が必要です。
- **[軽微な変更の参照](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/reference/)** - クラス、API メンバーシップ、データベース、依存関係インジェクション、インターフェイス、レイアウト、システム、およびXSDの軽微な変更について説明する、コードベースから生成された参照ドキュメント。

## サードパーティの拡張機能

Adobe Commerce Marketplaceの新しい互換性ポリシーにより、リストされている&#x200B;_すべての_&#x200B;拡張機能が、一般提供日から30日以内に最新のリリース版と互換性を持つことが保証されます。 そのため、可能な限りMarketplaceを通じてサードパーティの拡張機能を入手することが重要です。

## カスタムモジュール

すべてのカスタムモジュールは、アップグレードするターゲットバージョンに対してチェックする必要があります。 これは、アップグレードの中で最も時間とリソースを必要とするプロセスです。 カスタムモジュールを評価するときは、後方互換性のない変更を探し、コントローラの分解などの新しいプラクティスを認識する必要があります。 詳しくは、[ リリースノート ](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/overview)を参照してください。 また、モジュール開発に関する[ ベストプラクティス ](https://developer.adobe.com/commerce/php/best-practices/extensions/)に従っていることを確認してください。

## [!DNL Upgrade Compatibility Tool]

[!DNL Upgrade Compatibility Tool]は、潜在的なアップグレードの問題についてインスタンスを分析するコマンドラインツールです。 インストールした現在のバージョンと、アップグレードしようとしているバージョンの間の問題をチェックします。

このツールを使用することで、アップグレードの範囲と影響を把握するために必要な労力が軽減されます。 アップグレード時の一般的なコードの問題を回避し、特定された問題を解決する方法について明確な指示を提供します。 また、アップグレードを成功させるために必要な最も重要な問題に優先順位を付けることも可能になり、アップグレード時の時間とコストの両方を節約できます。

[!DNL Upgrade Compatibility Tool]の使用を開始するには、次の節を参照してください。 技術的な詳細と高度なユースケースについては、[!DNL Upgrade Compatibility Tool] [ ガイド ](../upgrade-compatibility-tool/overview.md)を参照してください。

### ツールをダウンロード

Composerを使用してツールをダウンロードします。 PHP 7.3以降、少なくとも2 GBのRAM、Node.js （GraphQLとの互換性を確認している場合）、Adobe Commerce ライセンスが必要です。

```shell
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

### ツールを実行

インスタンスを分析し、エラー、警告、重大な問題を確認するには：

```shell
bin/uct upgrade:check <dir> -c <coming version> 
```

>[!NOTE]
>
> `<dir>`引数は、コードベースが格納されるディレクトリです。 `-c` オプションは、コードベースと指定されたバージョンを比較します。

チームが対処すべき最も重要な課題を特定する方法：

```shell
bin/uct upgrade:check /path/to/magento/ --ignore-current-compatibility-issues –min-issue-level critical --vanilla-dir /path/to/vanilla/code/ /path/to/magento/app/code/Vendor/
```

このコマンドで使用するその他のオプションは次のとおりです。

- `--ignore-current-version-compatibility-issues` – 現在のバージョンに対するすべての既知の重大な問題、エラー、および警告を非表示にします。 アップグレードしようとしているバージョンに対するエラーのみが提供されます。

- `--min-issue-level` - アップグレードに関する最も重要な問題のみを優先できるように、最小問題レベルを設定できます。 オプションは、警告、エラー、および重要度の高い順に重要です。

- `-m | [=MODULE-PATH]` – 特定のベンダー、モジュール、ディレクトリのみを分析する場合は、パスをオプションとしても指定できます。

- `--vanilla-dir` – 機能またはカスタマイズの非標準の実装についてコアコードを確認できます。 これらは事前に掃除しておくことが重要です。 バージョンのバニラインスタンスは、参照用に自動的にダウンロードされます。

  >[!NOTE]
  >
  > これは、ツールの`core:code:changes` コマンドでも実行できます）。

### 出力の分析

[!DNL Upgrade Compatibility Tool]は、影響を受けるコードまたはモジュール、重大度、問題が発生するたびに問題の説明を識別するJSON ファイルを書き出します。 また、複雑さスコア付きの要約レポートを出力し、最新バージョンにアップグレードするために必要な作業を大まかに把握できます。 複雑さのスコアが低いほど、アップグレードの実行が容易になります。

次の出力は、サマリーレポートの例を示しています。

```console
 ------------------------ --------
  Installed version        2.4.2
  Adobe Commerce version   2.4.3
  Running time             0m:48s
  Checked modules          14
  Core checked modules     0
  Core modified files      0
  % core modified files    0.00
  PHP errors found         109
  PHP warnings found       0
  GraphQL errors found     0
  GraphQL warnings found   0
  Total errors found       109
  Total warnings found     0
  Complexity score         218
 ------------------------ --------
```

### ヒントとアドバイス

ツールが特定したすべての問題は、特定のエラーコードを含むレポートに一覧表示されます。 各問題について詳しくは、[ エラーメッセージ参照](../upgrade-compatibility-tool/error-messages.md)を使用してください。 Adobeでは、修正ステップを計画できるように、各問題タイプを修正するための推奨事項も提供されています。

このレポートを使用して、アップグレード用のコードを更新するのにかかる労力を見積もります。 経験に基づいて、特定された問題の合計数と問題の重大度に基づいて、アップグレードに必要な労力を見積もることができます。 これはコマンドラインツールなので、これを自動テストおよびコードチェックスイートに組み込み、JSON出力を使用してレポートを生成できます。

今後のアップグレード結果と以前の結果を比較できるように、各アップグレードプロジェクトの結果を保存することをお勧めします。 継続的に使用することで、ツールが提供するサマリーレポートから、次のバージョンにアップグレードするのにかかる労力レベルを把握できるようになります。

また、アップグレードの作業中にツールを定期的に実行して、進捗状況を可視化することをお勧めします。 問題を解決するにつれて数が減少します。 これにより、チームは作業を配分するための最適なアプローチを決定できます。

[!DNL Upgrade Compatibility Tool]は引き続き改善され、今後のリリースには、可能な限り迅速に問題を修正するのに役立つオートフィックスなどの機能が含まれます。 2022年1月にリリースされた最新の機能強化には、PHP 8.1互換性テストとHTMLのビジュアライゼーション機能が含まれており、アップグレードに多くの労力が必要な領域をすばやく特定するのに役立ちます。
