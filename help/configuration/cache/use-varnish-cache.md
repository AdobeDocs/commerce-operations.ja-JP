---
title: Varnish によるキャッシュのクリア
description: キャッシュクリアが Varnish でどのように機能するか、およびAdobe Commerce アプリケーションの web キャッシュアクセラレーターとして使用する方法について説明します。
feature: Configuration, Cache
exl-id: 866da415-c428-4092-a045-c3079493cdc4
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# Varnish によるキャッシュのクリア

ここでは、Adobe Commerceの web キャッシングアクセラレーターとして Varnish を使用する際の基本について説明します。

## ワニスパージ

基準： [Varnish ドキュメント](https://www.varnish-cache.org/docs/trunk/users-guide/purging.html), &quot;A *消去* は、キャッシュからオブジェクトを選択し、そのバリアントと一緒に破棄する場合に発生します。」 Varnish パージは、キャッシュの消去コマンド（またはクリック）に似ています **Magentoキャッシュのフラッシュ** （管理者で）。

実際、Commerceのキャッシュをクリーンアップ、フラッシュまたは更新すると、Varnish もパージします。

Commerceと連携するようにワニスをインストールして設定したら、次の操作を行うとワニスのパージが発生する場合があります。

- Web サイトの管理。

  例えば、次の場所の管理者で行うこと：

   - **ストア** > **設定** > **設定** > 一般 > **一般**
   - **ストア** > **設定** > **設定** > 一般 > **通貨設定**
   - **ストア** > **設定** > **設定** > 一般 > **メールアドレスの保存**

  Commerceがそのような変更を検出すると、キャッシュを更新するように求めるメッセージが表示されます。

- ストアの維持（カテゴリ、価格、製品、プロモーション価格ルールの追加や編集など）。

  これらのタスクを実行すると、ワニスは自動的にパージされます。

- ソースコードの管理。

  キャッシュを更新し、内のすべてを定期的に削除する必要があります `generated/code` および `generated/metadata` ディレクトリ。 キャッシュの更新については、次の節を参照してください。

## Commerceでワニスをパージするように設定する

Commerceでは、を使用して Varnish ホストを設定した後、Varnish ホストをパージします。 [`magento setup:config:set`](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#setupconfigset) コマンド。

オプションのパラメーターを使用できます `--http-cache-hosts` パラメーター：Varnish ホストとリッスンポートのコンマ区切りリストを指定します。 1 つまたは複数の Varnish ホストをすべて設定します。 （ホストをスペース文字で区切らないでください）。

パラメーターの形式は、 `<hostname or ip>:<listen port>`。を省略できます `<listen port>` ポート 80 の場合。

以下に例を挙げます。

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:6081
```

その後、Commerceのキャッシュ（ *クリーニング* キャッシュ）を使用するか、コマンドラインを使用します。

管理者を使用してキャッシュを更新するには、 **[!UICONTROL SYSTEM]** > ツール > **キャッシュ管理**&#x200B;を選択し、 **Magentoキャッシュのフラッシュ** ページの上部 （個々のキャッシュタイプを更新することもできます）。

コマンドラインを使用してキャッシュを更新するには、通常、 [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) としてコマンド [ファイルシステム所有者](../../installation/prerequisites/file-system/overview.md).
