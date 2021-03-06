﻿---
title: 'Lync Server 2013: 場所ポリシーの定義'
TOCTitle: 場所ポリシーの定義
ms:assetid: da3cca7f-f6e5-4b6f-90a1-2008e3dd1ebd
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Gg398962(v=OCS.15)
ms:contentKeyID: 48273813
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 の場所ポリシーの定義

 

_**トピックの最終更新日:** 2012-10-29_

場所ポリシーにはそれぞれ、以下の情報が含まれています。

  - **緊急サービスへの対応有効**  
    この値を \[**はい**\] に設定すると、クライアントが E9-1-1 に対して有効になります。クライアントは、登録時に 場所情報サービスから場所の取得を試み、緊急電話の一部として場所情報を組み込みます。

<!-- end list -->

  - **場所必須**  
    この設定は、\[**緊急サービスへの対応有効**\] が \[**はい**\] に設定されている場合にのみ使用されます。
    
    \[**場所 (必須)**\] 設定を構成して、クライアントの動作を定義できます。値を \[**いいえ**\] に設定すると、ユーザーは場所の入力を求められません。値を \[**はい**\] に設定すると、ユーザーは場所の入力を求められますが、入力せずにプロンプトを閉じることもできます。値を \[**免責事項**\] に設定すると、ユーザーは場所の入力を求められ、入力せずにプロンプトを閉じようとすると免責事項が表示されます。いずれの場合でも、ユーザーはクライアントを引き続き使用できます。
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>E9-1-1 への対応が有効でない場合に、ユーザーが場所を手動で入力すると、免責事項テキストは表示されません。免責事項が既に表示されたユーザーには、免責事項テキストの更新は表示されません。</td>
    </tr>
    </tbody>
    </table>


<!-- end list -->

  - **拡張緊急サービス免責事項**  
    この設定は、ユーザーが場所を入力せずにプロンプトを閉じた場合に表示される免責事項を指定します。 Lync Server 2013 では、場所のポリシーを使用して、異なるロケールまたは異なるユーザー セット向けの別の免責事項を設定できます。
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>この場所ポリシーの設定は、 <strong>Set-CsEnhancedEmergencyServiceDisclaimer</strong> コマンドレットを使用して組織全体のグローバル免責事項を設定していた Lync Server 2010 のものとは異なります。グローバル免責事項が既に存在する場合は、場所ポリシーでその免責事項を指定する必要があります。つまり、 Lync Server 2013 は、場所ポリシーで指定された免責事項だけを使用します。</td>
    </tr>
    </tbody>
    </table>


<!-- end list -->

  - **緊急ダイヤル文字列**  
    このダイヤル文字列 (先頭の「+」を省き、Lync ユーザーのダイヤル プランによって行われる正規化をすべて含めます) は、通話が緊急電話であることを表します。 **緊急ダイヤル文字列**を使用すると、クライアントによって場所とコールバック情報が緊急電話に含まれるようになります。
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>組織が外線アクセス プレフィックスを使用しない場合、対応するダイヤル プラン正規化ルールを作成する必要はありません。ダイヤル プラン正規化ルールでは、Lync プール サーバー上の発信ルーティングに通話を送信する前に、緊急電話番号の文字列に「+」を追加します。この「+」は、場所ポリシーの結果として Lync クライアントによって自動的に先頭に付加されます。サイトが外部アクセス プレフィックスを使用する場合、適用されるダイヤル プラン ポリシーに正規化ルールを追加して、外部アクセス プレフィックスを省き、「+」を追加するように設定する必要があります。たとえば、場所が外部アクセス プレフィックスとして 9 を使用しており、ユーザーが 9 911 をダイヤルして緊急電話を発信する場合、この番号が発信者の場所プロファイルのルートによって評価される前に、クライアントはダイヤル プラン ポリシーを使用して、この番号を +911 に正規化します。</td>
    </tr>
    </tbody>
    </table>


<!-- end list -->

  - **緊急ダイヤル文字列マスク**  
    特定の **緊急ダイヤル文字列**に変換されるダイヤル文字列の一覧です。この一覧のダイヤル文字列は、セミコロンで区切られています。たとえば、ヨーロッパの大部分で緊急サービス番号として使用されている 112 を追加します。ヨーロッパから訪れている Lync ユーザーは、米国の緊急電話番号である 911 がわからないかもしれませんが、112 をダイヤルして緊急電話に発信することができます。緊急ダイヤル文字列については、各番号の前に「+」を付けないでください。また、外線アクセス コードを使用する場合、ユーザーのダイヤル プラン ポリシーにアクセス コードの数字を取り除く正規化ルールがあることを確認してください。

<!-- end list -->

  - **PSTN の使用法**  
    PSTN 使用法の名前です。PSTN 使用法には、緊急電話がどの SIP トランク、PSTN ゲートウェイ、または ELIN ゲートウェイを通るかを決定するルーティング パスが含まれます。
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>場所ポリシーに割り当てられる使用法は 1 つだけです。この PSTN 使用法は、ユーザーの音声ポリシーに割り当てられた PSTN 使用法より優先されますが、緊急ダイヤル文字列または緊急ダイヤル文字列マスクの 1 つに発信する通話にのみ適用されます。</td>
    </tr>
    </tbody>
    </table>


<!-- end list -->

  - **通知 URI**  
    緊急電話が発信されたときに、インスタント メッセージング (IM) 通知を受信するセキュリティ担当者の 1 つ以上の SIP URI を指定します。配布グループがサポートされています。

<!-- end list -->

  - **電話会議 URI**  
    緊急電話が発信されたときに、参加することが必要な DID (Direct Inward Dialing) の番号 (通常はセキュリティ デスクの電話番号) を指定します。

<!-- end list -->

  - **会議モード**  
    会議 URI が単方向または双方向の通信を使用して緊急電話に参加するかどうかを指定します。

<!-- end list -->

  - **場所の更新間隔**  
    場所情報サービスの場所の更新に対するクライアント要求の時間間隔 (時間) を指定します。値は、1 ～ 12 の範囲で任意の値に設定できます。既定値は 4 です。

