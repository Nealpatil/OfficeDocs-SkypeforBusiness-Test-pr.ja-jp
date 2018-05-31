﻿---
title: 'Lync Server 2013: SIP トランクの展開チェックリスト'
TOCTitle: SIP トランクの展開チェックリスト
ms:assetid: 94f4f03e-19d5-4198-92be-e4076dbb959a
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Gg398755(v=OCS.15)
ms:contentKeyID: 48272893
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 に関する SIP トランクの展開チェックリスト

 

_**トピックの最終更新日:** 2012-09-21_

SIP トランクを展開する前に、ユーザーとサービス プロバイダーは、SIP トランク エンドポイントに関する各自の基本的な接続情報を交換する必要があります。

接続する各 ITSP ゲートウェイについて以下の情報を取得してください。

  - IP アドレス

  - 完全修飾ドメイン名 (FQDN)

<table>
<thead>
<tr class="header">
<th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>サービス プロバイダーから、複数の ITSP ゲートウェイに接続するよう求められることがあります。その場合は、各 ITSP ゲートウェイとプール内の各 仲介サーバー間の接続を構成する必要があります。</td>
</tr>
</tbody>
</table>


サービス プロバイダーに渡す情報は、ご使用の SIP トランク接続の種類によって異なります。

  - Multiprotocol Label Switching (MPLS) またはプライベート ネットワーク接続の場合は、境界ネットワーク (DMZ、非武装地帯、およびスクリーン サブネットとも呼ばれる) 内のルーターのパブリック ルーティング可能な IP アドレスを ITSP に渡します。ITSP のゲートウェイまたはセッション ボーダー コントローラー (SBC) がこのアドレスに接続できることを確認してください。 仲介サーバーの FQDN も ITSP に渡してください。

  - 仮想プライベート ネットワーク (VPN) 接続の場合は、VPN サーバーの IP アドレスを ITSP に渡します。

## 証明書に関する考慮事項

SIP トランキング用の証明書が必要かどうかを判断するには、どのプロトコルがサポートされているのかを ITSP に確認してください。

1.  ITSP が伝送制御プロトコル (TCP) のみをサポートしている場合、証明書は不要です。

2.  ITSP がトランスポート層セキュリティ (TLS) をサポートしている場合、ITSP から証明書を取得する必要があります。

<table>
<thead>
<tr class="header">
<th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>SIP は、リアルタイム転送プロトコル (RTP) またはセキュア リアルタイム転送プロトコル (SRTP) (ボイス オーバー IP (VoIP) 通話の実際の音声データを管理するプロトコル) と共に動作します。</td>
</tr>
</tbody>
</table>


## 展開プロセス

SIP トランク接続の Lync Server 側を実装するには、以下の手順に従います。

1.  Lync Serverトポロジ ビルダーを使用して、SIP ドメイン トポロジを作成、構成します。詳細については、「展開」のドキュメントの「[Lync Server 2013 のトポロジ ビルダーでのトポロジの定義と構成](lync-server-2013-define-and-configure-a-topology-in-topology-builder.md)」を参照してください。

2.  Lync Server コントロール パネルを使用して、新しい SIP ドメインの音声ルーティングを構成します。詳細については、「展開」のドキュメントの「[Lync Server 2013 でのトランクの構成](lync-server-2013-configuring-trunks.md)」を参照してください。

3.  **Test-CsPstnOutboundCall** コマンドレットを使用して、接続をテストします。詳細については、 Lync Server 管理シェルのドキュメントまたは Lync Server 管理シェルのヘルプを参照してください。
