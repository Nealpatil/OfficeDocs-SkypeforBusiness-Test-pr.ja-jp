﻿---
title: SEFAUtil ツールを展開する
TOCTitle: SEFAUtil ツールを展開する
ms:assetid: fb556e50-88dd-4404-a3d5-be36f5ba41e6
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ945659(v=OCS.15)
ms:contentKeyID: 52056757
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# SEFAUtil ツールを展開する

 

_**トピックの最終更新日:** 2016-12-08_

グループ通話ピックアップを展開および管理するには、SEFAUtil リソース キット ツールを使用する必要があります。このツールは Lync Server 2013 リソース キット ツールに含まれます。SEFAUtil をインストールするには、事前にトポロジに信頼済みアプリケーション プールがあり、SEFAUtil を信頼済みアプリケーションとして指定し、トポロジを有効にする必要があります。


> [!IMPORTANT]
> Microsoft Unified Communications Managed API (UCMA) 3.0 Core SDK を、SEFAUtil ツールを実行する予定のすべてのコンピューターにインストールする必要があります。



展開内のどのフロント エンド プールでも SEFAUtil を実行できます。

<table>
<thead>
<tr class="header">
<th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>SEFAUtil を実行する方法の詳細については、Technet ブログ記事「How to get SEFAutil running?」(<a href="http://go.microsoft.com/fwlink/?linkid=278940" class="uri">http://go.microsoft.com/fwlink/?linkid=278940</a>) を参照してください。</td>
</tr>
</tbody>
</table>


## SEFAUtil を展開するには

1.  Lync Server 管理シェルがインストールされているコンピューターに、RTCUniversalServerAdmins グループのメンバーとして、または「[Lync Server 2013 でのセットアップのアクセス許可の委任](lync-server-2013-delegate-setup-permissions.md)」に説明されている必要なユーザー権限を使用してログオンします。

2.  Lync Server 管理シェルを以下の手順で起動します。\[**スタート**\]、\[**すべてのプログラム**\]、\[**Microsoft Lync Server 2013**\]、\[**Lync Server 管理シェル**\] の順にクリックします。

3.  SEFAUtil ツールは、信頼済みアプリケーション プールに含まれるコンピューターでのみ実行できます。必要に応じて、SEFAUtil を実行する予定のフロント エンド プール用の信頼済みアプリケーション プールを定義します。コマンド ラインで、次のコマンドを実行します。
    
        New-CsTrustedApplicationPool -id <Pool FQDN> -Registrar <Pool Registrar FQDN> -site Site:<Pool Site>

4.  SEFAUtil ツールを信頼済みアプリケーションとして定義します。コマンド ラインで、次のコマンドを実行します。
    
        New-CsTrustedApplication -ApplicationId sefautil -TrustedApplicationPoolFqdn <Pool FQDN>  -Port 7489
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>必要に応じて、別のポートを使用できます。</td>
    </tr>
    </tbody>
    </table>


5.  変更を加えたトポロジを有効にします。コマンド ラインで、次のコマンドを実行します。
    
        Enable-CsTopology

6.  手順 3. で作成した信頼済みアプリケーション プール内のフロント エンド サーバーに Lync Server 2013 リソース キット ツールをインストールします。

7.  次のように、SEFAUtil ツールが正常に実行していることを確認します。
    
    1.  管理者特権で Windows コマンド プロンプトからツールを実行し、展開内のユーザーの着信転送設定を表示します。
        
        <table>
        <thead>
        <tr class="header">
        <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
        </tr>
        </thead>
        <tbody>
        <tr class="odd">
        <td>このツールは \Program Files\Microsoft Lync Server 2013\Reskit にあります。</td>
        </tr>
        </tbody>
        </table>
    
    2.  ユーザーの着信転送設定を表示します。コマンド ラインで、次のコマンドを実行します。
        
            SEFAUtil.exe <user SIP address> /server:<Lync Server/Pool FQDN>
        
        ユーザーの着信転送設定が表示されます。

