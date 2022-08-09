---
title: Vanish を使用したキャッシュの消去
description: キャッシュの消去が Vanrish と連携する仕組みと、それをAdobe Commerceアプリケーションの Web キャッシュアクセラレーターとして使用する方法を説明します。
source-git-commit: c65c065c5f9ac2847caa8898535afdacf089006a
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---


# Vanish を使用したキャッシュの消去

このトピックでは、Adobe CommerceとMagento Open Sourceの Web キャッシュアクセラレーターとして Vanrish を使用する際の基本について説明します。

## ワニスのパージ

基準 [Vanish 文書](https://www.varnish-cache.org/docs/trunk/users-guide/purging.html)「A」 *パージ* は、 [キャッシュ](https://glossary.magento.com/cache) それを変種と一緒に捨てなさい」 ワニスのパージは、キャッシュのクリーンコマンド ( または **フラッシュMagentoキャッシュ** （管理者）。

実際、Commerce キャッシュをクリーンアップ、フラッシュ、または更新すると、Vanish も削除されます。

Commerce と連携するように Vanrish をインストールして設定した後、次の操作を行うと、Varnish がパージされる場合があります。

- の保守 [web サイト](https://glossary.magento.com/website).

   例えば、次の場所の管理者でおこなった操作の例です。

   - **ストア** > **設定** > **設定** /一般 > **一般**
   - **ストア** > **設定** > **設定** /一般 > **通貨の設定**
   - **ストア** > **設定** > **設定** /一般 > **メールアドレスを保存**

   Commerce がそのような変更を検出すると、キャッシュを更新するよう通知するメッセージが表示されます。

- 店舗の保守（例えば、カテゴリ、価格、製品、プロモーションの価格ルールの追加や編集）。

   ワニスは、次のタスクを実行すると自動的にパージされます。

- ソースコードの保守。

   キャッシュを更新し、定期的に `generated/code` および `generated/metadata` ディレクトリ。 キャッシュの更新について詳しくは、次の節を参照してください。

## Vanish をパージするように Commerce を設定

Commerce は、Vanish ホストを [`magento setup:config:set`](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#setupconfigset) コマンドを使用します。

オプションのパラメーター `--http-cache-hosts` Vanish ホストとリッスンポートのコンマ区切りリストを指定するためのパラメータ。 Vanish ホストを 1 つでも複数でも構成します。 （ホストをスペース文字で区切らないでください）。

パラメーターの形式は、 `<hostname or ip>:<listen port>`を指定し、 `<listen port>` ポート 80 の場合。

以下に例を挙げます。

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:6081
```

その後、コマースキャッシュを更新すると、Vanish ホストをパージできます ( *クリーニング* キャッシュ ) を管理者またはコマンドラインで使用します。

管理者を使用してキャッシュを更新するには、 **[!UICONTROL SYSTEM]** /ツール/ **キャッシュ管理**&#x200B;を選択し、「 **フラッシュMagentoキャッシュ** をクリックします。 （個々のキャッシュタイプを更新することもできます）。

コマンドラインを使用してキャッシュを更新するには、通常、 [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) コマンドを [ファイルシステム所有者](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
