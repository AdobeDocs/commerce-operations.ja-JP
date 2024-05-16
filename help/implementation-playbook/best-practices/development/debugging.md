---
title: デバッグのベストプラクティス
description: Adobe Commerceの一般的な開発の問題を解決する方法について説明します。
feature: Best Practices
role: Developer
exl-id: 78fbea7b-28e8-4713-990d-b4cae159250c
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '1139'
ht-degree: 0%

---

# Adobe Commerceのデバッグのベストプラクティス

ここでは、Adobe Commerce フレームワークを体系的かつ効果的にデバッグする方法について説明します。 目的は、問題の原因を迅速に突き止め、調査時間を最小限に抑えることです。

## トラブルシューティング：通常の容疑者

ここでは、開発中に発生する可能性のある最も一般的な問題について説明します。

### キャッシュ

- さらに調査する前にキャッシュをフラッシュします
- APC キャッシュ、CDN、ワニス、生成されたコードおよび `var/view_preprocessed` および `pub/static/` ディレクトリ
- キャッシュのフラッシュまたはコードの変更後にキューハンドラーを停止および再起動します

次のコードサンプルでは、キャッシュの管理に関連する便利なコマンドを示しています（実稼動環境では実行しないでください）。

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

問題がインデックス関連の可能性がある場合は、すべてを再インデックスします。 インデックス付きデータのデバッグは、通常、実稼動以外の環境で行われます。 実稼動環境では、再インデックスを実行する前に、インデックスの不整合の原因を調査する必要が生じる場合があります。 不良状態の特徴は、問題の原因について何かを教えることができます。

### コンポーザー

ブランチの変更や、以前のデバッグ作業で編集されたコアファイルが原因で、コードが古くなっている可能性があります。 潜在的な問題を排除するには、次のコマンドを実行します。

```bash
rm -rf vendor/*
composer clear-cache
composer install
```

### 生成されたコンテンツ

JS、CSS、画像、翻訳、その他のファイルで生成されたコンテンツをデバッグする前に、フロントエンドファイルを再構築します。

```bash
rm -rf generated/* var/cache/* var/page_cache/* var/session/* var/view_preprocessed/* pub/static/*
bin/magento setup:static-content:deploy
bin/magento cache:flush
```

### 開発者モード

ローカルインストールがにあることを確認します `developer` モード。

### 新規モジュール

モジュールを作成した場合は、次の問題を確認してください。

- モジュールは有効になっていますか？

  ```bash
  bin/magento module --enable Your_Module
  ```

  を確認します `app/etc/config.php` 新しいモジュール用のファイルです。

- ファイルおよびディレクトリ構造のネストを確認します。 例えば、にはレイアウトファイルがあります。 `view/layout/` の代わりにのディレクトリ `view/frontend/layout` ディレクトリ？ のテンプレートです `view/frontend/template` の代わりにのディレクトリ `view/frontend/templates` ディレクトリ？

## トラブルシューティング：半分割

通常の容疑者が問題の解決策を提示しない場合、問題を半減（または 2 等分）させる方法が最も速い方法です。 この方法では、大きなチャンクを排除し、コードを線形的に調べるのではなく、残っているものを分割して根本原因を特定します。

次の図を参照してください。

![2 分割図](../../../assets/playbooks/bisect.png)

![2 分割図](../../../assets/playbooks/bisect2.png)

2 等分する方法はいくつかありますが、Adobeでは次の順序で行うことをお勧めします。

- トピック別に分割
- コミットで分割
- ファイル別に分割

### 手順 1：トピック別に分割

問題がコードに関連していない可能性がある場合は、最初に大きなチャンクを削除します。 大きなチャンクの一部を次に示します。

- **Adobe Commerce フレームワーク** – その課題は、そもそもAdobe Commerceの問題なのですか。それとも、他のコネクテッドシステムの問題なのでしょうか。
- **サーバーとクライアント**— ブラウザのキャッシュとストレージをクリアします。 問題は解決したか？ サーバー関連の原因は除外されるかもしれません。 問題はまだ存在しますか？ ブラウザーのデバッグに時間を費やす必要はありません。
- **Session** – 利用者ごとに問題が発生するのでしょうか。 そうでない場合、問題はセッション関連またはブラウザー関連のトピックに限定される可能性があります。
- **キャッシュ** – すべてのキャッシュを無効にすると、何か変更はありますか？ その場合は、キャッシュ関連のトピックに焦点を当てることができます。
- **データベース** – この問題は、同じコードを実行するすべての環境で発生しますか？ そうでない場合は、設定やその他のデータベース関連のトピックで問題を探します。
- **コード** – 上記のどれも問題を解決しなかった場合、コードの問題を探します。

### 手順 2: コミットで分割する

この問題が今から 2 か月前の間に発生した場合は、コードを 2 か月前にロールバックします。 問題がまだ発生しているかどうかを確認します。 1 か月先に進みます。 問題は発生しますか？ そうでない場合は、2 週間進みます。 それは今起こっていますか？ 1 週間戻る。 まだ居る？ 4 日間戻る。 ある時点で、問題に関連するコードを含んでいる可能性が高いコミットが 1 つだけ残っています。 これで、そのコミットで編集されたファイルだけが根本原因となる可能性が高くなります。

週と日をコミットで置き換えることができます。 例えば、ロールバック 100 コミット、フォワード 50、フォワード 25、バック 12 などです。

### 手順 3：ファイル別に分割する

- Adobe Commerceをファイルタイプ（コアと非コア）で分割します。 まず、すべての顧客モジュールとマーケットプレイスモジュールを無効にします。 問題はまだ存在しますか？ 非コアの問題である可能性が高いです。
- でモジュールの半分を再び有効にする `app/etc/config.php` ファイル。 依存関係に注意します。 同じトピックを持つモジュールクラスターをすべて一度に有効にすることをお勧めします。 問題はまだ存在しますか？
- 残りのモジュールの 4 分の 1 を有効にします。 問題はまだ存在しますか？ 有効にした操作の半分を無効にします。 この方法は、根本原因を単一のモジュールに分離するのに役立ちます。

## タイム セーバー

このセクションでは、トラブルシューティング以外にも、デバッグ中の時間節約に役立つ一般的なルールをいくつか示します。

### データを制限

問題をレプリケートするには、カタログ全体を表示する必要があるか、すべてのストアを表示する必要があるかを検討します。 デバッグを開始する前にカタログの 95% を削除したデータベースクローンで、インデックス作成の問題をデバッグできます。 この方法を使用すると、インデックス作成プロセス中にかなりの時間を節約できます。 ストア数とカタログを減らしたクライアントデータベースの複製を作成します。 これは、デバッグしている領域に応じて、他のエンティティ（顧客など）にも適用される場合があります。

### 詳細を確認する

時には、すべてのコードと技術的な仕事の中で忘れやすい簡単なステップ：詳細情報を尋ねます。 全画面表示のキャプチャ、ビデオ、問題を特定した人物とのビデオ会議チャット、レプリケーション手順、問題のあるイベントの周りで他の重要ではないように思われる問題が発生したかどうかに関する質問。 誰かが何が起こると予想したかを尋ねなさい。 これは本当にバグですか、それともコードの仕組みの誤解ですか。

### 言語と解釈

問題の説明は明確ですか。 用語や説明を複数の方法で解釈できないことに注意してください。 その場合は、同じことを話していることを確認してください。

### インターネット検索

問題に関連する用語でインターネット検索を実行します。 他のユーザーが既に同じ問題に遭遇している可能性があります。 でのの検索 [Adobe Commerce GitHub の問題](https://github.com/magento/magento2/issues).

### 休憩する

問題を長時間見ていると、解決策を見つけるのが難しい場合があります。 あなたの仕事を置いて、別のタスクをピックアップしたり、散歩してください。 しばらく問題を忘れると、答えが出ることがあります。

## ツール

n98 magerun CLI ツール （[https://github.com/netz98/n98-magerun2](https://github.com/netz98/n98-magerun2)）には、コマンドラインからAdobe Commerceを操作するための便利な機能が用意されています。 特に、次のコマンドでは、

```bash
n98-magerun2.phar dev:console
n98-magerun2.phar sys:cron:run
n98-magerun2.phar db:console
n98-magerun2.phar index:trigger:recreate
```


## コードスニペット

次のトピックでは、Commerce プロジェクトの問題をログに記録したり特定したりするのに使用できるコードスニペットを提供します。

### XML ファイルがCommerceで使用されているかどうかを確認

XML ファイルに明白な構文エラーを追加して、使用されているかどうかを確認します。 タグを開き、以下のような場合は閉じないでください。

```xml
<?xml version="1.0"?>
<test
```

このファイルを使用すると、エラーが生成されます。 そうでない場合は、モジュールが使用されていないか、インスタンスに対して有効になっていないか、XML ファイルが間違った場所にある可能性があります。

### ログ

>[!BEGINTABS]

>[!TAB Adobe Commerce]

```php
\Magento\Framework\App\ObjectManager::getInstance()
    ->get(\Psr\Log\LoggerInterface::class)->debug('message');
```

>[!TAB モノローグ]

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

どの PHP ファイルでも常に動作する 2 つの例を以下に示します。

```php
file_put_contents('/var/www/html/var/log/example.log', "example line\n", FILE_APPEND);
file_put_contents('/var/www/html/var/log/example.log', print_r($yourArray, true) . "\n", FILE_APPEND);
```

また、スタックトレースの場合は次のようになります。

```php
try {
    throw new \Exception('example');
} catch (\Exception $e) {
    file_put_contents('/var/www/html/var/log/example.log', $e->getTraceAsString() . "\n", FILE_APPEND);
}
```
