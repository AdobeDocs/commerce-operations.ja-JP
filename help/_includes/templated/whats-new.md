---
source-git-commit: 206f502c41b53c822cca42957d7705184f18c0ab
workflow-type: tm+mt
source-wordcount: '1282'
ht-degree: 1%
---
# 新しいテンプレート

## 最新情報

このページには、過去60日間に行われた変更が含まれます。 コピー編集などのマイナーな更新は、このリストから除外されます。

### 2026年10月2日（PT）

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
      <td><p><a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-83/overview">概要：品質パッチツール （QPT） v1.1.83</a>を追加しました。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/266c8529352dac198568dca4676aebd88ce50fc1">コミット</a></td>
    </tr>
  </tbody>
</table>

### 2026年9月18日（PT）

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
      <td><p>完全なセキュリティパッチリリース間のパッチ火曜日に、Adobe Commerceがターゲットを絞った個別CVE修正をどのように提供するか、またそれらを適用して検証する方法を説明する、<a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/release/planning/monthly-isolated-security-patches">月間個別セキュリティパッチポリシー</a>を追加しました。</p>
</td>
      <td>
        新しいトピック
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/681f7f0589aed8787aaf165d36ac00f670d751ce">コミット</a></td>
    </tr>
  </tbody>
</table>

### 2026年9月15日（PT）

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
      <td><p><a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/implementation-playbook/best-practices/planning/redis-valkey-service-configuration">Redis/Valkey サービス設定</a> ガイドを修正して、<code>VALKEY_BACKEND</code>および<code>REDIS_BACKEND</code>のデプロイ変数で、Adobe Commerceが実際に使用するキャッシュサービスが決まらないこと、および<code>VALKEY_USE_SLAVE_CONNECTION</code>/<code>REDIS_USE_SLAVE_CONNECTION</code>が実際に利用可能なサービスと一致する必要があることを確認しました。</p>
</td>
      <td>
        テクニカル
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/49781ad38a266fffa1be080b5a093327a28cf6a6">コミット</a></td>
    </tr>
  </tbody>
</table>

### 2026年9月8日（PT）

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
      <td><p>Adobe Commerce パッチオートメーションが一般公開されました。 詳しくは、<a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/caps-tool/intro"> ドキュメント </a>を参照してください。</p>
</td>
      <td>
        メジャーアップデート、新しいトピック
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/a88bfea449616c0b79c5bd3380bec74c68687052">コミット</a></td>
    </tr>
  </tbody>
</table>

### 2026年8月26日（PT）

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
      <td><p><a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4840">ACP2E-4840のQPT 1.1.82修正に関する詳細な説明を追加しました：GraphQL製品クエリは、カスタム在庫在庫の在庫商品に対してnull数量を返します</a>。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/edfc38af34925749c5acb36d2c0bcfc5d16a577a">コミット</a></td>
    </tr>
  </tbody>
</table>

### 2026年8月19日（PT）

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
      <td><p>Commerce キャッシュに関するドキュメントを更新し、オンプレミスとクラウドのガイダンスと、Symfony L2 キャッシュを使用してValkeyに移行するための新しい移行ガイダンスを更新しました：<br />- <a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/configuration-guide/cache/caching-overview"> キャッシュの概要と設定オプション </a>。<br />- <a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/configuration-guide/cache/cache-types"> キャッシュフロントエンドとタイプを更新</a>。<br />- パフォーマンス最適化のための<a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/configuration-guide/cache/cache-options"> キャッシュバックエンドオプションとストレージ参照</a>を更新しました。<br />- </a>から1&rbrace;Symfony2 キャッシュへのへのへの移行移行ガイダンスをに更新しました。<a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/configuration-guide/cache/level-two-cache">- <a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/implementation-playbook/best-practices/planning/redis-valkey-service-configuration"> クラウド固有の移行手順を使用したValkeyとRedis サービス設定</a>のベストプラクティスと、Symfony L2 キャッシュを使用したValkeyへの移行の手順。<code>RemoteSynchronizedCache</code><br /></p>
</td>
      <td>
        メジャーアップデート
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/3a840b544de95a4bb17ef49d0325b16d461aecaa">コミット</a></td>
    </tr>
  </tbody>
</table>

### 2026年8月14日（PT）

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
      <td><p>お客様がCloud UIでサービスの依存関係のバージョンを確認する方法の手順を更新し、お客様がストアのアップグレード互換性レポートを生成する方法に関するガイドのリンクを<a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/release/planning/security-enforcement-policy#action-1-verify-and-upgrade-third-party-software-dependencies"> サードパーティのソフトウェアの依存関係を確認してアップグレード </a>で更新しました。</p>
</td>
      <td>
        テクニカル
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/54ac98c35e1f161f390587601484db4e3294b6af">コミット</a></td>
    </tr>
  </tbody>
</table>

### 2026年8月13日（PT）

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
      <td><p><a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4194">ACP2E-4194のQPT 1.1.82修正に関する詳細な説明を追加しました。不明なフィルター名を持つGraphQL リクエストは、PHP例外ログ </a>を引き起こします。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/d4202395c5b7bb5e8c4a95d8fb353ec0fc523fcb">コミット</a></td>
    </tr>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4695">ACP2E-4695のQPT 1.1.82修正に関する詳細な説明を追加しました：カタログ ルール インデクサーのメモリ不足エラーは、メモリの過度の使用によって発生します</a>。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/dc891435d573c4c333e58e25b2dbe003ffa08f27">コミット</a></td>
    </tr>
    <tr>
      <td><p>Adobe Commerce 2.4.5および2.4.6 バージョンのEOSの日付のタイプミスを修正しました。</p>
</td>
      <td>
        テクニカル
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/8de65d309dcd4158627910ce5c0b87966db5c948">コミット</a></td>
    </tr>
  </tbody>
</table>

### 2026年8月12日（PT）

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
      <td><p>実稼動環境での使用は推奨されず、アップグレードの互換性のためにのみ存在するため、<a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/release/notes/adobe-commerce/2-4-9#php-and-composer">2.4.9 リリースノート </a>でサポート対象のPHP バージョンとしてPHP 8.4を削除しました。</p>
</td>
      <td>
        リリースノート、テクニカル
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/603bb70012a2f92ceeaad644d5252c4677a1a47c">コミット</a></td>
    </tr>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4894">ACP2E-4894のQPT 1.1.82修正に関する詳細な説明を追加しました。非同期インデックス作成が有効になっている場合に、新しい注文が管理注文グリッドに表示されます</a>。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/ad40d94c1618f7e423fd6a773185b8fba48c2c72">コミット</a></td>
    </tr>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4698">ACP2E-4698のQPT 1.1.82修正に関する詳細な説明を追加しました：ページビルダーテキストのインライン編集により、ポータブルディレクティブの代わりに絶対メディア URLが保存されます</a>。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/68e5e99ac0717b0e358acd6acf9934044a917a82">コミット</a></td>
    </tr>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/release/versions"> リリースバージョン </a> ページの複数のAdobe Commerce リリースラインのサポート終了、拡張サポート、その他のセキュリティ修正プロビジョニング日を修正および完了しました。</p>
</td>
      <td>
        テクニカル
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/fc5a7f7a466e6419a3e712bcbec4224f98f8c480">コミット</a></td>
    </tr>
  </tbody>
</table>

### 2026年8月11日（PT）

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
      <td><p>Adobe Commerce 2.4.4-p18 （最新）のサポート対象バージョンとしてRabbitMQ 3.13を追加するために、<a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/installation-guide/system-requirements">必要システム構成</a>を更新し、Debian OS アップグレードパスのブロッカーを解決しました。</p>
</td>
      <td>
        テクニカル
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/046d641dc45b269c6495bef0c06c53bdc500227b">コミット</a></td>
    </tr>
  </tbody>
</table>

### 2026年8月10日（PT）

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
      <td><p><a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4797">ACP2E-4797のQPT 1.1.82修正に関する詳細な説明を追加しました：utf8mb4がサポートされている場合のAdmin WYSIWYG エディターとPage Builder ブロックの4 バイト Unicode文字</a>。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/c97bb9c77eb0ec4bbc92d042cfa9fd440e970ca7">コミット</a></td>
    </tr>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4682">ACP2E-4682のQPT 1.1.82修正に関する詳細な説明を追加しました：見積もりをチェックするストアフロントページがアクティブで、空の見積もりレコードを作成しました</a>。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/ceac870e3ccb9eeee64e3b574aaccd33c6ab69d0">コミット</a></td>
    </tr>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4799">ACP2E-4799のQPT 1.1.82修正に関する詳細な説明を追加しました。GraphQL クエリ requisition_listsは、ページネーション </a>で誤ったtotal_countを返します。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/19f854db1a0ff78d0a6dca070b4b6db09d3de83e">コミット</a></td>
    </tr>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4870">ACP2E-4870のQPT 1.1.82修正に関する詳細な説明を追加しました：製品アラートの電子メールはストアビューの電子メール設定を無視します</a>。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/907df07e641ab7124353f89ca799f92d097aa54f">コミット</a></td>
    </tr>
    <tr>
      <td><p>Adobe Commerce 2.4.9がサポートされている<a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/release/product-availability">製品の可用性</a> テーブルを更新し、2.4.3以降のコア製品に含まれているページビルダーエントリを削除しました。</p>
</td>
      <td>
        メジャーアップデート
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/a5120adab9f624677447889722359951e775c3f3">コミット</a></td>
    </tr>
  </tbody>
</table>

### 2026年8月9日（PT）

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
      <td><p><a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4593">ACP2E-4593のQPT 1.1.82の修正に関する詳細な説明を追加しました。複数のweb サイトのストアフロントで、セカンダリ web サイトで提供される間違ったWeb サイト制限CMS ページ </a>。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/86c85db0098192092241b680d38b882f1a52b578">コミット</a></td>
    </tr>
  </tbody>
</table>

### 2026年8月6日（PT）

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
      <td><p>Adobe Commerce 2.4.6、2.4.7、および2.4.8の<a href="https://experienceleague.adobe.com/ja/docs/commerce-operations/release/product-availability">製品の可用性</a>のB2B拡張機能のバージョン サポートのマトリックスを修正しました。</p>
</td>
      <td>
        テクニカル
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/50fb71aa968abf1302e86ffeb3d3b3a66b3c33d5">コミット</a></td>
    </tr>
  </tbody>
</table>
