---

copyright:
  years: 2019
lastupdated: "2019-05-31"

keywords: IBM Blockchain Platform console, administer a console, add users, remove users, modify a user's role, install patches, Kubernetes cluster expiration

subcollection: blockchain

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:note: .note}
{:important: .important}
{:tip: .tip}
{:pre: .pre}
{:gif: data-image-type='gif'}


# コンソールの管理
{: #ibp-console-manage-console}

さまざまな方法でコンソールの動作を管理できます。 このトピックでは、日常のコンソール使用時に役立つ、ブロックチェーン・ノード操作以外のアクションについて説明します。
{:shortdesc}

**対象者:** このトピックは、ブロックチェーン・ネットワークの作成、モニター、管理を担当するネットワーク・オペレーターを対象に設計されています。

## コンソールへのユーザーの追加とコンソールからのユーザーの削除
{: #ibp-console-manage-console-add-remove}

コンソールにアクセスするすべてのユーザーに、{{site.data.keyword.cloud}} の IAM (ID およびアクセス管理) のユーザー役割を定義したアクセス・ポリシーを割り当てる必要があります。 ユーザーがコンソール内でどのような操作を行えるかは、ポリシーによって決まります。 {{site.data.keyword.blockchainfull_notm}} Platform コンソールは、コンソール管理者である {{site.data.keyword.cloud_notm}} 所有者の E メール・アドレスを使用してプロビジョンされます。  デフォルトでは、この {{site.data.keyword.cloud_notm}} ユーザーに、{{site.data.keyword.blockchainfull_notm}} Platform サービスの**管理者**役割が IAM で付与されます。 そのため、コンソール管理者は、IAM の UI を使用して、コンソールに対するアクセス権限を他のユーザーに付与できます。 IAM について詳しくは、[IAM とは?](/docs/iam?topic=iam-iamoverview#iamoverview){: external}を参照してください。  

[IAM を使用してユーザーを招待する](/docs/iam?topic=iam-iamuserinv#iamuserinv){: external}ときは、以下の手順を実行して、そのユーザーの役割およびコンソールに対するアクセス権限を構成する必要があります。
 1. メニュー・バーで**「管理」** > **「アクセス (IAM)」**をクリックして、**「ユーザー」**を選択します。
 2. **「ユーザーの招待」**をクリックします。
 3. ユーザーの E メール・アドレスを入力します。
 4. **「サービス」**ドロップダウン・リストから **Blockchain Platform** を選択します。
 5. **「役割の選択」**までスクロールダウンします。
 6. **「サービスのアクセス役割の割り当て」**で、ユーザーの役割を選択します。**管理者**、**ライター**、**リーダー**の中から選択できます。
 7. **「ユーザーの招待」**をクリックします。

| 役割 | 権限 |
|--------|----------|
| 管理者 | 管理者には、ライター役割を超える許可が与えられます。 リーダーとライターが行えるすべての操作に加えて、以下の操作を行えます。 <ul><li>コンソールまたは API を使用して、新規コンポーネントをプロビジョンする。</li><li>コンソールまたは API を使用して、プロビジョン済みコンポーネントを削除する。</li><li>コンソールまたは API を使用して、コンソールのロギング・レベルを変更する。</li><li>API を使用して、コンソールを再始動する。</li></ul> |
| ライター | ライターには、リーダー役割を超える許可が与えられます。例えば、以下の操作を行えます。 <ul><li>コンソールまたは API を使用して、コンポーネントをインポートする。</li><li>コンソールまたは API を使用して、インポート済みコンポーネントを削除する。</li><li>ユーザーを CA に登録する。</li><li> コンソールまたは API を使用して、通知を追加または削除する。</li></ul>  |
| リーダー | リーダーは、読み取り専用の操作を行えます。例えば、以下の操作を行えます。 <ul><li>コンソール UI を表示する。</li><li>コンソール・ログを表示する。</li><li>コンポーネントをエクスポートする。</li><li>GET API を発行する。</li></ul> | |

 許可は累積型です。 **管理者**役割を選択した場合は、そのユーザーは**ライター**と**リーダー**の操作もすべて実行できるようになるので、それらの役割にまでチェック・マークを付ける必要はありません。   同様に、`ライター`役割のユーザーは、**リーダー**役割の操作をすべて実行できるようになります。 コンソールにアクセスするためには、**「サービスのアクセス役割」**で役割を選択するだけでよく、**「プラットフォームのアクセス役割」**で何かを選択する必要はありません。 招待されたユーザーの {{site.data.keyword.cloud_notm}} ダッシュボードにサービス・インスタンスが表示されることが重要な場合は、**「プラットフォームのアクセス役割の割り当て」**の下で対応する役割を確認してください。

![ユーザーの追加](../images/AddICPUser.gif){: gif}


コンソールに追加された新規ユーザーは、通常、他のユーザーがデプロイしたノード、チャネル、チェーンコードをすべて表示することはできません。 これらのコンポーネントを操作するためには、各ユーザーが自分のコンソール・ウォレットに関連 ID をインポートする必要があります。 詳しくは、[アイデンティティーのコンソール・ウォレットへの保管](/docs/services/blockchain/howto/ibp-console-identities.html#ibp-console-identities-wallet)を参照してください。
{:important}

ユーザーの役割を変更する必要がある場合は、以下のようにします。
 1. メニュー・バーで**「管理」** > **「アクセス (IAM)」**をクリックして、**「ユーザー」**を選択します。
 2. 変更するユーザーの横にある「アクション」メニューをクリックして、**「アクセス権限の割り当て」**を選択します。
 3. **「リソースへのアクセス権限の割り当て」**タイルを選択します。
 4. **「サービス」**ドロップダウン・リストから **Blockchain Platform 2.0** を選択します。
 5. **「役割の選択」**までスクロールダウンします。
 6. **「サービスのアクセス役割の割り当て」**で、ユーザーの役割を選択します。**管理者**、**ライター**、**リーダー**の中から選択できます。
 7. **「割り当て」**をクリックします。

コンソールに対するユーザーのアクセス権限を削除する必要がある場合は、[IAM のユーザーの削除に関するトピック](/docs/iam?topic=iam-remove#remove){: external}の手順に従ってください。

### IAM での個別ユーザーまたはユーザー・グループへのアクセス役割の割り当て
{: #ibp-console-manage-console-users-groups}

{{site.data.keyword.cloud_notm}} IAM ポリシーを設定する際に、個別ユーザーまたはユーザー・グループに役割を割り当てることができます。

<dl>
<dt>個別ユーザー</dt>
<dd>チームの他のユーザーとは異なる許可を必要とする特定のユーザーがいる場合があります。 各人がそれぞれのタスクを完了するために必要な許可を持つように、個人レベルで許可をカスタマイズできます。 ユーザーごとに複数の {{site.data.keyword.cloud_notm}} IAM 役割を割り当てることができます。</dd>
<dt>アクセス・グループ内の複数のユーザー</dt>
<dd>ユーザーのグループを作成して、そのグループに許可を割り当てることができます。 例えば、すべてのチーム・リーダーをグループ化して、そのグループに管理者権限を割り当てることができます。 次に、すべての開発者をグループ化して、そのグループに書き込み権限のみを割り当てることができます。 アクセス・グループごとに複数の {{site.data.keyword.cloud_notm}} IAM 役割を割り当てることができます。 グループに許可を割り当てると、そのグループに追加される、またはそのグループから削除されるすべてのユーザーは影響を受けます。 グループにユーザーを追加した場合、ユーザーにはアクセス権限が追加されます。 ユーザーを削除した場合、アクセス権限は取り消されます。</dd>
</dl>

IAM に追加するユーザーは、単に、コンソールにログインできるユーザーの E メール・アドレスです。 これらは、「組織」タブの**「使用可能な組織 (Available Organizations)」**やコンソール・ウォレットで保管されているアイデンティティーとは関係がありません。
{:note}

## 管理者の E メール・アドレスの更新

コンソールが複数の個人や組織によって使用される場合、ネットワークにアクセスするための機能 E メール・アドレスを作成することをお勧めします。 部署用の E メールを使用しておけば、最初の管理者が組織を離れたり、その管理者の E メール・アドレスが使用停止になったりしても、コンソールの利用を続けられます。 管理者の連絡先として使用できる E メール・アドレスは 1 つだけです。

コンソールのデプロイ時に構成されたコンソール管理者の E メール・アドレスを更新するには、コンソール管理者としてログインする必要があります。 **「ユーザー」**タブにナビゲートし、**「{{site.data.keyword.IBM_notm}} ID」**タイルで**「構成」**をクリックします。 開いたパネルで、コンソール管理者の新規 E メール・アドレスを指定します。

## ログの表示
{: #ibp-console-manage-logs}

{{site.data.keyword.blockchainfull_notm}} Platform コンソールを使用していると、ログを表示して問題をデバッグする必要がある場合があります。

### コンソール・ログの表示
{: #ibp-console-manage-console-logs}

コンソールの使用時やノードの操作時に発生した問題のデバッグが必要な場合、コンソール・ログに簡単にアクセスできます。 ロギング・レベルを設定して、コンソールが収集するログの量を増減することもできます。 コンソール・ログは、[ノード・ログ](/docs/services/blockchain/howto/ibp-console-manage.html#ibp-console-manage-console-node-logs) ({{site.data.keyword.cloud_notm}} Kubernetes Service によって収集されます) とは別に収集されます。

コンソール・ブラウザーの**「設定」**タブにナビゲートして、ロギング設定を変更します。 コンソール・ログは、2 つの別個のソースから収集されます。

  * **クライアント・ロギング:** これらのログは、ブラウザーからコンソールにコマンドが送信されたときに収集されます。
  * **サーバー・ロギング:** これらのログは、コンソールからノードにコマンドが送信されたとき、およびコンソールのデプロイメント時に収集されます。 これらのログには、Hyperledger Fabric のロギング出力が含まれます。

各ログ・タイプの下のドロップダウン・リストを使用して、収集されるログの量を設定します。 例えば、**「エラー」**および**「警告」**では最少量のログが収集され、**「デバッグ」**および**「すべて」**では最大量が収集されます。

コンソール・ログは、コンソール管理者としてログインしている場合にのみ表示できます。 **「設定」**タブからログを表示するには、ブラウザー URL の語 `settings` を `api/v1/logs` に置き換えます。 例えば、コンソール URL が `localhost:3001/settings` の場合、`localhost:3001/api/v1/logs` にナビゲートすることによってログを表示できます。 クライアント・ログとサーバー・ログは別個のファイルに収集されます。 最新のログがページの先頭に表示されます。

### ノード・ログの表示
{: #ibp-console-manage-console-node-logs}

ピア、順序付けプログラム、および認証局のログは、{{site.data.keyword.IBM_notm}} Kubernetes サービスによって収集されます。 以下のステップに従って、{{site.data.keyword.blockchainfull_notm}} Platform ネットワークをデプロイしたクラスターのノードのログを表示します。

ノードのデプロイ時に使用した名前空間でフィルタリングすると、ノード・ログを見つけやすくなります。名前空間を調べるには、コンソールで CA ノードを開き、**「設定」**アイコンをクリックします。**「認証局エンドポイント URL」**の値を表示します。例えば、`https://n2734d0-paorg10524.ibpv2-cluster.us-south.containers.appdomain.cloud:7054` などが表示されます。

この URL の最初の部分が名前空間です。文字 `n` で始まり、6 文字のランダムな英数字から成る文字列が続きます。つまり、上の例では、名前空間の値は `n2734d0` です。

1. [{{site.data.keyword.cloud_notm}} ダッシュボード](https://cloud.ibm.com/resources){: external}を開き、{{site.data.keyword.IBM_notm}} Kubernetes サービス・クラスターの概要画面にナビゲートします。
2. クラスターの概要画面上の**「Kubernetes ダッシュボード」**をクリックします。
3. Kubernetes ダッシュボードで、左側のナビゲーションの**「名前空間」**ドロップダウン・リストを使用して、先ほど確認した {{site.data.keyword.blockchainfull_notm}} Platform のサービス・インスタンスの名前空間に変更します。
4. 左側のナビゲーションで、**「ポッド」**をクリックしてデプロイ済みのノード・ポッドのリストを表示します。
5. ポッドをクリックします。 次に、上部メニューで**「ログ」**をクリックして、ノードのログを開きます。 ログ上部の**「ログの取得元 (Logs from)」**の後にあるドロップダウン・メニューを使用して、ポッド内の異なるコンテナーのログを表示できます。 例えば、ピアと状態データベース (CouchDB など) は、異なるコンテナーで実行され、異なるログが生成されます。

デフォルトでは、ノードのログはクラスター内でローカルに収集されます。 {{site.data.keyword.cloud_notm}} のサービスやサード・パーティーのサービスを使用してネットワークのログを収集、保管、分析することもできます。詳しくは、[{{site.data.keyword.IBM_notm}} Kubernetes Service のロギングとモニタリング](https://cloud.ibm.com/docs/containers?topic=containers-health#health){: external}を参照してください。 ログをリアルタイムで簡単に解析できる[{{site.data.keyword.cloud_notm}} LogDNA](https://cloud.ibm.com/docs/services/Log-Analysis-with-LogDNA?topic=LogDNA-kube#kube){: external} サービスを利用することをお勧めします。

### スマート・コントラクトのコンテナー・ログの表示
{: #ibp-console-manage-console-container-logs}

スマート・コントラクトに関する問題が発生した場合は、以下のようにスマート・コントラクト (チェーンコード) のコンテナー・ログを表示して問題をデバッグできます。

- Kubernetes ダッシュボードを開き、[名前空間](#ibp-console-manage-console-node-logs)でフィルタリングし、スマート・コントラクトが実行されているピアのポッドをクリックします。
- ダッシュボードから`「ログ」`リンクをクリックします。デフォルトでは、ピア・コンテナーを指しています。
- ドロップダウン・リストから `fluentd` コンテナーを選択して、このコンテナーに切り替えます。  

すべてのスマート・コントラクト・ログがこのウィンドウに表示されます。パネルのダウンロード・アイコンを使用してダウンロードできます。

## ノードのパッチのインストール
{: #ibp-console-manage-patch}

ピア・ノード、CA ノード、および順序付けプログラム・ノードの基盤となる {{site.data.keyword.IBM_notm}} Hyperledger Fabric Docker イメージは、セキュリティー更新や新しい Fabric ポイント・リリースへの更新などのために、時間の経過とともに更新する必要が生じることがあります。 ノード・タイルに**「使用可能なパッチ (Patch available)」**というテキストが示された場合、これはそのようなパッチが使用可能であり、ユーザーの準備ができたらいつでもノードにインストール可能であることを示しています。 これらのパッチはオプションですが、推奨されます。  コンソールにインポートされたノードにパッチを適用することはできません。

パッチは、一度に 1 つのノードに適用されます。 パッチが適用されている間、そのノードでは要求やトランザクションを処理できません。 そのため、サービスの中断を防ぐために、可能な場合は常に、同じタイプの別のノードが要求を処理できることを確認する必要があります。 ノードへのパッチのインストールが完了するまでには約 1 分かかり、更新が完了すると、ノードで要求を処理できるようになります。
{:note}

ノードにパッチを適用するには、ノード・タイルを開き、**「パッチのインストール (Install patch)」**ボタンをクリックします。

## Kubernetes クラスターの有効期限
{: #ibp-console-manage-console-cluster-expiration}

無料の {{site.data.keyword.cloud_notm}} Kubernetes Service クラスターを使用する場合は、30 日後に有効期限が切れます。 そうなると、コンソールにアクセスできなくなります。 関連するノードと証明書もすべて削除されます。 一度に使用できる無料クラスターは 1 つだけです。 したがって、別のブロックチェーン・サービス・インスタンスを作成するためには、期限切れのクラスターとそれに関連するサービス・インスタンスが {{site.data.keyword.cloud_notm}} から削除されていることを確認しておく必要があります。 それらが既に削除されているかどうかを確認する場合や、それらのリソースを手動で削除する場合は、以下の手順を実行します。

1. {{site.data.keyword.cloud_notm}} ダッシュボードで、ハンバーガー・メニューをクリックし、**「リソース・リスト」**を開きます。
2. **「サービス」**ツイスティーまでスクロールし、それを展開してサービス・インスタンスを表示します。
3. インスタンスがリストされたら、サービス・インスタンスのアクション・メニューをクリックし、次に**「削除」**をクリックしてそのサービス・インスタンスを削除します。
4. **「Kubernetes クラスター」**ツイスティーまでスクロールし、それを展開して無料クラスターを表示します。
5. 無料クラスターがリストされたら、クラスターのアクション・メニューをクリックし、次に**「削除」**をクリックして無料クラスターを削除します。

これらのアクションが完了したら、[最初の手順](/docs/services/blockchain/howto/ibp-v2-deploy-iks.html#ibp-v2-deploy-iks)に従って、{{site.data.keyword.cloud_notm}} カタログ・ページから新しい Kubernetes クラスターとブロックチェーン・サービス・インスタンスを作成できます。
