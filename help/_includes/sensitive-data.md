---
source-git-commit: 475dbc056ac3e6a00c8f794259bb0fbf04143687
workflow-type: tm+mt
source-wordcount: '72'
ht-degree: 0%

---
# 機密データ

Adobe CommerceとMagento Open Sourceは、暗号化キーを使用して以下を暗号化します。

* クレジットカード情報
* 管理者設定で指定されたユーザー名とパスワード（例：支払いゲートウェイへのログイン）
* ネットワーク経由で送信される CAPTCHA 値

Adobe CommerceとMagento Open Sourceド *not* 暗号化：

* 管理者および顧客のユーザー名とパスワード（これらのパスワードはハッシュ化されます）
* 住所
* 電話番号
* クレジットカード番号を除く、個人を特定できるその他のタイプの情報
