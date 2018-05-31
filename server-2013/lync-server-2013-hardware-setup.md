﻿---
title: 'Lync Server 2013: ハードウェアのセットアップ'
TOCTitle: ハードウェアのセットアップ
ms:assetid: 37a9f295-cde3-4beb-9a6a-2580082798ab
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Gg425852(v=OCS.15)
ms:contentKeyID: 48271772
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 のハードウェアのセットアップ

 

_**トピックの最終更新日:** 2013-02-21_

トポロジの実装に必要なインフラストラクチャで要求されるハードウェアなどのコンポーネントの設定には、トポロジ ビルダーでのトポロジの公開に先立って、次の準備が必要になります。

  - トポロジ ビルダーを使用して作成および保存したトポロジ設計の各コンポーネントのハードウェアをインストールします。これらのコンポーネントには、Lync Server 2013 を実行するサーバー、データベース サーバー、インターネット インフォメーション サービス (IIS) を実行するサーバー、必要に応じて、リバース プロキシ サーバーなど必要なすべてのコンピューター、ネットワーク アダプター、ハードウェア ロード バランサー、ファイル サーバーなどの記憶装置が含まれます。ネットワーク アダプターについて推奨される数および速度に従っていることを確認してください。ハードウェア ロード バランサーを使用する場合は、Lync Server 2013 で使用するよう構成するために、ベンダーから得られる適切な情報がそろっていることを確認してください。ファイル サーバーまたは他のサーバーを使用して Lync Server で必要なファイル共有を収容する場合は、そのサーバーが使用可能であり、ファイル共有の構成準備ができていることを確認してください。展開に必要なコンポーネントを指定するトポロジの定義方法の詳細については、「[Lync Server 2013 でのトポロジの定義と構成](lync-server-2013-defining-and-configuring-the-topology.md)」を参照してください。サーバーのハードウェア要件の詳細については、「サポート」のドキュメントの「[Lync Server 2013 でサポートされるハードウェア](lync-server-2013-supported-hardware.md)」を参照してください。

  - ネットワーク インフラストラクチャが要件を満たすことを確認します。詳細については、「計画」のドキュメントの「[Lync Server 2013 でのネットワーク インフラストラクチャの要件](lync-server-2013-network-infrastructure-requirements.md)」を参照してください。

  - Active Directory ドメイン サービス を設定します。AD DS の設定には、AD DS の準備、AD DS に展開するすべてのコンポーネントの定義などが含まれます。AD DS の準備の詳細については、「展開」のドキュメントの「[Lync Server 2013 用の Active Directory ドメイン サービスの準備](lync-server-2013-preparing-active-directory-domain-services.md)」を参照してください。

  - ファイル共有の作成に必要なアクセス許可を設定します。Lync Server 2013 によるファイル共有の使用に対するアクセス許可は、トポロジの公開時に、トポロジ ビルダーによって自動で構成されます。ただし、トポロジ ビルダーで必要なアクセス許可を構成するには、トポロジの公開に使用されるユーザー アカウントがファイル共有に対するフル コントロール (読み取り/書き込み/変更) を持つ必要があります。トポロジ ビルダーの公開プロセスでファイル共有を正しく管理できるようにするには、ユーザーまたはそのユーザーが属しているドメイン グループを、ファイル共有が存在するマシン上のローカルの Administrators グループのメンバーにする必要があります。マルチドメイン シナリオでは、ドメイン A のユーザーまたはグループを、ファイル共有が配置されるドメイン B のマシン上でローカルの Administrators グループのメンバーにしてください。
    
    分散ファイル システム (DFS) におけるファイル共有の使用の詳細については、「[Lync Server 2013 でファイルの記憶域を構成する](lync-server-2013-configure-dfs-file-storage.md)」を参照してください。
    

    > [!WARNING]
    > Lync Server 2013、Enterprise Edition のファイル共有は、フロント エンド サーバー上には配置できません。



  - Web サービス用のハードウェア ロード バランサーをインストールして設定します。 ドメイン ネーム システム (DNS) 負荷分散が展開されている場合でも、これらのプールに対してハードウェア ロード バランサーを併用する必要があります。ただし、対象となるトラフィックは、HTTP/HTTPS トラフィックだけです。 ハードウェア ロード バランサーは、クライアントからのポート 443 および 80 経由での HTTPS トラフィックで使用されます。これらのプール用のハードウェア ロード バランサーは引き続き必要ですが、そのセットアップと管理は主に HTTP/HTTPS トラフィックに対するものであり、ハードウェア ロード バランサーの管理者にはなじみのあるものです。

このトピックの説明に従ってすべての準備タスクを完了したた場合でも、トポロジの公開前に、次のタスクを完了させておく必要があります。

  - [Lync Server 2013 のオペレーティング システムと必要なソフトウェアのサーバーへのインストール](lync-server-2013-install-operating-systems-and-prerequisite-software-on-servers.md)

  - [Lync Server 2013 での IIS の構成](lync-server-2013-configure-iis.md)

  - [Lync Server 2013 用 SQL Server の構成](lync-server-2013-configure-sql-server-for-lync-server.md)

  - [Lync Server 2013 でのフロント エンド プールまたは Standard Edition サーバー用の DNS レコードの構成](lync-server-2013-configure-dns-records-for-a-front-end-pool-or-standard-edition-server.md)
