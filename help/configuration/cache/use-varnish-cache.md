---
title: Varnish によるキャッシュのクリア
description: キャッシュクリアが Varnish でどのように機能するか、およびAdobe Commerce アプリケーションの web キャッシュアクセラレーターとして使用する方法について説明します。
feature: Configuration, Cache
exl-id: 866da415-c428-4092-a045-c3079493cdc4
source-git-commit: 79c8a15fb9686dd26d73805e9d0fd18bb987770d
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# Varnish によるキャッシュのクリア

ここでは、Adobe Commerceの web キャッシングアクセラレーターとして Varnish を使用する際の基本について説明します。

## ワニスパージ

[Varnish のドキュメント ](https://www.varnish-cache.org/docs/trunk/users-guide/purging.html) によると、「*パージ* は、キャッシュからオブジェクトを選択して、そのバリアントと共に破棄する場合に発生します。」 Varnish パージは、キャッシュクリーンコマンド（または管理者で **Magento キャッシュをフラッシュ** をクリックするコマンド）に似ています。

実際、Commerceのキャッシュをクリーンアップ、フラッシュまたは更新すると、Varnish もパージします。

Commerceと連携するようにワニスをインストールして設定したら、次の操作を行うとワニスのパージが発生する場合があります。

- Web サイトの管理。

  例えば、次の場所の管理者で行うこと：

   - **ストア**/**設定**/**設定**/一般/**一般**
   - **ストア**/**設定**/**設定**/一般/**通貨の設定**
   - **ストア**/**設定**/**設定**/一般/**メールアドレスを保存**

  Commerceがそのような変更を検出すると、キャッシュを更新するように求めるメッセージが表示されます。

- ストアの維持（カテゴリ、価格、製品、プロモーション価格ルールの追加や編集など）。

  これらのタスクを実行すると、ワニスは自動的にパージされます。

- ソースコードの管理。

  キャッシュを更新し、`generated/code` ディレクトリと `generated/metadata` ディレクトリ内のすべてを定期的に削除する必要があります。 キャッシュの更新については、次の節を参照してください。

## Commerceでワニスをパージするように設定する

Commerceは、[`magento setup:config:set`](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/cli-reference/commerce-on-premises#setupconfigset) コマンドを使用して Varnish ホストを設定した後に、Varnish ホストをパージします。

オプションのパラメーター `--http-cache-hosts` パラメーターを使用して、Varnish ホストとリッスンポートのコンマ区切りリストを指定できます。 1 つまたは複数の Varnish ホストをすべて設定します。 （ホストをスペース文字で区切らないでください）。

パラメーターの形式は `<hostname or ip>:<listen port>` にする必要があります。ポート 80 の場合、`<listen port>` を省略できます。

以下に例を挙げます。

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:6081
```

その後、Admin またはコマンドラインでCommerce キャッシュを更新するとき（キャッシュの *クリーニング* とも呼ばれます）に、Varnish ホストをパージできます。

管理者を使用してキャッシュを更新するには、**[!UICONTROL SYSTEM]** / ツール / **キャッシュ管理** をクリックし、ページ上部の **Magento キャッシュをフラッシュ** をクリックします。 （個々のキャッシュタイプを更新することもできます）。

コマンドラインを使用してキャッシュを更新するには、通常、[`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) コマンドを [ ファイルシステムの所有者 ](../../installation/prerequisites/file-system/overview.md) として使用します。
