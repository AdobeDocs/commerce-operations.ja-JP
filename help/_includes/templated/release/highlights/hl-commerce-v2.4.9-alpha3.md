---
source-git-commit: dbb758dd76fd9ea2f2e2e64fb87ea03d1c426263
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---
# Adobe Commerce リリースノート（v2.4.9-alpha3）

## v2.4.9-alpha3 のハイライト

Adobe Commerce 2.4.9-alpha3 リリースには、次のハイライトが適用されます。

### Braintree

#### アカウントエリアを介したGoogle Pay のヴォールティング

Magento 2.4.9-alpha3 では、BraintreeでGoogle Pay Vault が有効になっている場合、お客様はアカウント領域を通じてGoogle Pay カードをヴォールティングできるようになりました。 保管されたカードは、保管された支払い方法の下に表示され、チェックアウト時に今後の購入に使用でき、顧客が削除できます。 これにより、Cards と PayPal だけでなく、Google Pay にもヴォールティングのサポートが広がります。

_バンドル–3459_

#### Magento注文をBraintree Portal 注文にリンク

Magento 2.4.9-alpha3 で、Magento管理者の注文の詳細にBraintree ポータルリンクが追加されました。 リンクをクリックすると、関連する取引がBraintree ポータルで（新しいタブで）開き、Magento注文のマーチャント ID と取引 ID が使用されます。 これにより、両方のシステムに別々にログインすることなく、直接クロスリファレンスが可能になります。

_バンドル–3461_

#### リアルタイムアカウントアップデーター（RTAU）

Braintree用Magento 2.4.9-alpha3 のリアルタイムアカウントアップデーター（RTAU）機能により、カードの有効期限が切れたりカードが交換されたりすると、ヴォールティングされた Visa、Mastercard、Discover のカード詳細が自動的に更新されます。 これにより、支払い失敗を最小限に抑え、Magento Vault を最新の状態に保ち、サポートされていないタイプ（前払い、Apple Pay、Google Pay）は誤りなくスキップできます。

_バンドル–3462_

#### Braintreeカード支払いに対する ELO カードのタイプのサポート

Magento 2.4.9-alpha3 で、ELO カードタイプのサポートがBraintree Payments に追加されました。 管理者はクレジットカード設定で ELO を有効にできるようになりました。お客様はチェックアウト時に ELO カードを使用して注文を正常に行え、Braintreeを通じてシームレスな取引を確実に行うことができます。

_バンドル–3464_

### フレームワーク

#### RabbitMQ から Apache ActiveMQ への移行

_AC-14558_

#### chart.js の依存関係を最新バージョンにアップグレード

chart.js 依存関係が最新バージョン 4.5.0 にアップグレードされます

_AC-15133 - [GitHub コードの投稿 &#x200B;](https://github.com/magento/magento2/commit/657f983e)_

#### Laminas MVC からの移行

Adobe Commerceは、PHP 8.5 以降の長期にわたる互換性と安定性を確保するために、従来の Laminas MVC に代わるネイティブの MVC 実装を導入しました。この変更により、パフォーマンスが強化され、外部への依存が軽減され、Commerceの将来に備えた基盤が提供されます

_AC-15160_

### セキュリティ

セキュリティのバグ修正の最新情報については、[Adobe セキュリティ速報 APSB25-94](https://helpx.adobe.com/security/products/magento/apsb25-94.html) を参照してください。

{{$include /help/_includes/release-notes/highlights/security-2025-10.md}}
