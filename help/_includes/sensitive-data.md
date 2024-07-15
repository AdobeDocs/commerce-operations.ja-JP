---
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '64'
ht-degree: 1%

---
# 機密データ

Adobe Commerceでは、暗号化キーを使用して以下を暗号化します。

* クレジットカード情報
* 管理者設定で指定されたユーザー名とパスワード （例：支払いゲートウェイへのログイン）
* ネットワーク経由で送信される CAPTCHA 値

Adobe Commerceは暗号化 *ません*

* 管理者および顧客のユーザー名とパスワード（これらのパスワードはハッシュ化されます）
* アドレス
* 電話番号
* クレジットカード番号を除く、他のタイプの個人を特定できる情報
