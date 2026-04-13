---
source-git-commit: 0715ed3ba063b24cc7b74ec0402f3282175aad84
workflow-type: tm+mt
source-wordcount: '1692'
ht-degree: 1%

---
# 新しいテンプレート

## 最新情報

このページには、過去60日間に行われた変更が含まれます。 コピー編集などのマイナーな更新は、このリストから除外されます。

### 2026年4月8日（PT）

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>説明</th>
      <th>タイプ</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>リリース別のCommerce on CloudでサポートされているNew Relic（APM）のバージョンで<a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/installation-guide/system-requirements">必要システム構成</a>を更新しました。</p>
</td>
      <td>
        技術的、フィードバック
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/f82d05cf0f7d2749b313ef5f7e89e1e36248bf30">コミット</a></td>
    </tr>
    <tr>
      <td><p>SaaS プロジェクト用のカテゴリマーチャンダイジング （パブリックBeta）プログラムを<a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/release/beta">Beta リリース </a>に更新しました。これには、<a href="https://experienceleague.adobe.com/ja/docs/commerce/optimizer/merchandising/rules/add"> カテゴリマーチャンダイジング </a>および関連するマーチャンダイジングルールのトピックへのリンクが含まれます。</p>
</td>
      <td>
        メジャーアップデート
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/a9f3594a0ccf4326b0541a4f2b07fdf49cde7148">コミット</a></td>
    </tr>
  </tbody>
</table>

### 2026年4月3日（PT）

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>説明</th>
      <th>タイプ</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>キャッシュファイルが目的の場所に保存され、分割キャッシュディレクトリとGlusterFS セグメンテーションエラーを防ぐために、Adobe CommerceのデフォルトのL2 キャッシュディレクトリを<code class="language-plaintext highlighter-rouge">env.php</code>で適切に上書きする手順を追加しました。 更新されたガイダンスについては、<a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/implementation-playbook/best-practices/planning/redis-service-configuration">RedisおよびValkey サービス設定のベストプラクティス </a>を参照してください。</p>
</td>
      <td>
        技術的、フィードバック
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/c3030226d7832b17c82be375431795cba44d72f9">コミット</a></td>
    </tr>
  </tbody>
</table>

### 2026年4月1日（PT）

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>説明</th>
      <th>タイプ</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>最新のリリース情報で<a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/release/planning/schedule">2026 Adobe Commerce リリースカレンダー</a>を更新しました。</p>
</td>
      <td>
        リリースノート
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/3f32d342cbdc3e962fede45de828d836c242bc9a">コミット</a></td>
    </tr>
    <tr>
      <td><p>RedisおよびValkey設定<a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/implementation-playbook/best-practices/planning/redis-valkey-service-configuration">の</a> ベストプラクティスを更新し、関連する設定ガイダンスを提供しました。</p>
</td>
      <td>
        技術的、フィードバック
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/c96e5b397a2ffee8fadaf638e721799b40d320d3">コミット</a></td>
    </tr>
  </tbody>
</table>

### 2026年3月19日（PT）

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>説明</th>
      <th>タイプ</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69319">ACSD-69319のQPT 1.1.76修正に関する詳細な説明を追加しました。子製品がカスタムソースの下に在庫を持っていた場合、バンドル価格が適切にインデックス化されませんでした</a>。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/7646d46e37385cf0a2bfbee6de82410ca54629a1">コミット</a></td>
    </tr>
  </tbody>
</table>

### 2026年3月18日（PT）

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>説明</th>
      <th>タイプ</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69086">ACSD-69086のQPT 1.1.76修正に関する詳細な説明を追加しました。サポートされていないデータベース バージョン チェック </a>により、MariaDB 10.11でインストールが失敗しました。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/016d24d990492d009677c218b253ae88c21634e6">コミット</a></td>
    </tr>
  </tbody>
</table>

### 2026年3月17日（PT）

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>説明</th>
      <th>タイプ</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69331">ACSD-69331のQPT 1.1.76修正に関する詳細な説明を追加しました：メディアギャラリーのコンテンツ作成者は、<code class="language-plaintext highlighter-rouge">create_folder</code>権限のみを持つフォルダーを作成できませんでした。 修正後、期待どおりにフォルダーを作成できます</a>。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/40a14de0a67a0c373dcbb497f1893a98322435b3">コミット</a></td>
    </tr>
  </tbody>
</table>

### 2026年3月13日（PT）

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>説明</th>
      <th>タイプ</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/installation-guide/system-requirements">必要システム構成</a>を更新しました：Elasticsearchをv2.4.8のテクノロジースタックテーブルに追加しました。</p>
</td>
      <td>
        テクニカル
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/a9fe1555d9c9d5b27d8fb7fe23a312e8f124d94c">コミット</a></td>
    </tr>
  </tbody>
</table>

### 2026年3月12日（PT）

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>説明</th>
      <th>タイプ</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-68759">ACSD-68759のQPT 1.1.77修正に関する詳細な説明を追加しました。生年月日が表示されている場合にアラビア語ロケールで顧客アカウント作成エラーが発生する</a>。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/d3c2d0ebea67fb376a43a67995f3ce278ceac3ee">コミット</a></td>
    </tr>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69237">ACSD-69237: Sales__async_insert cron jobs process only 100 entries per run</a>のQPT 1.1.77修正の詳細な説明を追加しました。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/0842ba414e45857e36d61c589687718435739efa">コミット</a></td>
    </tr>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69203">ACSD-69203：製品リストウィジェットのQPT 1.1.76修正に関する詳細な説明を追加しました。カテゴリ条件</a>で複数のカテゴリを使用すると、製品リストウィジェットが誤った結果を返します。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/1c435f9cef082a01dbcc160443291e6b7655f009">コミット</a></td>
    </tr>
  </tbody>
</table>

### 2026年3月11日（PT）

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>説明</th>
      <th>タイプ</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69115">ACSD-69115のQPT 1.1.76修正に関する詳細な説明を追加しました：デフォルト以外のweb サイトに割り当てられている顧客の管理者ユーザーにショッピングカートエラーが表示されない</a>。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/9441537126c958bfcc6485e627cbad7efd16128e">コミット</a></td>
    </tr>
    <tr>
      <td><p>QPT 1.1.77の修正に関する詳細な説明を<a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69016">ACSD-69016に追加しました。タイムゾーンが異なるweb サイトでは特別価格は適用されません</a>。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/b9788fef5bab2eb33334ef9f62bb52fa7b9f243e">コミット</a></td>
    </tr>
    <tr>
      <td><p>更新された<a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/installation-guide/system-requirements">必要システム構成</a>: MariaDB 10.6は、2.4.5-p16で引き続きサポートされています。</p>
</td>
      <td>
        テクニカル
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.ja-JP/pull/173">プルリクエスト</a></td>
    </tr>
  </tbody>
</table>

### 2026年3月10日（PT）

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>説明</th>
      <th>タイプ</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>「<a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69351">ACSD-69351: ギフトカードの残高と有効期限が誤ったweb サイトに表示される</a>」に対するQPT 1.1.77修正の詳細な説明を追加しました。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/092972cf6a0689b886e1729bb195bfc9cea7cb07">コミット</a></td>
    </tr>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-67370">ACSD-67370のQPT 1.1.76修正に関する詳細な説明を追加しました：PDP/PLPのバンドル商品と複数通貨ストアのカートページに誤った価格が表示されました</a>。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/6be4fb9868ce348b9d7ab911b501807c2e9603a5">コミット</a></td>
    </tr>
    <tr>
      <td><p>セキュリティパッチリリースノート（2.4.4、2.4.5、2.4.6、2.4.7）を更新し、<a href="https://helpx.adobe.com/jp/security/products/magento/apsb26-05.html">Adobe セキュリティ情報APSB26-05</a>を参照しました：<a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/release/notes/security-patches/2-4-4-patches">2.4.4 パッチ </a>、<a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/release/notes/security-patches/2-4-5-patches">2.4.5 パッチ </a>、<a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/release/notes/security-patches/2-4-6-patches">2.4.6 パッチ </a>、および<a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/release/notes/security-patches/2-4-7-patches">2.4.7 パッチ </a>。</p>
</td>
      <td>
        テクニカル
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/aca7de52b79acd844950e792430937795bd23eba">コミット</a></td>
    </tr>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/cli-reference/uct">互換性ツール CLI リファレンス </a>をバージョン 3.0.26に更新しました：<code class="language-plaintext highlighter-rouge">dbschema:diff</code>と<code class="language-plaintext highlighter-rouge">upgrade:check</code>の修正されたコマンド例と使用可能なバージョンのリスト。</p>
</td>
      <td>
        テクニカル
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/4fa8705ac5d11e6baf2e9fe250e4fc87a1327116">コミット</a></td>
    </tr>
    <tr>
      <td><p>3月26日リリース：<br />- <a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/release/notes/adobe-commerce/2-4-9">Adobe Commerce 2.4.9-beta1 リリースノート </a>にハイライトを追加し、リリースに含まれる重要な更新をまとめました。<br />- オンプレミスのお客様に2026年4月30日（PT）より前に互換性のあるMariaDB バージョンに移行するようアドバイスする、<a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/release/notes/security-patches/2-4-5-patches">2.4.5</a>、<a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/release/notes/security-patches/2-4-6-patches">2.4.6</a>、<a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/release/notes/security-patches/2-4-7-patches">2.4.7</a>のセキュリティパッチリリースノートにMySQL 8.0 サポート終了（EOS）通知を追加しました。<br /> – 文書化された<a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/release/notes/security-patches/2-4-4-patches#p17">2.4.4-p17</a> セキュリティ パッチ リリース。<br />- 2.4.9-beta1 オンプレミス CLIで使用可能なすべてのコマンド、引数、およびオプションを文書化する<a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/cli-reference/commerce-on-premises-beta">bin/magento （Adobe Commerce オンプレミス 2.4.9-beta1） </a>CLI リファレンスを追加しました。<br /> – 新しいパッチバージョンとハイライトを含むセキュリティパッチリリースノートが更新されました：<a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/release/notes/security-patches/2-4-5-patches">2.4.5-p16</a>、<a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/release/notes/security-patches/2-4-6-patches">2.4.6-p14</a>、<a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/release/notes/security-patches/2-4-7-patches">2.4.7-p9</a>、および<a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/release/notes/security-patches/2-4-8-patches">2.4.8-p4</a>。<br />- Adobe Commerce 2.4.9 beta1 （アルファ列を2.4.9-beta1に置き換える）、更新された依存関係バージョン（PHP 8.5/8.4、ActiveMQ Artemis、AWS サービス）の<a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/installation-guide/system-requirements">必要システム構成</a>を更新し、パッチバージョン 2.4.8-p4、2.4.7-p9、2.4.6-p14、2.4.5-p16、および2.4.4-p17を追加しました。<br />- ベータ版の修正された問題を含む<a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/release/notes/adobe-commerce/2-4-9">Adobe Commerce 2.4.9-beta1 リリースノート </a>と<a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/release/notes/magento-open-source/2-4-9">Magento Open Source 2.4.9-beta1 リリースノート </a>を更新しました。<br />- フレームワークの更新（OpenSearch 3.x、Valkey 8.x、ActiveMQ、Composer、PHP 8.5）、セキュリティとACLの改善、配送（USPS、DHL）、Braintreeの機能強化、その他2.4.9-beta1の変更など、ベータ 1のハイライトを含む<a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/release/notes/adobe-commerce/2-4-9">Adobe Commerce 2.4.9-beta1 リリースノート </a>および<a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/release/notes/magento-open-source/2-4-9">Magento Open Source 2.4.9-beta1 リリースノート </a>を更新しました。</p>
</td>
      <td>
        メジャーアップデート
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/e4cec53679d038d2324f89478c5495de98a29fb3">コミット</a></td>
    </tr>
    <tr>
      <td><p>2026年3月リリース以降、<a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/release/versions"> リリース済みバージョン </a>を更新しました。</p>
</td>
      <td>
        テクニカル
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/9bc44a3ec7199ccb08927caf3d7904611cc7b167">コミット</a></td>
    </tr>
  </tbody>
</table>

### 2026年3月9日（PT）

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>説明</th>
      <th>タイプ</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-67091">ACSD-67091のQPT 1.1.76修正に関する詳細な説明を追加しました：カタログ ルール製品インデックスのクリーンアップは、大量の削除中に書き込みセットのサイズが最大になるため失敗します</a>。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/520273fb4c1b30e3f8b346f7079062cf9c8b37f3">コミット</a></td>
    </tr>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69261">ACSD-69261のQPT 1.1.76修正に関する詳細な説明を追加しました。部分的な請求書と解約フローで誤ったtimes_used処理が行われたため、1回限りのカート クーポンが再利用されました</a>。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/536364742e2102f8386b3e13503cf2965821f04b">コミット</a></td>
    </tr>
  </tbody>
</table>

### 2026年3月6日（PT）

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>説明</th>
      <th>タイプ</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69541">ACSD-69541のQPT 1.1.76修正に関する詳細な説明を追加しました。管理画面の商品の数量を、カートに既に存在する数量よりも少なくすると、GraphQL</a>を介してカート内の商品の数量を編集することが不可能になりました。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/b2b801b88aee7fc6c275be3fb32a2e75bbe6f20d">コミット</a></td>
    </tr>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69308">ACSD-69308のQPT 1.1.76修正に関する詳細な説明を追加しました。<code class="language-plaintext highlighter-rouge">special_price</code>がweb サイトレベルでのみ設定された場合（「すべてのストアビュー」ではなく）、カタログの価格規則は適用されませんでした。 修正後、web サイトの既定のストアを最初に確認することにより、カタログ価格ルールが正しく適用されます</a>。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/db07a5d6f991ff36536a4365ee88fa25062dbe43">コミット</a></td>
    </tr>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69020">ACSD-69020のQPT 1.1.77修正に関する詳細な説明を追加しました。子製品がフィルター</a>に一致すると、設定可能な製品がページビルダーカルーセルに表示されます。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/5ce526100a22243b91f75b8a52690e529b64b152">コミット</a></td>
    </tr>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69325">ACSD-69325のQPT 1.1.76修正に関する詳細な説明を追加しました：SKU ケースを変更すると、ストアフロント </a>で商品が在庫切れとして表示されます。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/bceda2e729082e0dc81f7eb81838ca5c5049342d">コミット</a></td>
    </tr>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/release/beta">Beta リリース </a>を更新し、2つの新しいパブリックベータ版プログラムが追加されました。グローバルおよびカタログビューごとのマーチャンダイジングルール、グローバルおよびカタログビューごとの商品レコメンデーションです。</p>
</td>
      <td>
        メジャーアップデート
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/5533640a3f0f648162ebfc3609eb4e35fd32f6d7">コミット</a></td>
    </tr>
  </tbody>
</table>

### 2026年3月5日（PT）

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>説明</th>
      <th>タイプ</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69129">ACSD-69129のQPT 1.1.76修正に関する詳細な説明を追加しました。デフォルトの基本web サイトを削除し、セカンダリ web サイトをデフォルト </a>として使用すると、REST API層の価格の更新が失敗します。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/06d33e9ed08e079365ac6ae6087e4bdf30bbf45e">コミット</a></td>
    </tr>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-68410">ACSD-68410のQPT 1.1.76修正に関する詳細な説明を追加しました。交渉可能な見積もりチェックアウトには、意図しないショッピングカート項目が含まれています</a>。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/123a0b7c2335fd27d6c8fabbb8a6520af2ac0c76">コミット</a></td>
    </tr>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-68892">ACSD-68892: キャッシュ可能なページに対するFastlyのキャッシュ動作に一貫性がないというQPT 1.1.77の修正に関する詳細な説明を追加しました</a>。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/d727bea23f1a60b597bb795948eb924e76e869a5">コミット</a></td>
    </tr>
  </tbody>
</table>

### 2026年3月3日（PT）

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>説明</th>
      <th>タイプ</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-63687">ACSD-63687のQPT 1.1.77修正に関する詳細な説明を追加しました。Redis キャッシュのクリーンアップの問題</a>が原因で、誤った価格が表示されます。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/e8a9b37a61119e7604461c83f135a282b15a93ef">コミット</a></td>
    </tr>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-68664">ACSD-68664のQPT 1.1.77修正に関する詳細な説明を追加しました。スケジュールされた更新プレビューで、カスタムストアドメイン </a>にエラーがあります。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/d0a57180c224fc7d1eba3e4e5b87a87ddb11d88c">コミット</a></td>
    </tr>
  </tbody>
</table>

### 2026年3月2日（PT）

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>説明</th>
      <th>タイプ</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/acsd-69333">ACSD-69333のQPT 1.1.76修正に関する詳細な説明を追加しました。アクティブなスケジュール済み更新プログラム </a>を含む製品に対して許可されるSKUの変更。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/b9ea11e00223a3c4a4cd5be1eca1a3175074124c">コミット</a></td>
    </tr>
  </tbody>
</table>

### 2026年2月27日（PT）

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>説明</th>
      <th>タイプ</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>QPT 1.1.77の<a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69311">ACSD-69311の修正に関する詳細な説明を追加しました：請求書からの一部返金後のクレジットメモの誤った税計算</a>。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/c6d81e7aeb4e2b4d2d5a140e9bf7b8c8ba5f5deb">コミット</a></td>
    </tr>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69494">ACSD-69494のQPT 1.1.77の修正に関する詳細な説明を追加しました：is_onlineを使用した非同期の返金要求がオンラインの返金をトリガーしません</a>。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/29a5f90122336bde78ed00e778b43b7c56549eef">コミット</a></td>
    </tr>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-68537">ACSD-68537のQPT 1.1.77修正に関する詳細な説明を追加しました：チェックアウトのパフォーマンスが多くの顧客セグメントで低下します</a>。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/70729169b3588f5061f98b555577c2b62215e6f0">コミット</a></td>
    </tr>
  </tbody>
</table>

### 2026年2月26日（PT）

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>説明</th>
      <th>タイプ</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-68341">ACSD-68341のQPT 1.1.77修正に関する詳細な説明を追加しました：PDPの読み込み時に複数のX-Magento-Vary Cookieの更新が行われます</a>。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/88ae7472fc5ec3c7b422a9a1d568204c42e017bb">コミット</a></td>
    </tr>
  </tbody>
</table>

### 2026年2月20日（PT）

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>説明</th>
      <th>タイプ</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/overview">概要：品質パッチツール （QPT） v1.1.77</a>を追加しました。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/09c026905c464ec0e41d12db8a5822b3e3b57064">コミット</a></td>
    </tr>
  </tbody>
</table>

### 2026年2月14日（PT）

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>説明</th>
      <th>タイプ</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-75/acsd-68359">ACSD-68359のQPT 1.1.75修正に関する詳細な説明を追加しました。大きな買い物かごを持つ店舗でピッキングを選択する際の414 エラーを修正しました</a>。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/33348fa893265e14d9e2cec9f30ffd6cf42b0878">コミット</a></td>
    </tr>
  </tbody>
</table>

### 2026年2月13日（PT）

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>説明</th>
      <th>タイプ</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>QPT 1.1.75の<a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-75/acsd-68517">ACSD-68517の修正に関する詳細な説明を追加しました：カタログおよびカタログ検索ページ </a>でフォーム再送信エラーが修正されました。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/3b3f33eda0f87829f97a875ec9805c6e257d9b09">コミット</a></td>
    </tr>
  </tbody>
</table>

### 2026年2月12日（PT）

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>説明</th>
      <th>タイプ</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p>現在のリリースガイドラインとタイムラインを明確にするために、<a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/release/planning/schedule"> パッチリリーススケジュール </a>を更新しました。</p>
</td>
      <td>
        技術的、フィードバック
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/8ee6404271170b19ff27a3ab64711061505494b3">コミット</a></td>
    </tr>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-76/overview">概要：品質パッチツール （QPT） v1.1.76</a>を追加しました。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/6e7e67291cabb1a35b132e3ae2d407e2ffefe7f1">コミット</a></td>
    </tr>
  </tbody>
</table>

### 2026年2月11日（PT）

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>説明</th>
      <th>タイプ</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-75/acsd-68573">ACSD-68573のQPT 1.1.75修正に関する詳細な説明を追加しました：カテゴリ権限が顧客のウィッシュリスト項目に正しく適用されませんでした。 修正後、ウィッシュリスト項目が適切に表示され、webとGraphQL</a>の両方でページ分けされます。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/19e5faea683395375efefe6fc57e0897392ef354">コミット</a></td>
    </tr>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-75/acsd-68793">ACSD-68793のQPT 1.1.75修正に関する詳細な説明を追加しました。有効な製品を共有カタログに割り当てる際に、誤って拒否されました</a>。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/bbd18afc87f16777b6218cdcf7ec0798c1640083">コミット</a></td>
    </tr>
  </tbody>
</table>

### 2026年2月10日（PT）

<table style="table-layout:auto;">
  <thead>
    <tr>
      <th>説明</th>
      <th>タイプ</th>
      <th>Source</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-75/acsd-68925">ACSD-68925のQPT 1.1.75修正に関する詳細な説明を追加しました：GraphQL リクエストのレスポンスが、HTTP仕様を通じてGraphQLと連携するようになりました。 リクエストを解析できない、不正な場合、または一般的な問題が発生した場合は、4XX応答コードが返されます。 リクエストが解析された場合</a>。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/210a5038743bec986807d7dff5db31d74670461e">コミット</a></td>
    </tr>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-75/acsd-68289">ACSD-68289のQPT 1.1.75修正に関する詳細な説明を追加しました。フルテキスト検索では、検索可能なすべてのフィールドで最低一致条件が満たされた場合、1つのフィールド </a>で条件を満たすことを要求するのではなく、一致する製品を返すようになりました。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/d26429ef5b2dee650e14914d3b9678895a23f73e">コミット</a></td>
    </tr>
  </tbody>
</table>
