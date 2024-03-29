---
title: モジュールの有効化または無効化
description: 以下の手順に従って、Adobe CommerceまたはMagento Open Sourceモジュールを管理します。
exl-id: 7155950a-a66a-4254-a71c-1a9aeab47606
source-git-commit: 6e87d68df97adf47b5a61e8b6683ac11f600806c
workflow-type: tm+mt
source-wordcount: '584'
ht-degree: 0%

---

# モジュールの有効化または無効化

このコマンドには前提条件はありません。

## モジュールのステータス

次のコマンドを使用して、有効なモジュールと無効なモジュールを一覧表示します。

```bash
bin/magento module:status [--enabled] [--disabled] <module-list>
```

ここで、

* `--enabled` は、すべての有効なモジュールを一覧表示します。
* `--disabled` 無効になっているすべてのモジュールの一覧を表示します。
* `<module-list>` は、ステータスを確認するためのモジュールのスペースで区切られたリストです。 モジュール名に特殊文字が含まれる場合は、名前を一重引用符または二重引用符で囲みます。

>[!NOTE]
>
>クラウドプロジェクトで直接モジュールを有効または無効にすることはできません。 これらのコマンドをローカルで実行し、変更を `app/etc/config.php` ファイルを作成します。 詳しくは、 [プロジェクトワークフロー：デプロイメントワークフロー](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow.html#deployment-workflow).

## モジュールの有効化、無効化

使用可能なモジュールを有効または無効にするには、次のコマンドを使用します。

```bash
bin/magento module:enable [-c|--clear-static-content] [-f|--force] [--all] <module-list>
```

```bash
bin/magento module:disable [-c|--clear-static-content] [-f|--force] [--all] <module-list>
```

ここで、

* `<module-list>` は、有効または無効にするモジュールのスペース区切りリストです。 モジュール名に特殊文字が含まれる場合は、名前を一重引用符または二重引用符で囲みます。
* `--all` ：すべてのモジュールを同時に有効または無効にします。
* `-f` または `--force` 依存関係に関わらず、モジュールを強制的に有効または無効にする場合。 このオプションを使用する前に、 [モジュールの有効化と無効化について](#about-enabling-and-disabling-modules).
* `-c` または `--clear-static-content` クリーン [生成された静的ビューファイル](../../configuration/cli/static-view-file-deployment.md).

  静的表示ファイルをクリアしないと、同じ名前のファイルが複数存在し、すべてをクリアしない場合、問題が発生する可能性があります。

  つまり、 [静的ファイルフォールバック](../../configuration/cli/static-view-file-deployment.md) ルール：静的ファイルをクリアせず、名前を付けた複数のファイルが存在する場合 `logo.svg` 異なる場合は、フォールバックによって誤ったファイルが表示される可能性があります。

例えば、 `Magento_Weee` モジュール、次を入力します。

```bash
bin/magento module:disable Magento_Weee
```

モジュールの有効化と無効化については、 [モジュールの有効化と無効化について](#about-enabling-and-disabling-modules).

## データベースを更新

1 つ以上のモジュールを有効にした場合は、次のコマンドを実行してデータベースを更新します。

```bash
bin/magento setup:upgrade
```

次に、キャッシュをクリーンアップします。

```bash
bin/magento cache:clean
```

## モジュールの有効化と無効化について

Adobe CommerceとMagento Open Sourceでは、現在使用可能なモジュール (Adobeが提供するモジュール、または現在使用可能なサードパーティのモジュール ) を有効または無効にすることができます。

特定のモジュールは他のモジュールに依存しています。その場合、他のモジュールに依存しているので、モジュールを有効または無効にできない可能性があります。

さらに、 *競合* 両方を同時に有効にできないモジュール。

例：

* モジュール A はモジュール B に依存します。最初にモジュール A を無効にしない限り、モジュール B を無効にすることはできません。

* モジュール A はモジュール B に依存し、どちらも無効です。 モジュール A を有効にする前に、モジュール B を有効にする必要があります。

* モジュール A はモジュール B と競合します。モジュール A とモジュール B を無効にするか、どちらかのモジュールを無効にすることができますが、 *できません* モジュール A とモジュール B を同時に有効にします。

* 依存関係は `require` Adobe CommerceとMagento Open Sourceのフィールド `composer.json` ファイルを作成します。 競合は `conflict` モジュールのフィールド `composer.json` ファイル。 この情報を使用して、依存関係グラフを作成します。 `A->B` とは、モジュール A がモジュール B に依存することを意味します。

* A *依存鎖* は、モジュールから別のモジュールへのパスです。 例えば、モジュール A がモジュール B に依存し、モジュール B がモジュール C に依存する場合、依存関係チェーンは `A->B->C`.

他のモジュールに依存するモジュールを有効または無効にしようとすると、エラーメッセージに依存関係グラフが表示されます。

>[!NOTE]
>
>そのモジュール A の可能性があります。 `composer.json` モジュール B との競合を宣言するが、逆には宣言しない。

*コマンドラインのみ：* モジュールの依存関係に関係なく、モジュールを強制的に有効または無効にするには、オプションの `--force` 引数。

>[!NOTE]
>
>使用 `--force` はストアを無効にし、管理者へのアクセスに問題を引き起こす可能性があります。
