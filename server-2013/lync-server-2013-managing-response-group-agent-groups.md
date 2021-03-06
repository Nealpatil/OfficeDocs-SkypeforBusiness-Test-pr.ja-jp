﻿---
title: 応答グループ エージェント グループの管理
TOCTitle: 応答グループ エージェント グループの管理
ms:assetid: 36084cdc-38f1-4c45-922f-f81c7e86210c
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Gg520976(v=OCS.15)
ms:contentKeyID: 48271739
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 応答グループ エージェント グループの管理

 

_**トピックの最終更新日:** 2012-10-01_

エージェント グループは、応答グループへの通話に応答するように指定されているユーザーのグループから構成されます。エージェント グループを作成するときは、そのグループに割り当てるエージェントを選択し、詳細なグループ設定 (ルーティング方法、エージェントがグループにサインイン/サインアウトするかどうかなど) を指定します。

<table>
<thead>
<tr class="header">
<th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>ユーザーをエージェント グループに追加するには、ユーザーをエンタープライズ VoIP に対して有効にする必要があります。エンタープライズ VoIP に対してユーザーを有効にする方法の詳細については、「<a href="lync-server-2013-enable-users-for-enterprise-voice.md">Lync Server 2013 でのエンタープライズ VoIP に対するユーザーの有効化</a>」を参照してください。</td>
</tr>
</tbody>
</table>


<table>
<thead>
<tr class="header">
<th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>社内ユーザーのみがエージェントであることができます。エージェントが社内からオンラインに移動した場合、応答グループ呼び出しはそのエージェントに送られません。</td>
</tr>
</tbody>
</table>


Lync Server へのサインイン/サインアウトとは別に、グループにサインイン/サインアウトする必要があるエージェントを公式エージェントと呼びます。公式エージェントが、グループにルーティングされた着信を受信するには、そのグループにサインインする必要があります。これは、パートタイム ベースでグループから通話に応答するエージェントには便利な方法です。公式エージェントは、Lync 2013 でメニュー項目をクリックして Windows Internet Explorer インターネット ブラウザーを起動し Web ページ コンソールを表示して、グループにサインイン/サインアウトします。

グループにサインインもサインアウトもしていないエージェントを、非公式エージェントと呼びます。非公式エージェントは、Lync Server にサインインすると、自動的にそのグループにサインインします。また、非公式エージェントはグループからサインアウトすることはできません。


> [!IMPORTANT]
> ユーザーを応答グループ エージェントとして割り当てる場合、ユーザーがプライバシー モードを有効にしているのであれば、"RGS Presence Watcher" 連絡先を検索して連絡先リストに追加する必要があることを通知してください。プライバシー モードを有効にしているが連絡先リストに RGS Presence Watcher がないエージェントは、応答グループに対する通話を受信できません。プライバシー モードを有効にしていないエージェントは、影響されません。



## このセクション中

  - [Lync Server 2013 エージェント グループの作成または変更](lync-server-2013-create-or-modify-an-agent-group.md)

  - [エージェント グループの削除](lync-server-2013-delete-an-agent-group.md)

