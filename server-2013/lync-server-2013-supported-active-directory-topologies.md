﻿---
title: 'Lync Server 2013: サポートされている Active Directory トポロジ'
TOCTitle: サポートされている Active Directory トポロジ
ms:assetid: 0c76b778-7652-4eb0-b161-86f2d4a94ccf
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Gg398173(v=OCS.15)
ms:contentKeyID: 48271238
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 でサポートされている Active Directory トポロジ

 

_**トピックの最終更新日:** 2016-12-08_

Lync Server 2013 は、Microsoft Lync Server 2010 および Microsoft Office Communications Server 2007 R2 と同じ Active Directory ドメイン サービス トポロジをサポートします。次のトポロジがサポートされています。

  - 単一のドメインを含む単一のフォレスト

  - 単一のツリーと複数のドメインを含む単一のフォレスト

  - 複数のツリーと不整合の名前空間を含む単一のフォレスト

  - 中央フォレスト トポロジの複数のフォレスト

  - リソース フォレスト トポロジの複数のフォレスト

  - Exchange Online を使用する Lync リソース フォレスト トポロジの複数のフォレスト

次の図に、このセクションで使用されるアイコンを示します。

**トポロジに関する重要点**

![トポロジに関する重要点](images/Gg398173.0c3cc89f-6c43-4bc8-b2ec-61d89e391ee9(OCS.15).jpg "トポロジに関する重要点")

## 単一フォレスト、単一ドメイン

Lync Server でサポートされている最も単純な Active Directory トポロジである単一ドメイン フォレストは、一般的なトポロジです。

次の図に、単一ドメインの Active Directory トポロジでの Lync Server の展開を示します。

**単一ドメイン トポロジ**

![単一ドメイン トポロジ](images/Gg398173.258b3b3f-0558-4a36-a4c2-031be7299668(OCS.15).jpg "単一ドメイン トポロジ")

## 単一フォレスト、複数ドメイン

Lync Server でサポートされる別の Active Directory トポロジは、ルート ドメインと 1 つ以上の子ドメインで構成される単一フォレストです。このタイプの Active Directory トポロジでは、Lync Server を展開するドメインとは別のドメインにユーザーを作成できます。ただし、フロントエンド プールを展開する場合、プール内のすべてのフロントエンド サーバーを 1 つのドメインに展開する必要があります。Lync Server は Windows ユニバーサル管理者グループをサポートしているので、複数のドメインにわたる管理を行うことができます。

次の図に、複数のドメインを持つ単一フォレストの展開を示します。この図では、ユーザー アイコンはユーザー アカウントが所属するドメインを示し、矢印は Lync Server プールが存在するドメインを指しています。ユーザー アカウントには次の種類があります。

  - Lync Server プールと同じドメインのユーザー アカウント

  - Lync Server プールとは別のドメインのユーザー アカウント

  - Lync Server プールがあるドメインの子ドメインのユーザー アカウント

**複数のドメインが含まれる単一のフォレスト**

![複数のドメインが含まれる単一のフォレスト](images/Gg398173.2b809c72-c3cd-4fad-afe6-8c2dae779750(OCS.15).jpg "複数のドメインが含まれる単一のフォレスト")

## 単一フォレスト、複数ツリー

複数ツリーのフォレスト トポロジは、独立したツリー構造を定義し、Active Directory 名前空間を分ける 2 つ以上のドメインで構成されます。

次の図に、複数のツリーがある単一のフォレストを示します。この図では、ユーザー アイコンはユーザー アカウントが所属するドメインを示しており、実線は同じドメインまたは別のドメインに存在する Lync Server プールを、破線は別のツリーに存在する Lync Server プールをそれぞれ指しています。ユーザー アカウントには次の種類があります。

  - Lync Server プールと同じドメインのユーザー アカウント

  - Lync Server プールとは別のドメイン (ただし、ツリーは同じ) のユーザー アカウント

  - Lync Server プールとは別のツリーのユーザー アカウント

**複数のツリーが含まれる単一のフォレスト**

![複数のツリーが含まれる単一のフォレスト](images/Gg398173.db30fa49-174a-4974-8695-41dd78e39432(OCS.15).jpg "複数のツリーが含まれる単一のフォレスト")

## 複数フォレスト、中央フォレスト

Lync Server は、中央フォレスト トポロジで構成される複数のフォレストをサポートします。中央フォレスト トポロジでは、中央フォレスト内の連絡先オブジェクトを使用して、他のフォレスト内のユーザーを表します。中央フォレストは、フォレスト内のすべてのユーザーのユーザー アカウントもホストします。Microsoft Identity Integration Server (MIIS)、Microsoft Forefront Identity Manager (FIM) 2010、または Microsoft Identity Lifecycle Manager (ILM) 2007 Feature Pack 1 (FP1) などのディレクトリ同期製品は、組織内のユーザー アカウントのライフ サイクルを管理します。いずれかのフォレストで新しいユーザー アカウントが作成されるか、フォレストからユーザー アカウントが削除されると、ディレクトリ同期製品が、中央フォレスト内の対応する連絡先を同期します。

中央フォレストには、次に示す利点があります。

  - Lync Server を実行するサーバーを、単一のフォレストで集中管理します。

  - ユーザーは、任意のフォレストのユーザーを検索して通信できます。

  - ユーザーは、任意のフォレストの他のユーザーのプレゼンスを表示できます。

  - ユーザー アカウントが作成または削除されると、ディレクトリ同期製品によって、中央フォレストの連絡先オブジェクトが自動的に追加および削除されます。

次の図に、中央フォレスト トポロジを示します。この図では、中央フォレスト内の Lync Server をホストするドメインと、別のフォレスト内のユーザー ドメインとの間に、双方向の信頼関係があります。別のユーザー フォレストのスキーマは、拡張する必要がありません。

**中央フォレスト トポロジ**

![中央フォレスト トポロジ](images/Gg398173.7feb049a-453b-4134-9128-873b83ee1755(OCS.15).jpg "中央フォレスト トポロジ")

## 複数フォレスト、リソース フォレスト

リソース フォレスト トポロジでは、1 つのフォレストが、Microsoft Exchange Server や Lync Server などのサーバー アプリケーションの実行専用となります。リソース フォレストは、サーバー アプリケーションとアクティブ ユーザー オブジェクトの同期表現をホストしますが、ログオン可能なユーザー アカウントはホストしません。リソース フォレストは、ユーザー オブジェクトが存在する他のフォレストのための共有サービス環境として動作します。ユーザー フォレストは、リソース フォレストとの間にフォレスト レベルの信頼関係を持ちます。このタイプのトポロジで Lync Server を展開するときは、リソース フォレストの中に、ユーザー フォレストのすべてのユーザー アカウントで使用される無効なユーザー オブジェクトを 1 つ作成します。Microsoft Exchange がリソース フォレストに既に展開されている場合は、無効なユーザー アカウントが既に存在している可能性があります。MIIS、Microsoft Forefront Identity Manager (FIM) 2010、または Microsoft Identity Lifecycle Manager (ILM) 2007 Feature Pack 1 (FP1) などのディレクトリ同期製品は、ユーザー アカウントのライフ サイクルを管理します。いずれかのユーザー フォレストで新しいユーザー アカウントが作成されるか、フォレストからユーザー アカウントが削除されると、ディレクトリ同期製品がリソース フォレスト内の対応するユーザー表現を同期します。

このトポロジは、組織のサービスに対して、複数のフォレストを管理する共有インフラストラクチャを提供するためや、Active Directory オブジェクトの管理を他の管理から切り離すために使用できます。セキュリティ上の理由から Active Directory の管理を分離する必要がある会社は、多くの場合、このトポロジを選択します。

このトポロジには、Active Directory スキーマの拡張の必要性が単一のフォレスト (リソース フォレスト) に限定されるという利点があります。

次の図に、リソース フォレスト トポロジを示します。

**リソース フォレスト トポロジ**

![Active Directory リソース フォレスト トポロジ](images/Gg398173.54ab82f1-e9e5-40f0-a54e-86e340b65c2a(OCS.15).jpg "Active Directory リソース フォレスト トポロジ")

## Exchange Online を使用する Lync リソース フォレスト トポロジの複数フォレスト

このトポロジでは、1 つ以上のフォレストが社内にあり、Active Directory ユーザー アカウントのホストを専用で行います。リソース フォレストは社外にあり、サードパーティ ホスティング プロバイダーによって管理されます。リソース フォレストは、Lync Server の展開および社内ユーザー アカウント フォレストからの同期されたユーザー アカウントのレプリケーションのみを含んでいます。また、ログオンできるユーザー アカウントは含んでいません。Exchange は、Exchange Online (ハイブリッド) と共に統合された社内ユーザー アカウント フォレストに、または Exchange Online により排他的に提供される社内ユーザー アカウント用電子メール サービスに展開されます。

リソース フォレストは、ユーザー オブジェクトが存在する社内 Active Directory 用の共有サービス環境として機能します。ユーザー アカウント フォレストは、リソース フォレストと一方向のフォレストレベル信頼関係を持っています。このタイプのトポロジに Lync Server を展開するときは、ユーザー フォレストのユーザー アカウントごとにリソース フォレスト内に 1 つの無効化されたユーザー オブジェクトを作成します。MIIS、Microsoft Forefront Identity Manager (FIM) 2010、または Microsoft Identity Lifecycle Manager (ILM) 2007 Feature Pack 1 (FP1) などのディレクトリ同期製品は、ユーザー アカウントのライフ サイクルを管理します。 いずれかのユーザー フォレストで新しいユーザー アカウントが作成されるか、フォレストからユーザー アカウントが削除されると、ディレクトリ同期製品がリソース フォレスト内の対応するユーザー表現を同期します。複数フォレスト展開を構成する詳細については、[複数フォレスト アーキテクチャへの Lync の展開 (Exchange ハイブリッドを使用してパートナーによりホストされる Lync)](http://go.microsoft.com/fwlink/p/?linkid=513216) を参照してください。
