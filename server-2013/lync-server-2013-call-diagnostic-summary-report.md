﻿---
title: 'Lync Server 2013: 通話診断の概要レポート'
TOCTitle: 通話診断の概要レポート
ms:assetid: 9091de56-13e6-440e-9353-f57c10c906fe
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Gg615016(v=OCS.15)
ms:contentKeyID: 48272835
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 の通話診断の概要レポート

 

_**トピックの最終更新日:** 2015-03-09_

通話診断の概要レポートでは、失敗したピアツーピア セッションや会議セッションの概要を確認できます。このレポートでは、両方の種類のセッション全体のエラー率が表示され、エラー情報がセッション モダリティごとに分類されます。

  - インスタント メッセージング

  - アプリケーション共有

  - ファイル送信

  - 音声

  - ビデオ

## 通話診断の概要レポートへのアクセス

通話診断の概要レポートには、監視レポートのホーム ページからアクセスします。 [Lync Server 2013 のピアツーピア アクティビティ診断レポート](lync-server-2013-peer-to-peer-activity-diagnostic-report.md)には、通話診断の概要レポートからアクセスできます。そのためには、レポートの \[ピアツーピア セッションの概要\] セクションにある \[エラー率\] 指標をクリックします。また、以下のいずれかの会議の指標をクリックして、 [Lync Server 2013 の電話会議診断レポート](lync-server-2013-conference-diagnostic-report.md)にアクセスすることもできます。

  - \[全体的なセッション エラー率\]

  - \[フォーカス エラー率\]

  - \[MCU エラー率\]

## 通話診断の概要レポートの活用

通話診断の概要レポートには、 Microsoft Lync Server 2013 で使用されるさまざまなモダリティのエラー率を比較するグラフが含まれています。これらのグラフ内の列は、実際にはホットリンクになっています。たとえば、ピアツーピア セッションの \[インスタント メッセージング\] 列をクリックすると、 [Lync Server 2013 のピアツーピア アクティビティ診断レポート](lync-server-2013-peer-to-peer-activity-diagnostic-report.md)のインスタンスにドリルダウンします。このレポートは、通話診断の概要レポートに含まれるすべてのインスタンス メッセージング セッションに関する詳細を提供します。

## フィルター

フィルターは、細かく絞り込んだデータ セットを返したり、返されたデータをさまざま方法で表示したりする方法として利用できます。たとえば、通話診断の概要レポートでは、セッションで使用されるレジストラー プールやエッジ プールのような要素をフィルターできます。また、データをグループ化する方法を選択することもできます。この場合は、通話が、時間、日、週、または月の単位でグループ化されます。

次の表に、通話診断の概要レポートで使用できるフィルターを示します。

### 通話診断の概要レポートのフィルター

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>名前</th>
<th>説明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>[ <strong>開始</strong> ]</p></td>
<td><p>時間範囲の開始日と開始時刻。データを時間単位で表示するには、次のように開始日と開始時刻の両方を入力します。</p>
<p>7/7/2012 1:00 PM</p>
<p>開始時刻を入力しないと、レポートは自動的に指定日の午前 12:00 に開始します。データを日単位で表示するには、次のように日付のみを入力します。</p>
<p>07.07.12</p>
<p>週単位または月単位で表示するには、表示する週または月の任意の日付を入力します (その週または月の最初の日である必要はありません)。</p>
<p>03.07.12</p>
<p>一週間は、日曜日から始まり、土曜日で終わるものとします。</p></td>
</tr>
<tr class="even">
<td><p>[ <strong>終了</strong> ]</p></td>
<td><p>時間範囲の終了日と終了時刻。データを時間単位で表示するには、次のように終了日と終了時刻の両方を入力します。</p>
<p>7/7/2012 1:00 PM</p>
<p>終了時刻を入力しないと、レポートは自動的に指定日の午前 12:00 に終了します。データを日単位で表示するには、次のように日付のみを入力します。</p>
<p>07.07.12</p>
<p>週単位または月単位で表示するには、表示する週または月の任意の日付を入力します (その週または月の最初の日である必要はありません)。</p>
<p>03.07.12</p>
<p>一週間は、日曜日から始まり、土曜日で終わるものとします。</p></td>
</tr>
<tr class="odd">
<td><p>[ <strong>間隔</strong> ]</p></td>
<td><p>時間間隔です。次のいずれかを選択します。</p>
<ul>
<li><p>時間単位 (最大 25 時間の表示が可能)</p></li>
<li><p>日単位 (最大 31 日の表示が可能)</p></li>
<li><p>週単位 (最大 12 週の表示が可能)</p></li>
<li><p>月単位 (最大 12 か月の表示が可能)</p></li>
</ul>
<p>入力した開始日と終了日が選択した間隔で使用できる値の最大数を超える場合は、最大数の値 (開始日からカウント) のみが表示されます。たとえば、開始日と終了日をそれぞれ 7/7/2012 (2012 年 7 月 7 日)、2/28/2012 (2012 年 2 月 28 日) として毎日の間隔を選択しても、2012 年 8 月 7 日の午前 12:00 から 2012 年 9 月 7 日の午前 12:00 までの日付のデータ (つまり、合計 31 日分のデータのみ) が表示されることになります。</p></td>
</tr>
<tr class="even">
<td><p>[ <strong>プール</strong> ]</p></td>
<td><p>レジストラー プールまたはエッジ サーバーの完全修飾ドメイン名 (FQDN)。個別のプールを選択するか、[ <strong>すべて</strong> ] をクリックしてすべてのプールのデータを表示できます。このドロップダウン リストは、データベース内のレコードに基づいて自動的に設定されます。</p></td>
</tr>
</tbody>
</table>


## ピアツーピア セッションの指標

次の表に、ピアツーピア セッション (参加者が 2 人だけのセッション) の通話診断の概要レポートで提供される情報を示します。

### ピアツーピア セッションの指標

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>名前</th>
<th>この項目での並べ替え</th>
<th>説明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>[ <strong>セッションの合計数</strong> ]</p></td>
<td><p>×</p></td>
<td><p>実施されたピアツーピア セッションの総数です。</p></td>
</tr>
<tr class="even">
<td><p>[ <strong>エラー率</strong> ]</p></td>
<td><p>×</p></td>
<td><p>エラーが発生したピアツーピア セッションの割合です。この項目をクリックすると、このレポートでは、エラーが発生したピアツーピア セッションに関する詳細情報を示すピアツーピア アクティビティ診断レポートが表示されます。</p></td>
</tr>
</tbody>
</table>


## 電話会議セッションの指標

次の表に、電話会議セッション (参加者が 3 人以上のセッション) の通話診断レポートで提供される情報を示します。

### 電話会議セッションの指標

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>名前</th>
<th>この項目での並べ替え</th>
<th>説明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>[ <strong>電話会議の合計数</strong> ]</p></td>
<td><p>×</p></td>
<td><p>実施された電話会議の総数です。</p></td>
</tr>
<tr class="even">
<td><p>[ <strong>電話会議セッションの合計数</strong> ]</p></td>
<td><p>×</p></td>
<td><p>実施された電話会議セッションの総数です。</p></td>
</tr>
<tr class="odd">
<td><p>[ <strong>全体的なセッション エラー率</strong> ]</p></td>
<td><p>×</p></td>
<td><p>エラーが発生した電話会議セッション総数の割合です。</p></td>
</tr>
<tr class="even">
<td><p>[ <strong>フォーカス セッション</strong> ]</p></td>
<td><p>×</p></td>
<td><p>エラーが発生したフォーカス ベース電話会議セッションの総数です。</p></td>
</tr>
<tr class="odd">
<td><p>[ <strong>フォーカス エラー率</strong> ]</p></td>
<td><p>×</p></td>
<td><p>エラーが発生したフォーカス ベース電話会議セッションの割合です。</p></td>
</tr>
<tr class="even">
<td><p>[ <strong>MCU セッション</strong> ]</p></td>
<td><p>×</p></td>
<td><p>エラーが発生した、会議サーバー (以前の Multipoint Control Unit (MCU)) ベースの電話会議の総数です。</p></td>
</tr>
<tr class="odd">
<td><p>[ <strong>MCU エラー率</strong> ]</p></td>
<td><p>×</p></td>
<td><p>エラーが発生した、会議サーバー (以前の Multipoint Control Unit (MCU)) ベースの電話会議の割合です。</p></td>
</tr>
</tbody>
</table>
