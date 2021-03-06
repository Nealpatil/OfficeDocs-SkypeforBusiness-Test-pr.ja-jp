﻿---
title: 'Lync Server 2013: 自動検出サービスの要件'
TOCTitle: 自動検出サービスの要件
ms:assetid: 0ac5dbf7-9acd-4d25-b21a-932022b8b983
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Hh690012(v=OCS.15)
ms:contentKeyID: 48271211
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 の自動検出サービスの要件

 

_**トピックの最終更新日:** 2013-02-25_

Microsoft Lync Server 2013 自動検出サービスは、ディレクターおよびフロントエンド プールのサーバーで実行されます。この自動検出サービスが DNS で公開された場合、Lync Mobile を実行するモバイル デバイスでこの自動検出サービスを使用して Mobility Service を検索できます。Lync Mobile を実行するモバイル デバイスで自動検出を利用できるようにするには、自動検出サービスを実行するすべての ディレクターおよび フロント エンド サーバーで、証明書のサブジェクトの別名リストを変更する必要があります。また、リバース プロキシ上の外部 Web サービス公開ルールで使用される証明書についても、サブジェクトの別名リストの変更が必要になる場合があります。

ディレクター、フロントエンド サーバー、およびリバース プロキシで必要とされるサブジェクトの別名エントリの詳細については、「Planning for Mobility」の「[Lync Server 2013 でのモビリティの技術要件](lync-server-2013-technical-requirements-for-mobility.md)」を参照してください。

リバース プロキシでのサブジェクトの別名リストの使用については、自動検出サービスをポート 80 またはポート 443 のどちらで公開するかに基づいて決定します。

  - **ポート 80 で公開する**:   自動検出サービスへの最初のクエリをポート 80 で実行する場合、証明書を変更する必要はありません。これは、Lync を実行するモバイル デバイスがポート 80 のリバース プロキシに外部的にアクセスした後に、ポート 8080 の ディレクターまたは フロント エンド サーバーに内部的にリダイレクトされるためです。詳細については、このトピックの後半の「ポート 80 を使用する初期の自動検出プロセス」を参照してください。

  - **ポート 443 で公開する**:   外部 Web サービス公開ルールで使用される証明書上のサブジェクトの別名リストには、組織内の各 SIP ドメインの *lyncdiscover.SIP ドメイン* エントリが含まれる必要があります。

通常、内部の証明機関を使用した証明書の再発行は簡単なプロセスですが、Web サービス公開ルールで使用されるパブリック証明書の場合、サブジェクトの複数の別名エントリを追加する処理に高い費用がかかる可能性があります。この問題を回避するために、ポート 80 での自動検出の初期接続がサポートされます。この接続は、その後、ディレクターまたは フロント エンド サーバーのポート 8080 にリダイレクトされます。

たとえば、初期要求の HTTP を使用し、自動検出機能を使用して Lync Server 2013 にサインインするように、Lync Mobile を実行するモバイル クライアントを構成すると仮定します。

## ポート 80 を使用するモバイル デバイスの初期の自動検出プロセス

1.  Lync Mobile を実行するモバイル デバイスが DNS を使用して lyncdiscover.contoso.com を検索します。DNS には、A レコードが存在します。

2.  外部 DNS は、外部 Web サービスの IP アドレスをクライアントに返します。

3.  Lync Mobile を実行するモバイル デバイスは、要求 http://lyncdiscover.contoso.com?sipuri=lyncUser1@contoso.com をリバース プロキシに送信します。

4.  ポート 80 に外部的に送信された要求は Web 公開ルールによってポート 8080 に内部的に橋渡しされ、その後、ディレクターまたは フロント エンド サーバーにルーティングされます。
    
    要求は HTTP なので (HTTPS ではない)、自動検出サービスをサポートするように外部 Web サービス公開ルール上の証明書を変更する必要はありません。

5.  自動検出サービスは外部 Web サービスの URL (HTTPS 形式) を返します。

6.  Lync Mobile を実行するモバイル デバイスをポート 443 のリバース プロキシに再接続し、ユーザーのホーム プールで実行されるモビリティ サービスに 4443 経由でリダイレクトできます。
    
    HTTPS クエリは自動検出サービスの URL に対する外部 Web サービスの URL に送信されるため、この HTTPS クエリは成功します。これは、外部 Web サービスの完全修飾ドメイン名 (FQDN) に対するサブジェクトの別名エントリが証明書に既に含まれるためです。
    
    このシナリオでは、モビリティをサポートするように証明書を変更する必要はありません。
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>対象の Web サーバーに含まれる証明書に、サブジェクトの別名リストの値として、lyncdiscover.contoso.com に一致する値が含まれない場合:<br />
    a. Web サーバーは &quot;Server Hello&quot; と応答します。証明書はありません。<br />
    b. Lync Mobile を実行するモバイル デバイスはセッションを直ちに終了します。<br />
    対象の Web サーバーに含まれる証明書に、サブジェクトの別名リストの値として、lyncdiscover.contoso.com が含まれる場合:<br />
    a. Web サーバーは &quot;Server hello&quot; および証明書で応答します。<br />
    b. Lync Mobile を実行するモバイル デバイスは証明書を検証し、ハンドシェイクを完了します。</td>
    </tr>
    </tbody>
    </table>


リバース プロキシ サーバーのポート 80 を使用する、自動検出サービスへの初期接続をサポートするには、Forefront Threat Management Gateway 2010 リバース プロキシ Web 公開ルールに対して、この例に類似した http 公開ルールを作成できます。

1.  新しい Web 公開ルール (例: **Lync Server Autodiscover (HTTP)** ) を作成します。

2.  \[**パブリック名**\] に「lyncdiscover.contoso.com」と入力します。

3.  \[**ブリッジ**\] タブで、要求をポート 80 からポート 8080 に橋渡しするオプションのみを選択します。

4.  \[**認証**\] タブで、\[**認証なし**\] および \[**クライアントは直接認証できません**\] を選択します。

5.  変更を確定し、ルールを Lync ルールのリストの一番上 (処理順序の 1 番目) に移動します。

## 分割ドメイン展開でのモビリティ

共有済みの SIP アドレス スペースは、*分割ドメイン*または*ハイブリッド展開*とも呼ばれる構成で、ユーザーは社内展開とオンライン展開をまたいで展開されます。この構成では、ホーム サーバーの設置場所 (社内またはオンラインのどちらであるか) に関係なく、展開にログインしたユーザーは、そのホーム サーバーの設置場所にリダイレクトされることが望まれます。これを達成するために、Microsoft Lync Server 2013 の自動検出を使用して、オンライン ユーザーはオンライン トポロジにリダイレクトされます。このリダイレクトを行うには、Lync Server 管理シェルで **Get-CsHostingProvider** および **Set-CsHostingProvider** コマンドレットを使用して自動検出の Uniform Resource Locator (URL) を構成します。

次の展開属性を収集して記録する必要があります。

  - Lync Server 管理シェルで、次のように入力します。
    
        Get-CsHostingProvider

  - 実行結果から、**ProxyFQDN** 属性を持つオンライン プロバイダー (たとえば、sipfed.online.lync.com) を見つけます。

  - ProxyFQDN の値を記録します。

  - 社内の Lync Server コントロール パネルでフェデレーションを有効にします。オンライン プロバイダーとのフェデレーションが可能になります。

  - オンライン プロバイダーに対してフェデレーションを有効にします。既定では、ドメイン フェデレーションに対してすべてのオンライン ユーザーが有効になり、すべてのドメインと通信できます。

  - 禁止ドメインと許可ドメインを定義する場合は、明示的に許可するドメイン、または明示的に禁止するドメインを決めます。

  - オンライン フェデレーションの場合、ファイアウォールに期待する動作、証明書、および DNS ホスト (A、または IPv6 を使用する場合は AAAA) レコードを計画する必要があります。また、フェデレーション ポリシーを構成する必要もあります。詳細については、「[Lync Server と Office Communications Server のフェデレーションの計画](lync-server-2013-planning-for-lync-server-and-office-communications-server-federation.md)」を参照してください。

