---
title: Security.txt
description: セキュリティ研究者が脆弱性を報告するのに役立つ情報を提供する方法について説明します。
feature: Configuration, Security
badge: label="協力：Kalpesh Mehta from Corra" type="Informative" url="https://solutionpartners.adobe.com/s/directory/detail/corra" tooltip="カルペシュ・メフタ"
exl-id: ddafd03c-77b2-42e8-b593-7d655d08e9c3
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
    internal-label: Security
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%
---
# セキュリティ TXT ファイル

セキュリティ上の脆弱性が研究者によって発見された場合、適切なレポートチャネルが不足していることがよくあります。 その結果、一部の脆弱性は報告されません。 `security.txt` [ ファイル形式](https://datatracker.ietf.org/doc/html/draft-foudil-securitytxt-09) ファイルの目的は、セキュリティ研究者が調査結果を報告するために使用できる情報を提供することです。

マーチャントは、Commerce _管理者_&#x200B;から[ セキュリティ問題レポート ](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-issue-reporting)の連絡先情報を入力できます。 開発者の場合、`Magento_Securitytxt` モジュールには次の機能が用意されています。

- セキュリティ設定を&#x200B;_管理者_&#x200B;から保存できます。
- `.well-known/security.txt`および`.well-known/security.txt.sig` ファイルへのリクエストに対するアプリケーションアクションクラスに一致するルーターが含まれています。
- `.well-known/security.txt`および`.well-known/security.txt.sig` ファイルのコンテンツを提供します。

有効な`security.txt` ファイルは次のようになります。

```text
Contact: mailto:security@example.com
Contact: tel:+1-201-555-0123
Encryption: https://example.com/pgp.asc
Acknowledgement: https://example.com/security/hall-of-fame
Policy: https://example.com/security-policy.html
Signature: https://example.com/.well-known/security.txt.sig
```

`security.txt`署名（`security.txt.sig`）ファイルを作成するには：

```shell
gpg -u KEYID --output security.txt.sig --armor --detach-sig security.txt
```

署名を検証するには：

```shell
gpg --verify security.txt.sig security.txt
```
