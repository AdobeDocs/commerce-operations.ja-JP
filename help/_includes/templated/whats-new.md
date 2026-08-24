---
source-git-commit: 9f9c38163d91b655bf44cac81875dab59ee2c77d
workflow-type: tm+mt
source-wordcount: '2845'
ht-degree: 0%

---
# 新しいテンプレート

## 最新情報

このページには、過去60日間に行われた変更が含まれます。 コピー編集などのマイナーな更新は、このリストから除外されます。

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
      <td><p>Commerce キャッシュに関するドキュメントを更新し、オンプレミスとクラウドのガイダンスと、Symfony L2 キャッシュを使用してValkeyに移行するための新しい移行ガイダンスを更新しました：<br />- <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cache/caching-overview"> キャッシュの概要と設定オプション </a>。<br />- <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cache/cache-types"> キャッシュフロントエンドとタイプを更新</a>。<br />- パフォーマンス最適化のための<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cache/cache-options"> キャッシュバックエンドオプションとストレージ参照</a>を更新しました。<br />- </a>から1}Symfony2 キャッシュへのへのへの移行移行ガイダンスをに更新しました。<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cache/level-two-cache">- <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/planning/redis-valkey-service-configuration"> クラウド固有の移行手順を使用したValkeyとRedis サービス設定</a>のベストプラクティスと、Symfony L2 キャッシュを使用したValkeyへの移行の手順。<code>RemoteSynchronizedCache</code><br /></p>
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
      <td><p>お客様がCloud UIでサービスの依存関係のバージョンを確認する方法の手順を更新し、お客様がストアのアップグレード互換性レポートを生成する方法に関するガイドのリンクを<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/security-enforcement-policy#action-1-verify-and-upgrade-third-party-software-dependencies"> サードパーティのソフトウェアの依存関係を確認してアップグレード </a>で更新しました。</p>
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
      <td><p><a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4194">ACP2E-4194のQPT 1.1.82修正に関する詳細な説明を追加しました。不明なフィルター名を持つGraphQL リクエストは、PHP例外ログ </a>を引き起こします。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/d4202395c5b7bb5e8c4a95d8fb353ec0fc523fcb">コミット</a></td>
    </tr>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4695">ACP2E-4695のQPT 1.1.82修正に関する詳細な説明を追加しました：カタログ ルール インデクサーのメモリ不足エラーは、メモリの過度の使用によって発生します</a>。</p>
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
      <td><p>実稼動環境での使用は推奨されず、アップグレードの互換性のためにのみ存在するため、<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/adobe-commerce/2-4-9#php-and-composer">2.4.9 リリースノート </a>でサポート対象のPHP バージョンとしてPHP 8.4を削除しました。</p>
</td>
      <td>
        リリースノート、テクニカル
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/603bb70012a2f92ceeaad644d5252c4677a1a47c">コミット</a></td>
    </tr>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4894">ACP2E-4894のQPT 1.1.82修正に関する詳細な説明を追加しました。非同期インデックス作成が有効になっている場合に、新しい注文が管理注文グリッドに表示されます</a>。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/ad40d94c1618f7e423fd6a773185b8fba48c2c72">コミット</a></td>
    </tr>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4698">ACP2E-4698のQPT 1.1.82修正に関する詳細な説明を追加しました：ページビルダーテキストのインライン編集により、ポータブルディレクティブの代わりに絶対メディア URLが保存されます</a>。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/68e5e99ac0717b0e358acd6acf9934044a917a82">コミット</a></td>
    </tr>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/versions"> リリースバージョン </a> ページの複数のAdobe Commerce リリースラインのサポート終了、拡張サポート、その他のセキュリティ修正プロビジョニング日を修正および完了しました。</p>
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
      <td><p>Adobe Commerce 2.4.4-p18 （最新）のサポート対象バージョンとしてRabbitMQ 3.13を追加するために、<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirements">必要システム構成</a>を更新し、Debian OS アップグレードパスのブロッカーを解決しました。</p>
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
      <td><p><a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4797">ACP2E-4797のQPT 1.1.82修正に関する詳細な説明を追加しました：utf8mb4がサポートされている場合のAdmin WYSIWYG エディターとPage Builder ブロックの4 バイト Unicode文字</a>。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/c97bb9c77eb0ec4bbc92d042cfa9fd440e970ca7">コミット</a></td>
    </tr>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4682">ACP2E-4682のQPT 1.1.82修正に関する詳細な説明を追加しました：見積もりをチェックするストアフロントページがアクティブで、空の見積もりレコードを作成しました</a>。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/ceac870e3ccb9eeee64e3b574aaccd33c6ab69d0">コミット</a></td>
    </tr>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4799">ACP2E-4799のQPT 1.1.82修正に関する詳細な説明を追加しました。GraphQL クエリ requisition_listsは、ページネーション </a>で誤ったtotal_countを返します。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/19f854db1a0ff78d0a6dca070b4b6db09d3de83e">コミット</a></td>
    </tr>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4870">ACP2E-4870のQPT 1.1.82修正に関する詳細な説明を追加しました：製品アラートの電子メールはストアビューの電子メール設定を無視します</a>。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/907df07e641ab7124353f89ca799f92d097aa54f">コミット</a></td>
    </tr>
    <tr>
      <td><p>Adobe Commerce 2.4.9がサポートされている<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/product-availability">製品の可用性</a> テーブルを更新し、2.4.3以降のコア製品に含まれているページビルダーエントリを削除しました。</p>
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
      <td><p><a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4593">ACP2E-4593のQPT 1.1.82の修正に関する詳細な説明を追加しました。複数のweb サイトのストアフロントで、セカンダリ web サイトで提供される間違ったWeb サイト制限CMS ページ </a>。</p>
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
      <td><p>Adobe Commerce 2.4.6、2.4.7、および2.4.8の<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/product-availability">製品の可用性</a>のB2B拡張機能のバージョン サポートのマトリックスを修正しました。</p>
</td>
      <td>
        テクニカル
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/50fb71aa968abf1302e86ffeb3d3b3a66b3c33d5">コミット</a></td>
    </tr>
  </tbody>
</table>

### 2026年7月31日（PT）

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
      <td><p><a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4547">ACP2E-4547のQPT 1.1.82修正に関する詳細な説明を追加しました。管理者は、ユーザーの共有カタログ </a>に割り当てられていない場合、既定のカタログ製品を見積もりに追加できません。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/6d0313c01e979d3d4bd3e781e2f0e9c336bbd8c5">コミット</a></td>
    </tr>
  </tbody>
</table>

### 2026年7月30日（PT）

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
      <td><p>サポートされていないバージョンまたはサードパーティ製ソフトウェアの依存関係を実行しているAdobe Commerce on Cloud デプロイメントをアップグレードするための要件、タイムライン、手順を説明するために、<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/security-enforcement-policy"> セキュリティポリシー：Adobe Commerce on Cloudのお客様に対する必須のアクションと期限</a>を追加しました。</p>
</td>
      <td>
        新しいトピック
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/b7649aae1f8cab020c1081db2b2363bca22adfed">コミット</a></td>
    </tr>
  </tbody>
</table>

### 2026年7月28日（PT）

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
      <td><p><a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4805">ACP2E-4805のQPT 1.1.82修正に関する詳細な説明を追加しました。最初の販売可能な子がリスト </a>の後半に表示されるときに、設定可能な製品のチェックアウトリクエストが遅くなります。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/1b5fb4826f6599d7b7609dedfeb545f29454ba4d">コミット</a></td>
    </tr>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4748">ACP2E-4748のQPT 1.1.82修正に関する詳細な説明を追加しました。報酬ポイントの有効期限は、大きな報酬ポイント履歴を持つストアでゆっくりと実行されます</a>。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/30fe149f9743ceca7f40374246b4fc9b9503c590">コミット</a></td>
    </tr>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4875">ACP2E-4875のQPT 1.1.82修正に関する詳細な説明を追加しました。管理者ユーザーは、大きなアドレス帳を含む顧客アカウントを開くときにログアウトしました</a>。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/3174f84e0a8c64aaed50cc075a9287bc011778ef">コミット</a></td>
    </tr>
  </tbody>
</table>

### 2026年7月27日（PT）

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
      <td><p><a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/overview">概要：品質パッチツール （QPT） v1.1.82</a>を追加しました。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/ddfb8e85d015b8ab675a3af56cf5d2bb72e535c4">コミット</a></td>
    </tr>
  </tbody>
</table>

### 2026年7月23日（PT）

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
      <td><p>Adobe Commerce 2.4.9 （12.3推奨、11.8 サポート）のMariaDB Cloud バージョン サポートの詳細を含む<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirements">必要システム構成</a>を更新しました。</p>
</td>
      <td>
        テクニカル
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/eaf47339d87d296799367f699f9322c14e6ee780">コミット</a></td>
    </tr>
  </tbody>
</table>

### 2026年7月22日（PT）

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
      <td><p>RabbitMQ 4.3のアップデートやMariaDB 12.3との互換性の確認など、最新のCommerce on Cloud Service バージョンを使用して、<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirements">必要システム構成</a>のトピックを更新しました。</p>
</td>
      <td>
        メジャーアップデート
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/6607852ba3221a1120f3c88007c106ed9704dcec">コミット</a></td>
    </tr>
  </tbody>
</table>

### 2026年7月21日（PT）

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
      <td><p><a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-81/acp2e-4401">ACP2E-4401のQPT 1.1.81修正に関する詳細な説明を追加しました。設定可能な製品を含むホームページのスケジュールされた更新プレビューは、メンテナンスページ </a>にリダイレクトされます。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/41aac13f73ff0836f93b8ec30a709bd89fa34a94">コミット</a></td>
    </tr>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-81/acp2e-4468">ACP2E-4468のQPT 1.1.81修正に関する詳細な説明を追加しました。Web サイト範囲の管理者ユーザーがページビルダー</a>に動的ブロックを保存できません。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/f5fbe594284c05aaa9b2461e3628a3444229efb6">コミット</a></td>
    </tr>
  </tbody>
</table>

### 2026年7月16日（PT）

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
      <td><p><a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-81/acp2e-4801">ACP2E-4801のQPT 1.1.81修正に関する詳細な説明を追加しました。Admin</a>で交渉可能な見積もりを再設定すると、バンドル製品オプションの数量が更新されません。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/31872eee953126b52f1c13444dd46140edc879c6">コミット</a></td>
    </tr>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-81/acp2e-4786">ACP2E-4786のQPT 1.1.81修正に関する詳細な説明を追加しました：AWS S3 リモートストレージが設定されている場合、製品の書き出しが失敗します</a>。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/b7ca2e40743aa512b0bc785e486d3e7d1c6dbefc">コミット</a></td>
    </tr>
  </tbody>
</table>

### 2026年7月15日（PT）

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
      <td><p><a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-81/acp2e-4630">ACP2E-4630のQPT 1.1.81修正に関する詳細な説明を追加しました。長い製品名は、ページ区切り</a>後のマルチページ販売PDFの隣接する列と重なります。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/5581e6f7a507bb83a3fc0fd7229239137b15acd7">コミット</a></td>
    </tr>
  </tbody>
</table>

### 2026年7月14日（PT）

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
      <td><p><a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-81/acp2e-4300">ACP2E-4300のQPT 1.1.81修正に関する詳細な説明を追加しました。管理者の顧客グループが変更された後、ストアフロントカタログの権限が更新されません</a>。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/2c26efeb7aa734e4dcc8d0131cb82a96d35e8f32">コミット</a></td>
    </tr>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-81/acp2e-4680">ACP2E-4680のQPT 1.1.81修正に関する詳細な説明を追加しました。最終交渉可能な見積もりから販売不能な製品が消えます</a>。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/1448b291e70cdf515872f019028c15bd703f80fe">コミット</a></td>
    </tr>
    <tr>
      <td><p>可用性、レポート生成、JSONおよびCSV出力、トラブルシューティング、毎月のAdobe Commerce セキュリティパッチステータスレポートのリリースノートを含む<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/commerce-version-tool/intro">Commerce Version Tool ドキュメント </a>を追加しました。</p>
</td>
      <td>
        新しいトピック
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/43571d84d9a27ffa113ba4f3a8a08883602211f6">コミット</a></td>
    </tr>
  </tbody>
</table>

### 2026年7月10日（PT）

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
      <td><p><a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-81/overview">概要：品質パッチツール （QPT） v1.1.81</a>を追加しました。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/2cc434ac8efd0d9344140ad07f2f68d2d48b1fb4">コミット</a></td>
    </tr>
  </tbody>
</table>

### 2026年7月6日（PT）

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
      <td><p><a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4493">ACP2E-4493のQPT 1.1.80修正に関する詳細な説明を追加しました。非同期インデックス作成が有効になっている場合、Sales Order Archive グリッドに誤った注文ステータスが表示されます</a>。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/2fdbf6a4fd4924947a2cb2a508e067b8bb0d694c">コミット</a></td>
    </tr>
  </tbody>
</table>

### 2026年7月2日（PT）

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
      <td><p><a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4239">ACP2E-4239のQPT 1.1.80修正に関する詳細な説明を追加：管理者グリッド日付フィルターは、タイムゾーンの不一致</a>が原因で結果を返しません。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/58f157a5f863973df723a6bce5844883f2aa12f4">コミット</a></td>
    </tr>
  </tbody>
</table>

### 2026年6月29日（PT）

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
      <td><p><a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4481">ACP2E-4481のQPT 1.1.80修正に関する詳細な説明を追加しました：注文キャンセル </a>後にバンドル製品の販売可能性が誤って再計算されました。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/ccea0456268862ba11e77ef16318bc8b2d76b0b1">コミット</a></td>
    </tr>
  </tbody>
</table>

### 2026年6月26日（PT）

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
      <td><p>「<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4615">ACP2E-4615: PayPal オンライン注文の返金が失敗し、「PayPal ゲートウェイがリクエストを拒否します」というエラーが発生した場合の、QPT 1.1.80の修正に関する詳細な説明を追加しました。 内部エラーです。"</a>。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/056f30558d8d9f3e218f589e2819ec5d8d6274e3">コミット</a></td>
    </tr>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acsd-53502">ACSD-53502: New Relic スクリプトの繰り返しにより、iOS Safariでカートに追加が断続的に失敗する</a>のQPT 1.1.80修正に関する詳細な説明を追加しました。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/95cfe4554c4501fa9526e0c8b0c039cf99228207">コミット</a></td>
    </tr>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4626">ACP2E-4626のQPT 1.1.80修正に関する詳細な説明を追加しました：ストアフロント JavaScript ファイルが2回読み込まれると、重複した読み込みと不安定な動作が発生します</a>。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/55fad95c3110f8150097f410115d89299b9e681b">コミット</a></td>
    </tr>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4813">ACP2E-4813のQPT 1.1.80修正に関する詳細な説明を追加しました：USPSの配送方法が利用できないか、複数パッケージの注文に対して正しくありません</a>。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/94b45f953d8a91814fa7359369f976e0cbd94a36">コミット</a></td>
    </tr>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4610">ACP2E-4610のQPT 1.1.80修正に関する詳細な説明を追加しました：sales_clean_quotes cron</a>の実行が遅くなりました。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/a7e34f7858dd74cf1c4702dfc877a793094ad042">コミット</a></td>
    </tr>
  </tbody>
</table>

### 2026年6月25日（PT）

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
      <td><p><a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4488">ACP2E-4488のQPT 1.1.80の修正に関する詳細な説明を追加しました：大規模な属性セットの管理者製品の保存/編集が遅い</a>。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/ac57acc5c527f1c7cc7dbd3198f23e75f08fe207">コミット</a></td>
    </tr>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4496">ACP2E-4496のQPT 1.1.80修正に関する詳細な説明を追加しました。Analytics cron ジョブは、実行時にパフォーマンスを低下させます</a>。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/0b7826459c116ef03a34f0a01e5db235294c3cb1">コミット</a></td>
    </tr>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4552">ACP2E-4552のQPT 1.1.80修正に関する詳細な説明を追加しました：GraphQLの回答が会社のステータスを返しません</a>。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/6988b8b17bd1f2161e8fd8c7dd128a75c0023de8">コミット</a></td>
    </tr>
  </tbody>
</table>

### 2026年6月24日（PT）

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
      <td><p><a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4808">ACP2E-4808のQPT 1.1.80修正に関する詳細な説明を追加しました：ストアフロント </a>で商品の重みが測定単位なしで表示されます。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/538221930434b21b92d587fd889e556564a0a45c">コミット</a></td>
    </tr>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4472">ACP2E-4472のQPT 1.1.80修正に関する詳細な説明を追加しました：「顧客としてログイン」フロー</a>を使用して作成されたNull見積もり。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/49b49560901525aa9e635eb0ea6542339270cabf">コミット</a></td>
    </tr>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4653">ACP2E-4653のQPT 1.1.80修正に関する詳細な説明を追加しました：カート価格ルール カテゴリ スコープの条件がREST API</a>から見つかりません。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/f6f4ed205def1cc5f9932857d75222015683fd08">コミット</a></td>
    </tr>
  </tbody>
</table>

### 2026年6月23日（PT）

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
      <td><p>クラウドとオンプレミスのスコープを明確にし、<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cache/caching-overview">設定ガイド </a>のキャッシュ設定のトピック全体で、クラウドのデプロイメントに関する<a href="https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/planning/redis-valkey-service-configuration">RedisとValkey サービス設定のベストプラクティス </a>を更新しました。 クラウドのデプロイメントに関するCommerceのベストプラクティス。</p>
</td>
      <td>
        フィードバック
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/5d8876789a01e0e27cedfb67e0dd8b3dbc4543f7">コミット</a></td>
    </tr>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4156">ACP2E-4156のQPT 1.1.80修正に関する詳細な説明を追加しました。REST APIの出荷先住所の検証では、管理者属性の設定</a>が無視されます。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/897bbc5b6624dfe17deac6ca878669a5245c34ea">コミット</a></td>
    </tr>
    <tr>
      <td><p><a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4533">ACP2E-4533のQPT 1.1.80修正に関する詳細な説明を追加しました。URLにストアコード </a>が含まれている場合、ストアフロントでプレースホルダー画像の読み込みに失敗します。</p>
</td>
      <td>
        新しいトピック、qpt
      </td>
      <td><a href="https://github.com/AdobeDocs/commerce-operations.en/commit/eb7012dd29323ae70a19c7b37ab82dac5215c705">コミット</a></td>
    </tr>
  </tbody>
</table>
