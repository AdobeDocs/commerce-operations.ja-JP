---
title: インストールの確認
description: オンプレミスのAdobe CommerceまたはMagento Open Sourceのインストールが正常に完了したことを確認するには、次の手順に従います。
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%

---


# インストールの確認

次に移動： [店頭](https://glossary.magento.com/storefront) （Web ブラウザー）を使用して、 例：インストールベース [URL](https://glossary.magento.com/url) が `http://www.example.com`を使用する場合は、ブラウザーのアドレスまたはロケーションバーに入力します。

次の図は、ストアフロントページのサンプルを示しています。 次のように表示される場合は、インストールは成功しています。

![Luma テーマを使用したストアフロント](../../assets/installation/install-success_store-luma.png)

## ストアフロントを検証します（サンプルデータがありません）

Web ブラウザーのストアフロントに移動します。 例えば、インストールベース URL が `http://www.example.com`を使用する場合は、ブラウザーのアドレスまたはロケーションバーに入力します。

次の図は、ストアフロントページのサンプルを示しています。 次のように表示される場合は、インストールは成功しています。

![インストールが成功したことを確認するストアフロント](../../assets/installation/install-success_store.png)

ページに `404 (Not Found)` エラーが発生したか、スタイルが表示されません。詳しくは、 [トラブルシューティング](https://support.magento.com/hc/en-us/articles/360032994352).

## 管理者の確認

次に移動： [管理者](https://glossary.magento.com/magento-admin) （Web ブラウザー）を使用して、 例えば、インストールベース URL が `http://www.example.com`の場合、Admin URI は `admin_au1nT`を入力して、 `http://www.example.com/admin_au1nT` をクリックします。

( [管理者](https://glossary.magento.com/admin) URI は `backend-frontname` インストールパラメータ )

プロンプトが表示されたら、管理者としてログインします。

次の図は、管理ページのサンプルを示しています。 次のように表示される場合は、インストールは成功しています。

![インストールが成功したことを確認する管理者](../../assets/installation/install_success_admin.png)

ページにスタイルが表示されない場合は、 [トラブルシューティング](https://support.magento.com/hc/en-us/articles/360032994352).

次のような 404（見つかりません）エラーが表示された場合は、 [ブラウザでAdobe Commerceにアクセスする際に PHP バージョンエラーが発生した、または 404](https://support.magento.com/hc/en-us/articles/360033117152).

`The requested URL /magento2index.php/admin/admin/dashboard/index/key/0c81957145a968b697c32a846598dc2e/ was not found on this server.`
