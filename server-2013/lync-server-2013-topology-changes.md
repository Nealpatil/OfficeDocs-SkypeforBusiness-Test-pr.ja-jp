﻿---
title: 'Lync Server 2013: トポロジの変更'
TOCTitle: トポロジの変更
ms:assetid: 9e40ef93-9ab0-498c-9bbf-f94584353e53
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ688153(v=OCS.15)
ms:contentKeyID: 49887071
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 のトポロジの変更

 

_**トピックの最終更新日:** 2012-10-02_

Lync Server 2013 では、以前のリリースとはトポロジの要件と考慮事項が異なります。ここでは、それらの違いについて説明します。

## 新しいフロントエンド プール アーキテクチャ

Lync Server 2013 では、 Enterprise Editionフロント エンド プールのアーキテクチャが分散システム アーキテクチャに変更されました。

この新しいアーキテクチャでは、バック エンド データベースはプールのリアルタイム データ ストアではなくなりました。特定のユーザーに関する情報は、プールの 3 つのフロントエンド サーバーで保持されます。各ユーザーに対して、1 つのフロントエンド サーバーがそのユーザーの情報のマスターとして機能し、他の 2 つのフロントエンド サーバーがレプリカとして機能します。フロントエンド サーバーがダウンすると、レプリカとして機能していた別のフロントエンド サーバーが自動的にマスターに昇格します。

この操作は内部で行われるため、どのフロントエンド サーバーがどのユーザーのマスターになっているかを管理者が知る必要はありません。このデータ ストレージの分散により、プール内のパフォーマンスとスケーラビリティが向上し、単一の バック エンド サーバーの単一障害点が取り除かれます。

バック エンド サーバーは、ユーザー データと会議データのバックアップ ストレージとして機能します。バック エンド サーバーは、応答グループ データベースなどの他のデータベースのプライマリ ストレージでもあります。

これらの強化により、プールの計画および保守の方法も変わります。すべての Enterprise Editionフロント エンド プールに少なくとも 3 つのフロントエンド サーバーを含めることをお勧めします。これにより、 フロント エンド プールのアーキテクチャで想定されている数のレプリカを提供できます。また、 フロント エンド プールのサーバーを追加、削除、またはアップグレードするときには、特定の手順に従う必要があります。詳細については、「[Lync Server 2013 フロントエンド サーバー、インスタント メッセージングおよびプレゼンスのトポロジおよびコンポーネント](lync-server-2013-topologies-and-components-for-front-end-servers-instant-messaging-and-presence.md)」を参照してください。

## サーバーの役割のトポロジの変更

これまで個別のサーバーで実行されていたいくつかのサーバーの役割がフロントエンド サーバーの役割に統合され、ハードウェアのコストを節約できます。

  - Lync Server 2013 では、音声ビデオ会議サーバーは、常に、フロントエンド サーバーと併置されます。

  - 監視とアーカイブのフロントエンドは、常にフロントエンド サーバーと併置されるようになりました。監視とアーカイブは、それぞれ個別のバック エンド データベースが引き続き必要ですが、これはフロントエンド プールのバック エンド データベースと同じサーバーに併置するか、個別のバック エンド サーバーでホストできます。

  - 常設チャット サーバーはサーバーの役割になっています。 Microsoft Lync Server 2010 では、 グループ チャット サーバー は Microsoft Lync Server 2010 用の信頼されたサードパーティ アプリケーションでした。 Lync Server 2013 では、 常設チャット サーバーの機能は 3 つの新しいサーバーの役割を使用して実装されています。
    
      - **PersistentChatService :** フロントエンドの役割として実装された 常設チャット サーバーの中心となるサービスです
    
      - **PersistentChatStore :** バック エンド サーバーの役割です
    
      - **PersistentChatComplianceStore :** 常設チャット コンプライアンスのためのバック エンド サーバーの役割です

