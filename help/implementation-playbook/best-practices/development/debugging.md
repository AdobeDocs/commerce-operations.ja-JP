---
title: デバッグのベストプラクティス
description: 一般的なAdobe Commerce開発の問題を解決する方法を説明します。
feature: Best Practices
role: Developer
source-git-commit: 291c3f5ea3c58678c502d34c2baee71519a5c6dc
workflow-type: tm+mt
source-wordcount: '1143'
ht-degree: 0%

---


# Adobe Commerceのデバッグのベストプラクティス

このトピックでは、Adobe Commerceフレームワークを体系的かつ効果的にデバッグする方法について説明します。 目標は、問題の根本にすばやく到達し、調査時間を最小限に抑えることです。

## トラブルシューティング：通常の容疑者

この節では、開発時に発生する可能性のある最も一般的な問題について説明します。

### キャッシュ

- さらに調査する前にキャッシュをフラッシュします
- APC キャッシュ、CDN、Vanrish、生成されたコード、 `var/view_preprocessed` および `pub/static/` ディレクトリ
- キャッシュのフラッシュまたはコードの変更後に、キューハンドラーを停止して再起動します

以下のコードサンプルは、キャッシュの管理に関連する便利なコマンドを提供します（実稼動環境では実行しない）。

```bash
# restart php-fpm to flush APC
sudo service php-fpm restart
 
# restart varnish to force full flush
sudo service varnish restart
 
# clear generated files
rm -rf generated/*
 
# clear static file cache
rm -rf var/view_preprocessed/*
rm -rf pub/static/*
 
# flush redis cache
redis-cli -n <db_number> FLUSHDB
 
# flush redis cache and sessions
redis-cli FLUSHALL
 
# flush redis cache with telnet
telnet <ip_or_host> 6379
SELECT <db_number>
FLUSHDB
Ctrl + ]
quit
 
# flush redis cache and sessions with telnet
telnet <ip_or_host> 6379
FLUSHALL
Ctrl + ]
quit
 
# find consumers
pgrep -af queue:consumers:start
 
# kill all queue consumers (they will restart by cron job)
sudo pkill -f queue:consumers:start
 
# kill a specific queue consumer (it will restart by cron job)
sudo kill <process_id>
```

### インデックス付きデータ

インデックス関連の問題の場合は、すべてを再インデックス化します。 インデックス付きデータのデバッグは、通常、実稼動環境以外でおこなわれます。 実稼動環境では、インデックスを再作成する前に、インデックスのずれの起源を調べる必要が生じる場合があります。 障害状態の特性は、問題の原因について何かを示すことができます。

### コンポーザー

ブランチの変更や、以前のデバッグ作業で編集されたコアファイルが原因で、古いコードが使用されている可能性があります。 潜在的な問題を解消するには、次のコマンドを実行します。

```bash
rm -rf vendor/*
composer clear-cache
composer install
```

### 生成されたコンテンツ

JS、CSS、画像、翻訳およびその他のファイルで生成されたコンテンツをデバッグする前に、フロントエンドファイルを再構築します。

```bash
rm -rf generated/* var/cache/* var/page_cache/* var/session/* var/view_preprocessed/* pub/static/*
bin/magento setup:static-content:deploy
bin/magento cache:flush
```

### 開発者モード

ローカルインストールがにあることを確認します。 `developer` モード。

### 新しいモジュール

モジュールを作成した場合は、以下の問題を確認してください。

- モジュールは有効になっていますか？

  ```bash
  bin/magento module --enable Your_Module
  ```

  次を確認します。 `app/etc/config.php` ファイルを作成します。

- ファイルとディレクトリの構造のネストを確認します。 例えば、は、 `view/layout/` の代わりにディレクトリ `view/frontend/layout` ディレクトリ？ テンプレートは `view/frontend/template` の代わりにディレクトリ `view/frontend/templates` ディレクトリ？

## トラブルシューティング：分割の半分

通常の容疑者が問題に対する解決策を提供しない場合、最も早い方法は、問題を半分に分割（または 2 分）することです。 この方法を使用すると、大きなチャンクを削除し、残りの部分を分割して、コードを線形的に処理する代わりに、根本原因を特定できます。

次の図を参照してください。

![2 等分図](../../../assets/playbooks/bisect.png)

![2 等分図](../../../assets/playbooks/bisect2.png)

2 分する方法はいくつかありますが、Adobeでは次の順序に従うことをお勧めします。

- トピック別に分割
- コミットで 2 等分
- 2 等分

### 手順 1：トピック別に分割

コードに関連しない問題が発生した場合は、まず大きなチャンクを削除します。 考慮すべき大きなチャンクの一部を次に示します。

- **Adobe Commerce framework** — 問題はAdobe Commerceに関係しているのでしょうか、それとも別の接続システムに関連しているのでしょうか。
- **サーバーとクライアント** — ブラウザのキャッシュとストレージをクリアします。 問題は解決しましたか？ サーバー関連の原因が除外される可能性があります。 問題はまだ存在しますか？ ブラウザーのデバッグで、これ以上時間を無駄にする必要はありません。
- **セッション** — すべてのユーザーに問題が発生しているか。 そうでない場合、問題はセッションまたはブラウザー関連のトピックに限定される可能性があります。
- **キャッシュ** — すべてのキャッシュを無効にすると、何も変更されませんか。 その場合は、キャッシュ関連のトピックに焦点を当てることができます。
- **データベース** — 同じコードを実行するすべての環境で問題が発生しますか。 設定されていない場合は、設定やその他のデータベース関連のトピックに問題があるかどうかを確認します。
- **コード** — 上記の問題が解決されなかった場合は、コードの問題を探します。

### 手順 2：コミットで 2 等分

問題が今から 2 ヶ月前に発生した場合は、2 ヶ月前にコードを再度ロールしてください。 問題が解決しないかを確認します。 1 ヶ月先に進んでください。 そこで問題が発生しているか。 そうでない場合は、2 週間前に進んでください。 今起こっているのか？ 1 週間戻ります。 まだ？ 4 日前に戻ります。 ある時点で、問題に関連するコードを含むコミットが 1 つだけ残っています。 根本原因は、そのコミットで編集されたファイルに限定される可能性が高くなりました。

週と日をコミットで置き換えることができます。 例えば、100 コミット、50 コミット、25 コミット、12 コミットをロールバックします。

### 手順 3：ファイルで分割

- Adobe Commerceをファイルタイプ（コアと非コア）で割ります。 まず、すべての顧客モジュールと Marketplace モジュールを無効にします。 問題はまだ存在しますか？ これは、おそらくコアでない問題です。
- でモジュールの半分（およそ）を再度有効にする `app/etc/config.php` ファイル。 依存関係に注意してください。 同じトピックを含むモジュールクラスターを一度に有効にすることをお勧めします。 問題はまだ存在しますか？
- 残りのモジュールの 4 分の 1 を有効にします。 問題はまだ存在しますか？ 有効にした内容の半分を無効にします。 このメソッドは、単一のモジュールに対する根本原因を特定するのに役立ちます。

## タイムセーバー

この節では、トラブルシューティングの手法に加えて、デバッグ中の時間を節約できる一般的なルールをいくつか示します。

### データを制限

問題をレプリケートするために、完全なカタログが必要か、すべてのストア表示が必要かを検討します。 デバッグを開始する前にカタログの 95%を削除したデータベース複製で、インデックス作成の問題をデバッグできます。 この方法を使用すると、インデックス作成プロセス中の時間を大幅に節約できます。 ストア数とカタログ数を減らして、クライアントデータベースの複製を作成します。 これは、デバッグしている領域に応じて、他のエンティティ（顧客など）にも当てはまります。

### 詳細を確認

すべてのコードと技術的な作業の中で、忘れやすい手順が表示される場合があります。詳細を確認してください。 問題の特定者とのフルスクリーンキャプチャ、ビデオ、ビデオ会議のチャット、レプリケーション手順、問題のあるイベントに関して他の一見重要でないことが発生したかどうかに関する質問。 誰かが何が起こると思ったかを尋ねる。 これは本当にバグなのか、それとも単にコードの動作方法を誤解するのか？

### 言語と解釈

問題の説明は明らかですか？ 複数の方法で解釈できる用語や説明がないことを確認していますか。 その場合は、同じことを言っていることを確認してください。

### インターネット検索

問題に関連する用語を使用してインターネット検索を実行します。 おそらく他の誰かが既に同じ問題に遭遇しています。 検索範囲： [Adobe Commerce GitHub の問題](https://github.com/magento/magento2/issues).

### 休憩を取る

長時間問題を見つけ過ぎると、解決策を見つけるのが困難になる場合があります。 仕事を降ろして別の仕事を引き受けるか、散歩をする。 しばらくの間問題を忘れると、その答えがあなたに届くかもしれません。

## ツール

n98 magerun CLI ツール ([https://github.com/netz98/n98-magerun2](https://github.com/netz98/n98-magerun2)) は、コマンドラインからAdobe Commerceを操作する際に役立つ機能を提供します。 特に、次のコマンドを使用します。

```bash
n98-magerun2.phar dev:console
n98-magerun2.phar sys:cron:run
n98-magerun2.phar db:console
n98-magerun2.phar index:trigger:recreate
```


## コードスニペット

次のトピックでは、Commerce プロジェクトの問題をログに記録または識別するために使用できるコードスニペットを示します。

### XML ファイルが Commerce で使用されているかどうかを確認します

XML ファイルに明確な構文エラーを追加して、使用されているかどうかを確認します。 タグを開き、次のような場合は閉じないでください。

```xml
<?xml version="1.0"?>
<test
```

このファイルを使用すると、エラーが発生します。 そうでない場合は、モジュールが使用されていないか、例えば有効になっていない可能性があります。そうでない場合は、XML ファイルの場所が正しくない可能性があります。

### ログ

>[!BEGINTABS]

>[!TAB Adobe Commerce]

```php
\Magento\Framework\App\ObjectManager::getInstance()
    ->get(\Psr\Log\LoggerInterface::class)->debug('message');
```

>[!TAB Monolog]

```php
$log = new \Monolog\Logger('custom', [new \Monolog\Handler\StreamHandler(BP.'/var/log/test.log')]);
$log->info('Your Logging Message', ['context' => ['email' => 'john@example.com']]);
```

>[!TAB Zend]

```php
$writer = new \Zend\Log\Writer\Stream(BP . '/var/log/test.log');
$logger = new \Zend\Log\Logger();
$logger->addWriter($writer);
$logger->info('Your text message');
$logger->info(print_r($yourArray, true));
```

>[!ENDTABS]

### 低レベルのログ

PHP ファイルで常に動作する 2 つの例を次に示します。

```php
file_put_contents('/var/www/html/var/log/example.log', "example line\n", FILE_APPEND);
file_put_contents('/var/www/html/var/log/example.log', print_r($yourArray, true) . "\n", FILE_APPEND);
```

スタックトレースの場合：

```php
try {
    throw new \Exception('example');
} catch (\Exception $e) {
    file_put_contents('/var/www/html/var/log/example.log', $e->getTraceAsString() . "\n", FILE_APPEND);
}
```
