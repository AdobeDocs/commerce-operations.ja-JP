---
title: Adobe Commerceの導入
description: Composerを使用してAdobe Commerce ソフトウェアを入手する方法、拡張機能の互換性を確認する方法、インストールに適したディストリビューションを選択する方法について説明します。
exl-id: 7a769d5b-5397-4572-8db5-7602068e6aad
source-git-commit: 41b8d77793f1c24f08ff7e6a2d35826a62477534
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# Adobe Commerceの導入

あなたは、アドビのe コマースソフトウェアに信頼を置く世界中の24万人のマーチャントの1人です。 インストールを開始するのに役立つ情報をいくつか収集しました。

## ソフトウェアの入手方法

Adobeで作成された拡張機能とAdobe CommerceおよびMagento Open Source用のCommerce サービスの可用性と互換性については、[製品の可用性ページ ](https://experienceleague.adobe.com/en/docs/commerce-operations/release/product-availability)を参照してください。

>[!NOTE]
>
>Adobe Commerce コードベースは、ポリシーの変更により、Composer経由でのみ配布されるようになりました。 コードベースはダウンロードセクションで使用できなくなったため、Composerを使用して、リストされているAdobe Commerce バージョンのいずれかをダウンロードします。
>
>詳しくは、[請求明細書にアクセスできず、クラウドインフラストラクチャ上のAdobe Commerceでコードベースをダウンロードできない](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26611)を参照してください

Adobe Commerceのインストールを開始するには、次の表を参照してください。

<table>
    <tbody>
        <tr>
            <th>利用者のニーズ</th>
            <th>説明</th>
            <th>インストールとアップグレードの手順</th>
            <th>今すぐはじめるリンク</th>
        </tr>
    <tr>
        <td><p>インテグレータ、パッケージャ</p></td>
        <td><p>インストールされているすべてのコンポーネントを完全に制御したい、アプリケーションサーバーにアクセスできる、高度に技術的な、Magento Open Sourceを他のコンポーネントと再パッケージする可能性があります。</p>
        </td>
        <td><ol><li>使用するコンポーネントのリストを含むコンポーザー<em> プロジェクト </em>を作成します。</li>
            <li>Composerを使用してパッケージの依存関係を更新します。<code>composer create-project</code>を使用してComposer メタパッケージを取得します。</li>
            <li><a href="../advanced.md"> コマンドライン </a>を使用してアプリケーションをインストールします。</li>
        <li><a href="../../upgrade/implementation/perform-upgrade.md"> コマンドライン </a>を使用して、アプリケーションと拡張機能をアップグレードします。</li></ol></td>
        <td><p><a href="../composer.md">メタパッケージを入手</a></p></td>
    </tr>
    <tr>
        <td><p>開発者提供</p></td>
        <td><p>Magento Open Sourceのコードベースに貢献し、バグを報告し、アプリケーションをカスタマイズします。 非常に技術的な、独自の開発サーバーを持って、コンポーザーとGitHubを理解しています。</p>
            <p>実稼動環境でアプリケーションを<em>使用することはできません</em>。</p>
      <p><a href="../../upgrade/developer/git-installs.md">Composer コマンドとGit コマンド </a>を使用してアップグレードする必要があります。</p></td>
        <td><ol><li>GitHub リポジトリを複製します。</li>
            <li>Composerを使用して、パッケージの依存関係を更新します。</li>
            <li><a href="../advanced.md"> コマンドライン </a>を使用してアプリケーションをインストールします。</li>
            <li><a href="../../upgrade/developer/git-installs.md">ComposerおよびGit コマンド </a>を使用してアプリケーションをアップグレードします。</li>
            <li><code>app/code</code> ディレクトリのコードをカスタマイズします。</li></ol></td>
        <td><p><a href="https://developer.adobe.com/commerce/contributor/guides/install/clone-repository">GitHub リポジトリのクローン</a></p></td>
    </tr>
    </tbody>
</table>

## 役立つ情報

ページの左側にあるリンクを使用して、インストールの各部分のトピックを移動します。

## 必要なサーバー権限

UNIX システムでは、Web サーバーやPHPなどのソフトウェアをインストールして設定するには、`root`権限が必要です。 このソフトウェアをインストールする必要がある場合は、`root` アクセス権があることを確認してください。

Web サーバーがそれらのファイルを操作できない可能性があるため、*not*&#x200B;は`root` ユーザーとしてweb サーバーのdocrootにアプリケーションをインストールしないでください。

[ ファイルシステム所有者](file-system/overview.md)を作成し、その所有者をweb サーバーのグループに追加するには、`root`権限が必要です。 ファイルシステム所有者を使用して、コマンドラインから`bin/magento` コマンドを実行し、タスクをスケジュールするcron ジョブを設定します。
