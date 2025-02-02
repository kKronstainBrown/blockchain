---

copyright:
  years: 2017, 2019
lastupdated: "2019-05-31"

keywords: IBM Blockchain, IBM Blockchain Platform, terms, Fabric, Raft, CouchDB, consortium

subcollection: blockchain

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# 用語集
{: #glossary}

このトピックでは、この資料に記載されている {{site.data.keyword.blockchainfull}} プラットフォーム固有の用語を定義します。 用語の詳細な意味、および Hyperledger Fabric の概念に関連する用語の用語集は、[Hyperledger Fabric の用語集](https://hyperledger-fabric.readthedocs.io/en/release-1.4/glossary.html){: external}を参照してください。
{:shortdesc}

## 資産
{: #glossary-asset}
ブロックチェーン・ネットワーク上で取引されるアイテムとして表される有形または無形の商品、サービス、またはプロパティー。

## ブロック
{: #glossary-block}
順序付けられたトランザクション集合。チャネル上の先行ブロックに暗号的にリンクされます。

## CA
{: #glossary-CA}
「認証局 (Certificate Authority)」の省略形。これは、すべての参加メンバーに証明書を発行するコンポーネントです。 これらの証明書は、メンバーの ID を表します。 ネットワーク内のすべてのエンティティー (ピア、順序付けサービス、クライアントなど) には、通信や認証やトランザクションで使用する ID が必要です。 これらの ID は、ブロックチェーン・ネットワークの直接的な参加者すべてに必要です。

## チェーン
{: #glossary-chain}
台帳のチェーンは、トランザクションのハッシュ・リンク・ブロックとして構造化されたトランザクション・ログです。 ピアは順序付けサービスからトランザクションのブロックを受け取り、エンドースメント・ポリシーおよび並行性違反に基づいてブロックに有効または無効のマークを付け、そのブロックをピアのファイル・システム上のハッシュ・チェーンの末尾に追加します。

## チェーンコード
{: #glossary-chaincode}
チェーンコードは**スマート・コントラクト**とも呼ばれ、台帳を照会または更新するための一連の関数を含むソフトウェアです。

## チャネル
{: #glossary-channel}
プライベートに取引するネットワーク・メンバーのサブセットで構成されます。 チャネルは、チャネルのメンバーが特定の規則と、チャネル・メンバーのみがアクセスできる個別の台帳を作成できるようにすることにより、データの分離と機密性を提供します。 ピアは、組織のトランザクション・エンドポイントとして機能するノードであり、チャネルに結合されます。

## クライアント
{: #glossary-client}
クライアントは、ユーザーに代わって行動するエンティティーを表します。 ブロックチェーンと通信するには、ピアに接続する必要があります。 クライアントは、任意のピアに接続できます。 クライアントはトランザクションを作成して呼び出します。 クライアントは、実際のトランザクション呼び出しをエンドーサーに送信し、トランザクション・プロポーザルを順序付けサービスにブロードキャストします。

## 接続プロファイル
{: #glossary-connection-profile}
接続プロファイルは、 **「接続プロファイル」**ボタンをクリックすると、ネットワーク・モニターの「概要」画面に表示されます。 この情報は JSON フォーマットで使用可能で、ネットワーク・リソース (ピア、順序付けプログラム、CA) の API エンドポイント情報と 登録 ID/秘密鍵が含まれています。 アプリケーションはこれらの API エンドポイントを介してネットワーク・リソースと対話します。

## コンセンサス
{: #glossary-consensus}
台帳トランザクションをネットワーク全体で同期させるためのコラボレーション・プロセス。 コンセンサスにより、適切な参加者がトランザクションを承認するときにのみ台帳が更新され、また、同じ順序の同じトランザクションにより、台帳が更新されます。 コンセンサスを達成するためのアルゴリズム的な方法はいろいろあります。

## コンソール
{: #glossary-console}
{{site.data.keyword.blockchainfull_notm}} Platform 内のユーザー・インターフェースの名前。 ユーザーはコンソールを使用して、デプロイメントを表示、作成、および管理できます。 公開鍵および秘密鍵は、コンソールが実行されているブラウザーにローカルでのみ格納されるため、ユーザーは自分の鍵を完全に制御できます。

## 共同事業体
{: #glossary-consortium}
順序付けプログラム・システム・チャネルにリストされている非順序付けサービス組織のグループ。 これらは、チャネルを作成できる唯一の組織です。 チャネルの作成時には、チャネルに追加されるすべての組織が共同事業体の一部である必要があります。 ただし、共同事業体で定義されていない組織を既存のチャネルに追加することはできます。 1 つのブロックチェーン・ネットワークに複数の共同事業体を含めることができますが、ほとんどのブロックチェーン・ネットワークでは共同事業体は 1 つのみです。

## CouchDB
{: #glossary-couchdb}
{{site.data.keyword.blockchainfull_notm}} Platform およびスターター・プラン・ネットワーク内の状態データベースに対して使用される、データのリッチ・クエリーを可能にする文書ストア。 CouchDB は LevelDB と並んで、エンタープライズ・プラン・ネットワークのオプションでもあります。

## 現在の状態
{: #glossary-current-state}
台帳の現在の状態は、チェーン・トランザクション・ログに含まれるすべてのキーの最新の値を表します。 現在の状態は、チャネルに認識されているすべての最新のキー値を表すため、**ワールド・ステート**と呼ばれることもあります。 スマート・コントラクトは、現在の状態のデータに対してトランザクション・プロポーザルを実行します。 現在の状態は、キーの値が変更されるか、新しいキーが追加されるたびに変化します。最新のキーと値のペアを変更するには、そのペアが既知でなければならないため、現在の状態はトランザクション・フローにとって重要です。 ピアは、ブロック内の有効なトランザクションごとに、最新の値を台帳の現在の状態にコミットします。 現在の状態は、ピアに関連付けられている状態データベースに格納されます。

## 動的メンバーシップ
{: #glossary-dynamic-memership}
**「登録」**特権を持つユーザーは、メンバーを動的にネットワークに追加することができます。 また、メンバーには役割や属性も割り当てられます。これは、ネットワークでのアクセスと権限を制御します。 ただし、役割も属性も動的に割り当てることはできません。 Hyperledger Fabric は、ネットワーク全体の運用を損なうことなく、メンバー、ピア、および順序付けサービス・ノードの追加や削除をサポートします。 動的メンバーシップは、さまざまな理由でビジネス関係の調整や、エンティティーを追加または削除する必要がある場合に重要です。

## エンドースメント
{: #glossary-endorsement}
チェーンコード・トランザクションを検証するプロセス。 エンドースメント・ルールは、エンドースメント・ポリシーを指定することによって実装されます。

## エンドースメント・ポリシー
{: #glossary-endorsement-policy}
特定のチェーンコード・アプリケーションに接続されたトランザクションを実行する必要があるチャネル上のピア・ノード、および必要な応答の組み合わせ (エンドースメント) を定義します。 ポリシーでは、承認ピアの最小数、承認ピアの最小パーセンテージ、または特定のチェーンコード・アプリケーションに割り当てられているすべての承認ピアによって、トランザクションを承認しなければならない場合があります。 ポリシーは、意図的であるかどうかにかかわらず、アプリケーションおよび不正行為に対して必要な回復力レベルに基づいて、承認ピアにより調達できます。 送信されるトランザクションは、関わっているピアにより有効とマーク付けされる前に、このエンドースメント・ポリシーを満たす必要があります。 トランザクションをインストールおよびインスタンス化するための別のエンドースメント・ポリシーも必要です。

## ジェネシス・ブロック
{: #glossary-genesis-block}
ブロックチェーン・ネットワークまたはチャネルを初期化し、チェーンの最初のブロックとしても機能する構成ブロック。

## Gossip
{: #glossary-gossip}
Hyperledger Fabric では、順序付けサービスに依存せずに、ピアどうしで重要なネットワーク情報を収集できます。 [ゴシップ・データ配布プロトコル](https://hyperledger-fabric.readthedocs.io/en/release-1.4/gossip.html){: external}により、安全、確実、スケーラブルなピア間のメッセージ交換が可能になっています。 例えば、遅延、ネットワーク障害、その他の理由でいくつかのブロックがピアに存在しない場合、ピアは、ゴシップ・メッセージングを使用して、欠落ブロックを所有している他のピアと通信し、最新の台帳状態に同期できます。

## HSM
{: #glossary-hsm}
ハードウェア・セキュリティー・モジュール。 オンデマンド暗号化、鍵管理、および鍵格納をマネージド・サービスとして提供します。 HSM は、リソース集中型の暗号化処理タスクを処理し、アプリケーションの待ち時間を削減する物理アプライアンスです。 詳しくは、[Hardware Security Module](https://www.ibm.com/cloud/hardware-security-module){: external} を参照してください。

## Hyperledger Fabric
{: #glossary-hyperledger-fabric}
[Hyperledger Fabric](https://hyperledger-fabric.readthedocs.io/en/release-1.4/){: external} は Linux Foundation がホストするビジネス・ブロックチェーン・フレームワークで、ブロックチェーン・アプリケーションまたはソリューションを、モジュラー・アーキテクチャーで開発するための基盤として機能します。 コンセンサス・サービスやメンバーシップ・サービスなどの Hyperledger Fabric コンポーネントは、プラグ・アンド・プレイです。

## インストール
{: #glossary-install}
チェーンコードをピアのファイル・システムに配置するプロセス。 このチェーンコードを実行するすべてのピアにチェーンコードをインストールする必要があります。

## インスタンス化
{: #glossary-instantiate}
特定のチャネルでチェーンコード・コンテナーを開始および初期化するプロセス。 チェーンコードがピアにインストールされ、すべてのピアがチャネルに参加したら、チェーンコードをチャネル上でインスタンス化する必要があります。 インスタンス化は、チェーンコードの初期状態を構成するキーと値のペアの設定を含む、チェーンコードの必要な初期化を実行します。 インスタンス化の後、チェーンコードがインストールされているピアはチェーンコード呼び出しを受け入れることができます。

## Kafka
{: #glossary-kafka}
ブロックチェーン・ネットワーク内で順序付けサービス・ノードのクラスターとなる Hyperledger Fabric のコンセンサス・プラグイン実装。 Kafka 実装および Raft 実装は、実動ネットワークのための実装です。 ただし、Raft の順序付けサービス・クラスターのみがネイティブにサポートされ、{{site.data.keyword.blockchainfull_notm}} Platform を使用して作成できます。

## 台帳
{: #glossary-ledger}
トランザクションの不変のシーケンス・レコードと、現在の状態を維持するための状態データベースを保管する、文字どおり「ブロックのチェーン」から構成されています。 チャネルごとに 1 つの台帳があり、それに対する更新は、特定のチャネルのポリシーに従ってコンセンサス・プロセスによって管理されます。

## LevelDB
{: #glossary-leveldb}
CouchDB とともに、エンタープライズ・プラン・ネットワークの状態データベースのオプションであるキー値ストア。 LevelDB は現在の状態をキー値ペアとして格納し、索引やリッチ・クエリーの使用はサポートしていません。

## メンバー
{: #glossary-member}
「組織」とも呼ばれ、ブロックチェーン・ネットワーク内のメンバーは、グループのメンバーと同じように、ネットワークの構造を形成します。 メンバーは多国籍企業のような大きな場合も、個人のように小さい場合もあります。 メンバーは、ネットワークをサービス・プロバイダー (証明書の発行、トランザクションの検証/順序付けなど) またはコンシューマーとして使用する許可を付与する証明書を使用して、ネットワークに登録されます。 前者は、トランザクション検証、トランザクションの順序付け、および証明書管理サービスを含む基本的なブロックチェーン・サービスを提供します。 コンシューマー・メンバーは、ネットワークを使用して、分散台帳に対してトランザクションを呼び出します。 メンバーは複数のピアを持つことができます。

## MSP
{: #glossary-msp}
**Membership Service Provider** (メンバーシップ・サービス・プロバイダー) の省略形。これは、組織に関連付けられているエンティティーの証明書を発行する CA のルート証明書、および組織の管理者の署名付き証明書を含む、組織の定義を提供します。 MSP はピア・ノードまたは順序付けノードのローカル・レベルにも存在し、ノードの管理者ユーザーを検証する認証メカニズムです。 {{site.data.keyword.blockchainfull_notm}} Platform では、あるコンソールから別のコンソールに MSP をエクスポートできます。このためユーザーは、あるコンソールで組織を作成し、その組織を別のコンソールにインポートして、操作 (例えば、チャネルを作成するために) することができます。 MSP を順序付けサービスにインポートして、チャネルを作成し、チャネルに参加することを許可されている組織のリストである「コンソーシアム」を形成することもできます。

## ネットワーク
{: #glossary-network}
{{site.data.keyword.cloud_notm}} 上の {{site.data.keyword.blockchainfull_notm}} プラットフォーム・サービスのインスタンス。

## ネットワーク資格情報
{: #glossary-network-credentials}
ネットワーク・モニターの「API」画面で確認できます。 資格情報には、Swagger UI に「key」 (ユーザー名) と「secret」 (パスワード) が含まれます。 REST API を試す前に、これらのネットワーク資格情報を使用して認証する必要があります。

## ネットワーク・モニター
{: #glossary-network-monitor}
{{site.data.keyword.blockchainfull_notm}} Platform のスターター・ネットワークおよびエンタープライズ・ネットワークの GUI ダッシュボード。ユーザーはこれを使用して、ブロックチェーン・ネットワークを表示および管理できます。

## ノード
{: #glossary-node}
ブロックチェーンの通信エンティティー。 ノードには、CA、ピア、順序付けプログラムの 3 つのタイプがあります。

## 順序付けプログラム
{: #glossary-orderer}
ネットワーク・メンバーからトランザクションを収集し、トランザクションを順序付けてブロックにバンドルするノード。 次に、これらのブロックはピアに配布されます。ピアはブロックを検証し、それらを各チャネルの台帳に追加します。 順序付けプログラムには、各メンバーに紐付けられた暗号 ID 情報が含まれており、ネットワークにアクセスするためのクライアントおよびピアの ID を認証します。 順序付けノードまたはノードの集合が提供する全体的な機能は、**順序付けサービス**と呼ばれます。

## 組織
{: #glossary-organization}
「[メンバー](/docs/services/blockchain/glossary.html#glossary-member)」を参照。

## 参加者
{: #glossary-participant}
ブロックチェーン・ネットワークと対話する任意の組織、個人、アプリケーション、またはデバイス。 「参加者」というくくりの中に、メンバーとユーザーという 2 つのグループがあります。

## ピア
{: #glossary-peer}
トランザクションの実行と検証、および台帳の保守を行うサービスを提供するブロックチェーン・ネットワーク・リソース。 ピアはチェーンコードを実行します。また、トランザクションの履歴情報やネットワーク・チャネルに存在する資産の現在の状態に関する情報の保有者です。 これらは組織によって所有および管理され、チャネルに結合されます。

## Raft
{: #glossary-raft}
Raft は、`etcd` での [Raft プロトコル](https://raft.github.io/raft.pdf){: external}の実装に基づく、クラッシュ・フォールト・トレラント (CFT) 順序付けサービスです。 Raft は「リーダーとフォロワー」モデルに従います。このモデルでは、リーダー・ノードが (チャネルごとに) 選ばれ、その決定がフォロワーによって複製されます。 Raft の順序付けサービスは、Kafka ベースの順序付けサービスよりも設定と管理が簡単です。また、{{site.data.keyword.blockchainfull_notm}} Platform を使用して、これらのノードのクラスターを作成できます。

## サービス資格情報
{: #glossary-service-credentials}
サービス資格情報は JSON 形式であり、ネットワーク・リソース (CA、順序付けプログラム、およびピア) の API エンドポイント情報と登録 ID/秘密が含まれています。 アプリケーションはこれらの API エンドポイントを介してネットワーク・リソースと対話します。

## SDK
{: #glossary-sdk}
Hyperledger Fabric は 2 つの Software Development Kit (SDK) をサポートします。 ノード SDK および Java SDK です。  ノード SDK は NPM を介して、Java SDK は Maven を介してインストールできます。  SDK には独自の git リポジトリー、つまり [ファブリック・ノード SDK](https://github.com/hyperledger/fabric-sdk-node){: external} および[ファブリック Java SDK](https://github.com/hyperledger/fabric-sdk-java){: external} があり、使用可能な API の資料が付いています。 Hyperledger Fabric のクライアント SDK は、クライアント・アプリケーションとブロックチェーン・ネットワーク間の対話を可能にします。

## 署名付き証明書
{: #glossary-sign-cert}
組織または管理者のいずれかを問わず、任意のエンティティーがその提案または提案の応答に添付する証明書。 これらの署名付き証明書はエンティティーに固有であり、そのエンティティーのファイルに対する署名付き証明書と一致することを確認するために、順序付けサービスによってチェックされます。

## スマート・コントラクト
{: #glossary-smart-contracts}
[チェーンコード](/docs/services/blockchain/glossary.html#glossary-chaincode)を参照してください。

## Solo
{: #glossary-solo}
ブロックチェーン・ネットワーク内で単一の順序付けサービス・ノードとなる Hyperledger Fabric のコンセンサス・プラグイン実装。 スターター・プラン・ネットワークは Solo 実装を使用します。 Solo 実装は実動ネットワーク用ではありません。 Solo の代わりは、Raft クラスターと Kafka クラスターです。

## 状態データベース
{: #glossary-state-database}
現在の状態のデータは、チェーンコードからの効率的な読み取りとクエリーのためにピアのデータベースに格納されます。 スターター・プラン・ネットワークは状態データベースとして CouchDB を使用します。 エンタープライズ・プラン・ネットワークは LevelDB または CouchDB のいずれかを使用できます。

## トランザクション
{: #glossary-transaction}
ブロックチェーン・ネットワーク上の参加者が資産と対話するために使用するメカニズム。 トランザクションは新規チェーンコードを作成するか、既存のチェーンコードで操作を呼び出します。

## ユーザー
{: #glossary-user}
ユーザーは、ブロックチェーン・ネットワークの既存のメンバーとの信頼関係に基づいて台帳に間接的にアクセスできる参加者です。

## ワールド・ステート
{: #glossary-world-state}
[現在の状態](/docs/services/blockchain/glossary.html#glossary-current-state)を参照してください。
