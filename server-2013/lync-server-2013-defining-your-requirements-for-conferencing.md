﻿---
title: 'Lync Server 2013: 会議の要件の定義'
TOCTitle: 会議の要件の定義
ms:assetid: 5c83e268-22bf-42b2-bac3-3237b5e02e03
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ204935(v=OCS.15)
ms:contentKeyID: 48272208
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 での会議の要件の定義

 

_**トピックの最終更新日:** 2012-09-30_

どの会議機能を展開するかを決定するときには、ユーザーに提供したい機能とネットワーク帯域幅の能力を考慮する必要があります。次に示す質問の一覧では、組織の要件に基づいて展開する必要のある会議機能を決定するための会議計画プロセスを辿ります。

  - **ドキュメントのコラボレーションやアプリケーション共有を含む Web 会議を有効にしますか。**
    
    その場合は、フロント エンド プールまたはMicrosoft Lync Server 2013、計画ツールのトポロジ ビルダーで会議を有効にする必要があります。会議を有効にすると、Web 会議と音声ビデオ会議の両方が有効になります。
    
    アプリケーション共有では、ドキュメントのコラボレーションよりも多くのネットワーク帯域幅を使用する必要があります。Lync Server 2013 は、各アプリケーション共有セッションを制御するための制限メカニズムを提供します。既定では、セッションあたり 1.5 KB/秒に設定されます。
    
    アプリケーション共有は有効にせず、ドキュメントのコラボレーションを有効にする場合は、会議を有効にし、会議ポリシーを使用してアプリケーション共有を無効にすることができます。会議ポリシーの構成の詳細については、「[Lync Server 2013 での会議ポリシー](lync-server-2013-conferencing-policies.md)」を参照してください。
    
    ユーザーが PowerPoint プレゼンテーションを共有できるようにするには、Office Web Apps サーバー を構成する必要があります。Office Web Apps サーバー の構成の詳細については、「[Lync Server 2013 と Office Web Apps サーバーの統合の構成](lync-server-2013-enabling-office-web-apps-server-and-lync-server-2013.md)」を参照してください。

  - **音声ビデオ会議を有効にしますか。**
    
    その場合は、Lync Server 2013、計画ツールまたは トポロジ ビルダーの フロント エンド プールで会議を有効にする必要があります。会議を有効にすると、Web 会議と音声ビデオ会議の両方が有効になります。
    
    音声ビデオ会議では、Web 会議 (ドキュメントのコラボレーションやアプリケーション共有を含む) よりも多くのネットワーク帯域幅を使用する必要があります。音声ビデオ会議は有効にせず、Web 会議を有効にする場合は、会議を有効にし、会議ポリシーを使用して音声ビデオ会議を無効にすることができます。
    
    電話会議を有効にして、ビデオ会議は無効にする場合は、音声ビデオ会議を有効にし、会議ポリシーを使用してビデオ会議を使用できないようにすることができます。 あるいは、音声ビデオ会議を有効にして、特定のユーザーだけが音声ビデオ会議を開始または音声ビデオ会議に参加できるようにすることが可能です。
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>音声ビデオ会議を使用するために エンタープライズ VoIP は必要ありません。音声ビデオ会議を有効にすると、電話ソリューション用に PBX を使用していても、ユーザーはオーディオ デバイスがあればオーディオを会議に追加できます。</td>
    </tr>
    </tbody>
    </table>


  - **PSTN 電話を使用している場合、ユーザーが会議のオーディオ部分に参加できるようにしますか。**
    
    その場合は、ダイヤルイン会議を展開して有効にする必要があります。 組織内と外部の両方の招待ユーザーが、PSTN 電話を使用して会議のオーディオ部分に参加できるようになります。

  - **Lync Server 2013 クライアントの外部ユーザーが、有効にした種類の会議に参加できるようにしますか。**
    
    その場合は、エッジ サーバーを展開します。会議への参加を外部に許可すると、Lync Server 2013 への投資が最大限に発揮されます。たとえば、ラップトップを使用している Lync Server 2013 のユーザーは、自宅、空港、顧客サイトなど、どこにいても会議に参加できます。
    
    また、エッジ サーバーを展開していれば、顧客やベンダーなどの他の組織とフェデレーション関係を築くことができ、これらの組織のユーザーは、こちらのユーザーとより容易に共同作業を行うことができます。
    
    エッジ サーバーの展開の詳細については、「[Lync Server 2013 の外部ユーザー アクセスの計画](lync-server-2013-planning-for-external-user-access.md)」および「[Lync Server 2013 での外部ユーザー アクセスの展開](lync-server-2013-deploying-external-user-access.md)」を参照してください。Office Web Apps サーバー の外部アクセスの有効化の詳細については、「[Lync Server 2013 でリバース プロキシ サーバーを使用して Office Web Apps サーバーを公開する](lync-server-2013-publishing-office-web-apps-server-using-a-reverse-proxy-server.md)」を参照してください。

  - **Lync Server 2013 の会議に参加できるクライアントを制御しますか。**
    
    その場合は、サポートしたいクライアント オプションのみが利用可能になるように、ミーティング参加ページを構成します。予定されている会議に参加するためのリンクをユーザーがクリックするたびに、Lync Server 2013 は、コンピューター上に既にクライアントがインストールされているかどうかを検知します。そして、既定のクライアントを開始し、ミーティング参加ページを開きます。このページには代替クライアントのリンクが含まれています。ミーティング参加ページには、Microsoft Lync Web App を使用するためのオプションが常に含まれています。このオプションに加え、Attendee および以前のバージョンの Communicator のリンクを含めるかどうかを決めることができます。詳細については、「[Lync Server 2013 での会議参加ページの構成](lync-server-2013-configuring-the-meeting-join-page.md)」を参照してください。

## このセクション中

  - [Lync Server 2013 での Web 会議の要件](lync-server-2013-web-conferencing-requirements.md)

  - [Lync Server 2013 での音声ビデオ会議の要件](lync-server-2013-a-v-conferencing-requirements.md)

  - [Lync Server 2013 でのダイヤルイン会議の要件](lync-server-2013-dial-in-conferencing-requirements.md)

## 関連項目

#### その他のリソース

[Lync Server 2013 での会議の計画](lync-server-2013-planning-for-conferencing.md)  
[Lync Server 2013 の会議の展開チェックリスト](lync-server-2013-deployment-checklist-for-conferencing.md)

