---
title: Adobe Commerceソフトウェアの入手
description: Adobe CommerceおよびMagento Open Sourceソフトウェアのダウンロード方法を説明します。
exl-id: 7a769d5b-5397-4572-8db5-7602068e6aad
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# Adobe Commerceソフトウェアの入手

あなたは世界中の 24 万人の商人の中で、私たちの e コマースソフトウェアに信頼を置いています。 インストールを開始する際に役立つ情報をいくつか収集しました。

## ソフトウェアの入手方法

魅力的な新機能とリリースの入手可否を確認し、 [製品の可用性ページ](https://devdocs.magento.com/release/availability.html).

Adobe CommerceまたはMagento Open Sourceのインストールの概要については、次の表を参照してください。

<table>
    <tbody>
        <tr>
            <th>ユーザーのニーズ</th>
            <th>説明</th>
            <th>インストールおよびアップグレードの手順の概要</th>
            <th>はじめにリンク</th>
        </tr>
    <tr>
        <td><p>インテグレーター、Packager</p></td>
        <td><p>インストールされているすべてのコンポーネントを完全に制御し、高度な技術を持つアプリケーションサーバーにアクセスできるように、他のコンポーネントとのMagento Open Sourceを再パッケージ化する可能性があります。</p>
        </td>
        <td><ol><li>コンポーザーを作成 <em>プロジェクト</em> 使用するコンポーネントのリストを含む</li>
            <li>Composer を使用してパッケージの依存関係を更新し、を使用 <code>composer create-project</code> をクリックして、Composer のメタパッケージを取得します。</li>
            <li>を使用してアプリケーションをインストールします <a href="../advanced.md">コマンドライン</a>.</li>
        <li>を使用して、アプリケーションと拡張機能をアップグレードします。  <a href="../../upgrade/implementation/perform-upgrade.md">コマンドライン</a>.</li></ol></td>
        <td><p><a href="../composer.md">メタパッケージの取得</a></p></td>
    </tr>
    <tr>
        <td><p>貢献開発者</p></td>
        <td><p>Magento Open Sourceコードベース、ファイルのバグ、およびアプリケーションのカスタマイズに関与します。 高度に技術的で、独自の開発サーバーを持ち、Composer と GitHub を理解しています。</p>
            <p>あなた <em>できません</em> 実稼動環境でアプリケーションを使用します。</p>
      <p>を使用してアップグレードする必要があります。 <a href="../../upgrade/developer/git-installs.md">コンポーザーと Git のコマンド</a>.</p></td>
        <td><ol><li>GitHub リポジトリのクローンを作成します。</li>
            <li>Composer を使用してパッケージの依存関係を更新します。</li>
            <li>次を使用してアプリケーションをインストール <a href="../advanced.md">コマンドライン</a>.</li>
            <li>次を使用してアプリケーションをアップグレード <a href="../../upgrade/developer/git-installs.md">コンポーザーと Git のコマンド</a>.</li>
            <li>の下のコードをカスタマイズします。 <code>app/code</code> ディレクトリ。</li></ol></td>
        <td><p><a href="https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/">GitHub リポジトリのクローン</a></p></td>
    </tr>
    </tbody>
</table>

## 役に立つ情報

ページの左側にあるリンクを使用して、インストールの各部分のトピックに移動します。

## 必要なサーバー権限

UNIX システムには `root` Web サーバ、PHP などのソフトウェアをインストールして設定する権限。 このソフトウェアをインストールする必要がある場合は、 `root` にアクセスします。

実行 *not* web サーバーのドキュメントルートに、 `root` ユーザーを設定する必要があります。

必要な操作 `root` 作成する権限 [ファイルシステム所有者](file-system/overview.md) その所有者を web サーバーのグループに追加します。 ファイルシステムの所有者を使用して、 `bin/magento` コマンドをコマンドラインから実行し、cron ジョブを設定します。cron ジョブは、タスクをスケジュールします。
