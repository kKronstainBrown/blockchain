---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-31"

keywords: IBM Blockchain Platform, remote peer, operate peers, AWS peer, AWS peers, necessary certificates, command line

subcollection: blockchain

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Exploitation des homologues dans AWS
{: #remote-peer-aws-operate}

Après que vous avez configuré des homologues {{site.data.keyword.blockchainfull}} Platform dans AWS, vous devez effectuer plusieurs étapes supplémentaires pour que votre homologue puisse émettre des transactions afin d'interroger et d'appeler le registre du réseau de blockchain. Ces étapes incluent l'ajout de votre organisation à un canal, l'association de votre homologue au canal, l'installation de code blockchain sur votre homologue, l'instanciation de code blockchain sur le canal, ainsi que la connexion d'applications à votre homologue. Vous pouvez utiliser les [logiciels SDK Fabric](/docs/services/blockchain/howto/remote_peer_operate_aws.html#remote-peer-aws-operate-with-sdk) ou la [ligne de commande](/docs/services/blockchain/howto/remote_peer_operate_aws.html#remote-peer-aws-operate-cli-operate) pour effectuer ces étapes opérationnelles. Les logiciels SDK Fabric sont recommandés. Cependant, les instructions supposent que vous avez une bonne connaissance du fonctionnement du logiciel SDK.

**Remarque **: L'homologue {{site.data.keyword.blockchainfull_notm}} Platform dans AWS n'a pas accès à toutes les fonctionnalités ou à la prise en charge des homologues qui sont hébergés sur {{site.data.keyword.blockchainfull_notm}} Platform. Par conséquent, vous ne pouvez pas utiliser le moniteur réseau pour exploiter un homologue. Avant de commencer à lancer des homologues, assurez-vous d'avoir passé en revue les [considérations](/docs/services/blockchain/howto/remote_peer.html#remote-peer-aws-about-limitations).

## Utilisation de SDK Fabric pour l'exploitation de votre homologue
{: #remote-peer-aws-operate-with-sdk}

Les logiciels SDK Hyperledger Fabric fournissent un puissant jeu d'API qui permettent aux applications d'interagir et d'exploiter les réseaux de blockchain. Vous pouvez obtenir la liste la plus récente des langages pris en charge et la liste complète des API disponibles au sein des logiciels SDK Hyperledger Fabric dans la [documentation Hyperledger Fabric SDK Community](https://hyperledger-fabric.readthedocs.io/en/release-1.2/getting_started.html#hyperledger-fabric-sdks){: external}. Vous pouvez utiliser les logiciels SDK Fabric pour associer votre homologue à un canal sur {{site.data.keyword.blockchainfull_notm}} Platform, installer un code blockchain sur votre homologue, et instancier le code blockchain sur un canal.

Les instructions suivantes utilisent le [Logiciel SDK Node Fabric](https://fabric-sdk-node.github.io/){: external} pour exploiter l'homologue et supposent une connaissance préalable du logiciel SDK. Vous pouvez utiliser le [tutoriel de développement d'applications](/docs/services/blockchain/v10_application.html#dev-app) pour en savoir plus sur l'utilisation du logiciel SDK Node avant de commencer, et comme guide pour le développement d'applications avec votre homologue lorsque vous êtes prêt à appeler et à interroger le code blockchain.

Le démarrage rapide de l'homologue {{site.data.keyword.blockchainfull_notm}} Platform on AWS crée deux homologues pour la haute disponibilité. Par conséquent, vous devez suivre ces opérations une fois pour chaque homologue. Lorsque vous êtes prêt à appeler et à interroger le code blockchain depuis votre application, utilisez le logiciel SDK pour la connexion aux deux homologues pour vous assurer que les [applications sont hautement disponibles](/docs/services/blockchain/best_practices.html#best-practices-app-ha-app).

### Installation du logiciel SDK Node
{: #remote-peer-aws-operate-install-sdk}

Vous pouvez utiliser NPM pour installer le [logiciel SDK Node](https://fabric-sdk-node.github.io/){: external} :
```
npm install fabric-client@1.2
```
{:codeblock}

Il est recommandé d'utiliser la version 1.2 du logiciel SDK Node.

### Préparation du logiciel SDK pour l'utilisation de l'homologue
{: #remote-peer-aws-operate-sdk}

Avant d'utiliser le logiciel SDK pour exploiter l'homologue, vous devez générer les certificats nécessaires (inscription) qui permettront à votre application de communiquer avec votre réseau sur {{site.data.keyword.blockchainfull_notm}} Platform et votre homologue. Suivez les étapes d'[inscription auprès du logiciel SDK](/docs/services/blockchain/v10_application.html#dev-app-enroll-sdk) avec votre identité **admin**. Le tutoriel [Développement d'applications](/docs/services/blockchain/v10_application.html#dev-app) inscrit également en tant qu'**admin**, il n'est donc pas nécessaire de modifier l'exemple de code.

### Envoi par téléchargement d'un certificat signcert vers {{site.data.keyword.blockchainfull_notm}} Platform
{: #remote-peer-aws-operate-upload-SDK}

Vous devez envoyer par téléchargement le certificat signataire de votre logiciel SDK au réseau sur {{site.data.keyword.blockchainfull_notm}} Platform afin que les autres membres puissent reconnaître votre signature numérique.

- Le certificat signataire se trouve dans le répertoire où votre logiciel SDK a généré votre matériel cryptographique, dans le fichier nommé admin. Copiez le certificat figurant entre guillemets après la zone `certificate`, commençant par `-----BEGIN CERTIFICATE-----` et se terminant par `-----END CERTIFICATE-----`. Vous pouvez utiliser l'interface CLI pour convertir le certificat au format PEM à l'aide de la commande `echo -e "<CERT>" > admin.pem`. Vous pouvez ensuite coller le contenu du certificat dans votre réseau de blockchain à l'aide du moniteur de réseau. Connectez-vous au réseau sur {{site.data.keyword.blockchainfull_notm}} Platform. A l'écran "Membres" du Moniteur réseau, cliquez sur **Certificats** > **Ajouter un certificat**. Indiquez un nom pour votre certificat et collez le contenu dans le champ **Certificat**. Cliquez sur **Redémarrer** lorsque vous êtes invité à indiquer si vous voulez redémarrer vos homologues. Cette opération doit être effectuée avant que votre organisation ne rejoigne le canal.

### Envoi par téléchargement d'un certificat signataire à l'homologue
{: #remote-peer-aws-operate-upload-signcert}

Vous devez également envoyer par téléchargement le certificat signataire du logiciel SDK à l'homologue distant et le redémarrer. Vous devez installer le même certificat signataire que celui que vous [avez envoyé par téléchargement à {{site.data.keyword.blockchainfull_notm}} Platform](/docs/services/blockchain/howto/remote_peer_operate_aws.html#remote-peer-aws-operate-upload-SDK) au sein du conteneur homologue distant.

Lancez SSH dans votre instance VPC en sélectionnant l'instance dans la console AWS (cliquez sur **Services > EC2 > Instances**), puis cliquez sur le bouton Connecter. Suivez les instructions d'AWS pour émettre la commande ssh.

Exécutez les commandes suivantes dans votre conteneur homologue pour envoyer par téléchargement votre certificat.  
```
cd /etc/hyperledger/<PEER_ENROLL_ID>/msp/admincerts/
echo -e "<CERT.PEM>" > cert2.pem
```
{:codeblock}

- Remplacez `<PEER_ENROLL_ID>` par l'ID d'inscription qui est spécifié dans le modèle de démarrage rapide et est associé à cette instance homologue distant.  
- Remplacez `<CERT.PEM>` par votre certificat signcert, qui commence par `-----BEGIN CERTIFICATE-----` et se termine par `-----END CERTIFICATE-----`.    

  **Remarque :** Si le fichier `cert.pem` existe, ne le remplacez pas, mais créez un nouveau fichier, par exemple, `cert2.pem`.

Etant donné que vous ajoutez un nouveau certificat, vous devez redémarrer le conteneur pour que l'homologue prélève le certificat. Suivez ces [instructions](/docs/services/blockchain/howto/remote_peer_operate_aws.html#remote-peer-aws-operate-restart) pour redémarrer votre homologue.

### Transmission du certificat TLS de votre homologue au logiciel SDK
{: #remote-peer-aws-operate-download-tlscert}

Vous devez copier le contenu du fichier `cacert.pem` de TLS du conteneur homologue à votre application afin d'authentifier la communication depuis votre logiciel SDK. Exécutez la commande suivante dans le conteneur homologue. Remplacez `<PEER_ENROLL_ID>` par le nom de pile de l'homologue distant que vous avez indiqué dans le modèle de démarrage rapide. (Rappel : deux instances VPC sont créées.)
```
cat /etc/hyperledger/<PEER_ENROLL_ID>/tls/ca.crt
```
{:codeblock}

Copiez l'intégralité du texte du fichier `ca.crt` dans votre presse-papiers, qui commence par le premier `-----BEGIN CERTIFICATE-----` et se termine par le tout dernier `-----END CERTIFICATE-----`. Sauvegardez ce certificat sur votre système de fichiers local au format PEM. Vous pouvez ensuite importer le certificat TLS dans votre application à l'aide d'une simple commande de lecture de fichier.
```
var caCert = fs.readFileSync(path.join(__dirname, './ca.pem'));
```
{:codeblock}

### Indication des informations de noeud final de l'homologue au logiciel SDK
{: #remote-peer-aws-operate-SDK-endpoints}

Pour extraire les informations de noeud final de votre homologue, localisez votre instance homologue sur la console AWS. Notez la valeur de `AWS EC2 dashboard Public DNS (IPv4)` pour l'instance EC2 et indiquez-la au logiciel SDK en déclarant une nouvelle variable d'homologue ou en mettant à jour votre profil de connexion. Concaténez l'adresse DNS publique avec le port `7051`. L'exemple suivant définit l'homologue sur votre réseau Fabric et le transmet au certificat TLS que vous avez importé.

```
var peer = fabric_client.newPeer('grpcs://<AWS_EC2_dashboard_Public_DNS>:7051', { pem:  Buffer.from(caCert).toString()});
```
{:codeblock}

**Remarque :** Etant donné que l'homologue est distant, les autres organisations sur le réseau {{site.data.keyword.blockchainfull_notm}} Platform ne pourront pas trouver les informations de noeud final de votre homologue dans leur profil de connexion. Si d'autres organisations doivent envoyer à votre homologue une transaction à approuver, vous devez fournir l'adresse IP publique et les certificats TLS dans une opération hors bande.

### Utilisation du logiciel SDK pour rejoindre un canal
{: #remote-peer-aws-operate-join-channel-sdk}

En tant que membre du réseau blockchain, votre organisation doit être ajoutée à un canal du réseau pour que vous puissiez rejoindre votre homologue dans le canal.

  - Vous pouvez démarrer un nouveau canal pour l'homologue. En tant qu'initiateur de canal, vous pouvez inclure automatiquement votre organisation durant la [création de canal](/docs/services/blockchain/howto/create_channel.html#ibp-create-channel-creating-a-channel).

  - Un autre membre du réseau blockchain peut également ajouter votre organisation à un canal existant en utilisant une [mise à jour de canal](/docs/services/blockchain/howto/create_channel.html#ibp-create-channel-updating-a-channel).

    Une fois que votre organisation est ajoutée à un canal, vous devez ajouter le certificat signataire de votre homologue au canal de sorte que les autres membres puissent vérifier votre signature numérique au cours des transactions. L'homologue envoie par téléchargement son certificat signataire lors de l'installation, de sorte que vous devez uniquement synchroniser le certificat pour le canal. Dans l'écran "Canaux" de votre Moniteur réseau, localisez le canal rejoint par votre organisation et sélectionnez **Synchroniser le certificat** dans la liste déroulante sous l'en-tête **Action**. Cette action synchronise les certificats entre tous les homologues sur le canal. Vous devrez peut-être attendre quelques minutes le temps que le canal se synchronise avant l'exécution des commandes join channel.

Lorsque votre organisation fait partie du canal, suivez les instructions permettant de [rejoindre un canal](/docs/services/blockchain/v10_application.html#dev-app-join-channel-sdk). Vous devez indiquer l'URL du service de commande et le nom du canal.

### Utilisation du logiciel SDK pour installer le code blockchain sur l'homologue
{: #remote-peer-aws-operate-install-cc-sdk}

Suivez les instructions relatives à l'utilisation du logiciel SDK pour [installer un code blockchain](/docs/services/blockchain/v10_application.html#dev-app-install-cc-sdk) sur votre homologue.

### Utilisation du logiciel SDK pour instancier le code blockchain sur l'homologue
{: #remote-peer-aws-operate-instantiate-cc-sdk}

Un seul membre de ce canal doit instancier ou mettre à jour le code blockchain. Par conséquent, tout membre réseau du canal avec des homologues sur {{site.data.keyword.blockchainfull_notm}} Platform peut utiliser le Moniteur réseau pour instancier du code blockchain et spécifier les règles de validation. Toutefois, si vous souhaitez utiliser l'homologue pour instancier du code blockchain sur un canal, vous pouvez utiliser le logiciel SDK et suivre les instructions d'[instanciation d'un code blockchain](/docs/services/blockchain/v10_application.html#dev-app-instantiate-cc-sdk).


## Utilisation de l'interface CLI pour exploiter l'homologue
{: #remote-peer-aws-operate-cli-operate}

Vous pouvez également exploiter votre homologue depuis la ligne de commande à l'aide du client CA Fabric et du conteneur d'outils Fabric. Dans les présentes instructions, nous allons d'abord générer les certificats requis à l'aide du client d'autorité de certification Fabric. Nous utiliserons ensuite le conteneur d'outils Fabric pour exploiter l'homologue en l'associant à un canal, en installant un code blockchain, puis en instanciant ce code blockchain sur un canal.

### Inscription à l'aide du client d'autorité de certification Fabric
{: #remote-peer-aws-operate-client-enroll}

La première étape consiste à générer les certificats requis (inscription) à l'aide du client d'autorité de certification Fabric. Vous devez d'abord installer le client d'autorité de certification Fabric. Téléchargez les fichiers [fabric-ca binaries v1.2.1 de votre plateforme](https://nexus.hyperledger.org/content/repositories/releases/org/hyperledger/fabric-ca/hyperledger-fabric-ca/){: external} sur votre machine locale, extrayez-les et placez-les dans un dossier, par exemple `$HOME/fabric-ca-remote/`.

1.  Préparez votre environnement pour utiliser le client d'autorité de certification Fabric. Accédez au répertoire dans lequel vous avez placé les fichiers binaires du client afin de pouvoir y faire référence directement dans vos commandes.
    ```
    cd $HOME/fabric-ca-remote/
    ```
    {:codeblock}

2.  Définissez le chemin dans lequel le client peut créer vos clés.  S'il s'agit de la première fois que vous exécutez la commande `enroll`, le dossier `msp` et le fichier `.yaml` n'existent pas. Si vous avez exécuté la commande `enroll` auparavant, il est important de supprimer tout matériel de configuration des précédentes tentatives d'inscription à l'aide des commandes `rm` ci-dessous :
    ```
    export FABRIC_CA_CLIENT_HOME=$HOME/fabric-ca-remote
    rm -rf $FABRIC_CA_CLIENT_HOME/fabric-ca-client-config.yaml
    rm -rf $FABRIC_CA_CLIENT_HOME/msp
    ```
    {:codeblock}

3.  Vous devrez extraire les informations de noeud final de votre autorité de certification sur {{site.data.keyword.blockchainfull_notm}} Platform. A l'écran "Présentation" de votre Moniteur réseau, cliquez sur le bouton **Profil de connexion** et ouvrez le fichier JSON qui contient les données d'identification réseau. Faites défiler jusqu'à la section `certificateAuthorities` et notez les informations ci-dessous.
    ```
    Hostname and port for CA: url (without the https prefix)
    Admin user ID: enrollId
    Admin password: enrollSecret
    CA Name: caName
    ```

4.  Vous devrez également extraire un certificat TLS d'{{site.data.keyword.blockchainfull_notm}} Platform pour communiquer avec l'autorité de certification. Les données d'identification réseau incluent le certificat nécessaire. Dans la section `certificateAuthorities` du fichier du profil de connexion, copiez le certificat qui suit `"pem:"`, qui commence par `-----BEGIN CERTIFICATE----` et se termine par `-----END CERTIFICATE----`. **N'incluez pas les apostrophes**.

    Exécutez la commande suivante dans une fenêtre de terminal, en remplaçant `<certificate>` par votre certificat copié.
    ```
    echo -e "<certificate>" > $HOME/fabric-ca-remote/cert.pem
    ```
    {:codeblock}

 Conservez ce certificat dans un emplacement où vous pouvez y faire référence dans les commandes futures.  

5.  Vous êtes maintenant prêt à générer les certificats requis. Exécution de la commande suivante :
    ```
    ./fabric-ca-client enroll -u https://<enroll_id>:<enrollSecret>@<ca_hostname_with_port> --caname <ca_name> --tls.certfiles <tls_cert_file>
    ```
    {:codeblock}

    Par exemple :
    ```
    ./fabric-ca-client enroll -u https://admin:C25A062870@ash-zbc07c.4.secure.blockchain.ibm.com:21241 --tls.certfiles $HOME/fabric-ca-remote/cert.pem --caname PeerOrg1CA
    ```
    {:codeblock}

    **Astuce :** Si la valeur de l'URL d'enregistrement, valeur de paramètre `-u`, contient un caractère spécial, vous devez l'encoder ou indiquer l'URL d'enregistrement entre guillemets simples. Par exemple, `!` devient `%21`, ou la commande ressemble à ceci :

    ```
    ./fabric-ca-client enroll -u 'https://admin:C25A06287!0@ash-zbc07c.4.secure.blockchain.ibm.com:21241' --tls.certfiles $HOME/fabric-ca-remote/cert.pem --caname PeerOrg1CA
    ```
    {:codeblock}

    Lorsque la commande aboutit, vous pouvez voir une réponse semblable à l'exemple suivant :
    ```
    2018/06/13 09:00:45 [INFO] Created a default configuration file at
    /fabric-ca-remote/fabric-ca-client-config.yaml
    2018/06/13 09:00:45 [INFO] TLS Enabled
    2018/06/13 09:00:45 [INFO] generating key: &{A:ecdsa S:256}
    2018/06/13 09:00:45 [INFO] encoded CSR
    2018/06/13 09:00:46 [INFO] Stored client certificate at
    /fabric-ca-remote/msp/signcerts/cert.pem
    2018/06/13 09:00:46 [INFO] Stored root CA certificate
    at /fabric-ca-remote/msp/cacerts/ash-4-secure-blockchain-ibm-com-71139-PeerOrg1CA.pem
    2018/06/13 09:00:46 [INFO] Stored intermediate CA certificates at
    /fabric-ca-remote/intermediatecerts/ash-4-secure-blockchain-ibm-com-71139-PeerOrg1CA.pem
    ```

    La commande génère les certificats requis et les stocke dans un dossier nommé `msp` dans `$FABRIC_CA_CLIENT_HOME`. Ce dossier et les certificats qui y figurent sont importants dans les étapes suivantes.

### Gestion des certificats sur votre système local
{: #remote-peer-aws-operate-manage-certs}

Pour pouvoir exploiter l'homologue, nous devons effectuer des opérations de gestion des certificats sur la machine locale, et envoyer par téléchargement certains certificats générés par le client CA Fabric pour {{site.data.keyword.blockchainfull_notm}} Platform et votre homologue. Nous devons également télécharger les certificats TLS à partir de la plateforme et de l'homologue. Si vous souhaitez en savoir plus sur les certificats que vous allez utiliser et les tâches que vous allez exécuter, voir [Gestion des certificats sur {{site.data.keyword.blockchainfull_notm}}](/docs/services/blockchain/certificates.html#managing-certificates) Platform.

Sur votre machine locale, ouvrez un terminal de commandes et accédez au répertoire dans lequel vous avez déplacé les fichiers binaires Fabric-CA-Client et stocké le dossier MSP.

1. Copiez le fichier `cert.pem` du dossier `signcerts` dans un nouveau dossier `admincerts`.
   ```
   cd /$FABRIC_CA_CLIENT_HOME/msp/
   mkdir admincerts
   cd admincerts/
   cp ../signcerts/cert.pem  .
   ```
   {:codeblock}

2. Copiez le certificat TLS de vos services de tri de {{site.data.keyword.blockchainfull_notm}} Platform dans le dossier MSP. Votre profil de connexions contient le certificat nécessaire. A l'écran "Présentation" de votre Moniteur réseau, cliquez sur le bouton **Profil de connexion** et ouvrez le fichier JSON qui contient les données d'identification réseau. Accédez à la section `orderers`. Copiez le certificat qui suit `"pem:"`, commençant par `-----BEGIN CERTIFICATE-----` et se terminant par `-----END CERTIFICATE----- `. N'incluez pas les apostrophes.

    Depuis votre fenêtre de terminal, exécutez les commandes suivantes :
    ```
    cd /$FABRIC_CA_CLIENT_HOME/msp
    echo -e "<paste in the certificate here>" > orderer_tlscacert.pem
    ```
    {:codeblock}

3. Vous devez aussi copier le certificat TLS de votre homologue du conteneur d'homologue sur AWS vers votre machine locale.

    - [Suivez ces instructions](/docs/services/blockchain/howto/remote_peer_aws.html#remote-peer-aws-test) pour vous connecter à votre conteneur homologue et exécutez la commande suivante, en remplaçant <PEER_ENROLL_ID> par le nom de pile de l'homologue, que vous avez indiqué dans le modèle de démarrage rapide, suivi par son numéro. (Rappel : deux instances VPC sont créées.)
      ```
      cat /etc/hyperledger/<PEER_ENROLL_ID>/tls/ca.crt
      ```
      {:codeblock}

      Copiez l'intégralité du texte du fichier `cacert.pem` dans votre presse-papiers, qui commence par le premier `-----BEGIN CERTIFICATE-----` et se termine par le tout dernier `-----END CERTIFICATE-----`.

    - Revenez sur votre machine locale et exécutez les commandes suivantes. Remplacez le texte `<CACERT.PEM>` par le texte du presse-papiers.
      ```
      cd /$FABRIC_CA_CLIENT_HOME/msp
    mkdir tls
    cd tls/
    echo -e "<CACERT.PEM>" > cacert.pem
      ```
      {:codeblock}

      **Remarque :** Par défaut, le modèle de démarrage rapide AWS crée deux instances homologue dans deux zones de disponibilité différentes. Si vous avez déjà exécuté ces étapes pour l'un de ces homologues, lorsque vous exécutez les étapes de la deuxième instance, le fichier cacert.pem file existe déjà. Continuez et remplacez-le par le certificat du second homologue.

4. Pour donner à votre interface CLI l'autorisation d'installer le code blockchain sur l'homologue, envoyez par téléchargement le certificat signataire généré par le client CA Fabric dans le dossier admin de l'homologue et redémarrez ce dernier. Par conséquent, copiez le certificat `admincert/cert.pem` de votre machine locale dans le répertoire `/etc/hyperledger/<PEER_ENROLL_ID>/msp/admincerts/` dans le conteneur d'homologues container en tant que `cert2.pem`.

    - Sur votre machine locale, exécutez les commandes suivantes :

      ```
      cd /$FABRIC_CA_CLIENT_HOME/msp/admincerts
      cat cert.pem
      ```
      {:codeblock}

    - Copiez le texte du fichier `cert.pem` dans votre presse-papiers à partir de `-----BEGIN CERTIFICATE-----` et jusqu'à `-----END CERTIFICATE-----`.

    - Revenez au conteneur homologue et exécutez les commandes suivantes pour ajouter le fichier cert.pem aux certificats de l'homologue. Remplacez le texte `<CERT.PEM>` par le texte du presse-papiers.

      ```
      cd /etc/hyperledger/<PEER_ENROLL_ID>/msp/admincerts/
      echo -e "<CERT.PEM>" > cert2.pem
      ```
      {:codeblock}

      **Remarque **: un fichier cert.pem existe déjà dans ce répertoire. Ne le remplacez pas.

    - Etant donné que vous avez ajouté un nouveau certificat, vous devez redémarrer le conteneur pour que l'homologue prélève le certificat. Suivez ces instructions pour [redémarrer le conteneur homologue](/docs/services/blockchain/howto/remote_peer_operate_aws.html#remote-peer-aws-operate-restart).

5. Envoyez par téléchargement le même certificat `admincert/cert.pem` que celui de votre machine locale à {{site.data.keyword.blockchainfull_notm}} Platform afin qu'une interface CLI ou une application distante puisse effectuer des opérations de canal, comme l'extraction du bloc d'origine du canal et l'instanciation de code blockchain.
    1. Sur votre machine locale, coupez le fichier `/$FABRIC_CA_CLIENT_HOME/msp/admincerts/cert.pem` et copiez-le dans le presse-papiers.
    2. Accédez au Moniteur réseau de votre réseau sur {{site.data.keyword.blockchainfull_notm}} Platform.
    3. Cliquez sur **Membres** dans le navigateur de gauche et cliquez sur l'onglet **Certificats**.
    4. Cliquez sur le bouton **Ajouter un certificat**.
    5. Dans la fenêtre **Ajouter un certificat**, donnez un nom à votre certificat, par exemple `fabrictools.pem`, collez le certificat que vous venez de copier dans le presse-papiers et cliquez sur **Soumettre**.
    6. Il vous sera peut-être demandé si vous souhaitez redémarrer les homologues. Si tel est le cas, cliquez sur **Redémarrer**.
    7. Cliquez sur **Canaux** dans le navigateur de gauche et recherchez le canal que l'homologue va rejoindre.
    8. Cliquez sur les trois points sous l'en-tête **Actions** et cliquez sur **Synchroniser le certificat**. Dans la fenêtre **Synchroniser le certificat**, cliquez sur **Soumettre**.

    **Remarque **: Il est important de synchroniser le certificat de canal avant que l'homologue ne rejoigne le canal ou instancie le code blockchain sur le canal. Vous devrez peut-être attendre quelques minutes le temps que le canal se synchronise avant l'exécution des commandes join channel ou l'instanciation de commandes de code blockchain.   

### Configuration du conteneur d'outils Fabric
{: #remote-peer-aws-operate-fabric-cli}

Après avoir déplacé tous vos certificats vers l'emplacement nécessaire, vous pouvez installer et utiliser le conteneur d'outils Fabric de Docker. Ces commandes sont destinées à être exécutées en local sur votre machine. Assurez-vous d'exécuter ces commandes à partir du répertoire dans lequel vous avez stocké votre dossier MSP. Avant de terminer ces étapes, [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git){: external} doit être installé sur votre machine locale.   

Téléchargez l'image Docker des outils Fabric à l'aide de la commande suivante :

```
docker pull ibmblockchain/fabric-tools:1.2.1
```
{:codeblock}

#### Collecte de ressources pour le conteneur    

Nous devons définir les mêmes dossiers sur votre machine locale pour y placer l'exemple `fabcar` qui sera utilisé ultérieurement lors de l'installation et de l'instanciation de code blockchain. Exécutez les commandes suivantes pour définir la structure de dossiers de l'exemple de code blockchain, puis téléchargez celui-ci à l'aide de Git.

```
mkdir toolsrc
cd toolsrc
mkdir mycc
mkdir vendor
cd vendor
git clone https://github.com/hyperledger/fabric.git
```
{:codeblock}

**Remarque :** Si vous disposez de vos propres fichiers de code blockchain, vous pouvez les placer dans le dossier `mycc` afin qu'ils puissent être utilisés par les commandes CLI de l'homologue.  

Exécutez les commandes suivantes pour démarrer le conteneur d'outils Fabric. La deuxième commande monte le répertoire MSP dans votre dossiers d'exemples Fabric au sein de votre conteneur d'outils. Assurez-vous d'exécuter ces commandes à partir du répertoire dans lequel vous avez stocké votre dossier MSP.

```
docker network create blockchain.com
docker run -ti --network blockchain.com -v ${PWD}:/mnt -v path/to/toolsrc:/src ibmblockchain/fabric-tools:1.2.1
```
{:codeblock}


<!--
3.  The peer address must resolve to a domain name with a suffix of `blockchain.com`. You can do this either via your DNS or modify your /etc/hosts file. For purposes of these instructions, we will modify the `/etc/hosts` file in the Fabric tools container. To retrieve the endpoint information of your peer, locate your peer instance in the AWS console. Make note of the value of the AWS `IPv4 Public IP` for the EC2 instance.

    ```
    echo -e "<AWS_IPv4_PUBLIC_IP> remotepeer.blockchain.com" >> /etc/hosts
    ```
    {:codeblock}
-->

### Utilisation de l'interface CLI des outils Fabric pour joindre l'homologue au canal
{: #remote-peer-aws-operate-cli-join-channel}

Avant d'exécuter les commandes d'interface CLI pour joindre l'homologue à un canal, il est nécessaire d'ajouter votre organisation à un canal du réseau.

  - Vous pouvez démarrer un nouveau canal pour l'homologue. En tant qu'initiateur de canal, vous pouvez inclure automatiquement votre organisation durant la [création de canal](/docs/services/blockchain/howto/create_channel.html#ibp-create-channel-creating-a-channel).

  - Un autre membre du réseau blockchain peut également ajouter votre organisation à un canal existant en utilisant une [mise à jour de canal](/docs/services/blockchain/howto/create_channel.html#ibp-create-channel-updating-a-channel).

    Une fois que votre organisation est ajoutée à un canal, vous devez ajouter le certificat signataire de votre homologue au canal de sorte que les autres membres puissent vérifier votre signature numérique au cours des transactions. L'homologue envoie par téléchargement son certificat signataire lors de l'installation, de sorte que vous devez uniquement synchroniser le certificat pour le canal. Dans l'écran "Canaux" de votre Moniteur réseau, localisez le canal rejoint par votre organisation et sélectionnez **Synchroniser le certificat** dans la liste déroulante sous l'en-tête **Action**. Cette action synchronise les certificats entre tous les homologues sur le canal.

1. Procédez à l'extraction des informations de configuration de votre `profil de connexion` disponible dans l'écran Présentation du Moniteur réseau. Cliquez sur **Profil de connexion**, puis sur **Télécharger**.

  - Localisez l'URL du service de tri en recherchant **orderers**, qui se trouve sous `orderers > url`. Notez l'URL qui commence par le nom réseau. L'URL est similaire à l'exemple suivant :

    ```
    ash-zbc07b.4.secure.blockchain.ibm.com:21239
    ```

  - Localisez le nom de votre organisation en recherchant **organizations**. Il doit s'agir de la même organisation que celle que vous utilisez pour enregistrer votre homologue. Vous pouvez trouver le nom de votre organisation ainsi que le `mspid` associé. Notez la valeur de `mspid`.

2. Recherchez les informations de noeud final de votre homologue VPC AWS (l'adresse IPv4 DNS publique) dans le DNS public du tableau de bord AWS EC2 (IPv4). Elles devraient être similaires à ceci :

  ```
  ec2-10-221-8-71.us-north-2.compute.amazonaws.com
  ```

  Utilisez ces informations pour générer la variable d'environnement `PEERADDR` en concaténant l'adresse avec le port '7051', de sorte que
la valeur de `PEERADDR` serait similaire à ceci :

  ```
  ec2-10-221-8-71.us-north-2.compute.amazonaws.com:7051
  ```
3. Exécutez les commandes suivantes pour définir les variables d'environnement dans le conteneur d'outils Fabric.

    ```
    export ORDERER_1=<ORDERER_URL>
  export CHANNEL=<CHANNEL_NAME>
  export CC_NAME=<CC_NAME>
  export ORGID=<ORGANIZATION_MSP_ID>
  export PEERADDR=<PEER_ADDR>
    ```
    {:codeblock}

    Remplacez les zones par vos informations.
      - Remplacez `<ORDERER_URL>` par le nom d'hôte et le port du service de tri du fichier `creds.json`.
      - Remplacez `<CHANNEL_NAME>` par le nom du canal que rejoint l'homologue.
      - Remplacez `<CC_NAME>` par un nom pour faire référence à votre code blockchain.
      - Remplacez `<ORGANIZATION_MSP_ID>` par le nom de l'organisation du fichier `creds.json`.
      - Remplacez `<PEER_ADDR>` par la valeur que vous avez construite à l'étape précédente.  

  Par exemple :

    ```
    export ORDERER_1=ash-zbc07b.4.secure.blockchain.ibm.com:21239
    export CHANNEL=defaultchannel
    export CC_NAME=mycc
    export ORGID=PeerOrg1
    export PEERADDR=ec2-10-221-8-71.us-north-2.compute.amazonaws.com:7051
    ```
    {:codeblock}

3. Extrayez le bloc d'origine du canal pour générer le registre de canal sur votre homologue. Accédez (`cd`) d'abord à votre répertoire racine, puis exécutez la commande d'extraction du bloc d'origine.

  ```
  cd /

  GOPATH=/ CORE_PEER_TLS_ROOTCERT_FILE=/mnt/msp/tls/cacert.pem CORE_PEER_TLS_ENABLED=true CORE_PEER_ADDRESS=${PEERADDR} CORE_PEER_LOCALMSPID=${ORGID} CORE_PEER_MSPCONFIGPATH=/mnt/msp/ GOPATH=/ peer channel fetch 0 -o ${ORDERER_1} -c ${CHANNEL} --cafile /mnt/msp/orderer_tlscacert.pem --tls
  ```
  {:codeblock}

  **Remarque :** Il est possible que lors de l'exécution de l'une de ces commandes de l'interface CLI, vous obteniez l'avertissement suivant qui peut être ignoré.

  ```
  [msp] getPemMaterialFromDir -> WARN 001 Failed reading file
     /mnt/crypto/peer/peer/msp/intermediatecerts/<intermediate cert name>.pem: no pem content for file  /mnt/crypto/peer/peer/msp/intermediatecerts/<intermediate cert name>.pem
     ```

  Exécutez la commande suivante pour vérifier que le bloc d'origine est ajouté à votre conteneur homologue avec succès :

  ```
  ls *.block
  ```
  {:codeblock}

  Une fois le bloc d'origine ajouté, vous devez voir quelque chose de similaire à l'exemple suivant :
  ```
  defaultchannel_0.block
  ```
  <!-- removing the code block since this is a result and not an executable command
  {:codeblock}
  -->
4. Joignez maintenant l'homologue au canal, en transmettant le bloc d'origine à l'aide de la commande suivante :

  ```
  GOPATH=/ CORE_PEER_TLS_ROOTCERT_FILE=/mnt/msp/tls/cacert.pem CORE_PEER_TLS_ENABLED=true CORE_PEER_ADDRESS=${PEERADDR} CORE_PEER_LOCALMSPID=${ORGID} CORE_PEER_MSPCONFIGPATH=/mnt/msp/ GOPATH=/ peer channel join -b ${CHANNEL}_0.block
  ```
  {:codeblock}

  Lorsque cette opération est exécutée correctement, vous devriez voir un quelque chose de similaire à ceci :

  ```
  2018-07-06 18:32:09.509 UTC [channelCmd] InitCmdFactory -> INFO 001 Endorser and orderer connections initialized
  2018-07-06 18:32:09.992 UTC [channelCmd] executeJoin -> INFO 002 Successfully submitted proposal to join channel
  2018-07-06 18:32:09.992 UTC [main] main -> INFO 003 Exiting.....
  ```

### Utilisation du conteneur d'outils Fabric pour installer le code blockchain sur l'homologue
{: #aws-toolcontainer-install-cc}

Nous sommes maintenant prêts à installer et à instancier le code blockchain sur l'homologue. Dans le cadre des présentes instructions, nous installerons le code blockchain `fabcar` du référentiel Hyperledger `fabric-samples` que vous devez avoir déjà téléchargé sur votre machine locale lors de la [configuration de votre conteneur d'outils Fabric](/docs/services/blockchain/howto/remote_peer_operate_aws.html#remote-peer-aws-operate-cli-operate).  

Exécutez la commande d'interface CLI d'homologue suivante afin d'installer le code blockchain `fabcar` sur l'homologue.

  ```
  GOPATH=/ CORE_PEER_TLS_ROOTCERT_FILE=/mnt/msp/tls/cacert.pem CORE_PEER_TLS_ENABLED=true CORE_PEER_ADDRESS=${PEERADDR} CORE_PEER_LOCALMSPID=${ORGID} CORE_PEER_MSPCONFIGPATH=/mnt/msp/ GOPATH=/ peer chaincode install -n ${CC_NAME} -v v0 -p fabric-samples/chaincode/fabcar/go/
  ```
  {:codeblock}

  Lorsque cette commande est exécutée correctement, vous devriez voir un quelque chose de similaire à ceci :

  ```
  2018-07-06 18:39:00.461 UTC [chaincodeCmd] checkChaincodeCmdParams -> INFO 001 Using default escc
  2018-07-06 18:39:00.461 UTC [chaincodeCmd] checkChaincodeCmdParams -> INFO 002 Using default vscc
  2018-07-06 18:39:01.142 UTC [main] main -> INFO 003 Exiting.....
  ```

### Utilisation du conteneur d'outils Fabric pour instancier le code blockchain sur un canal
{: #remote-peer-aws-operate-oolcontainer-instantiate-cc}

Etant donné qu'un seul homologue doit instancier du code blockchain sur un canal, vous n'avez pas à utiliser votre homologue pour instancier du code blockchain. Les homologues hébergés sur {{site.data.keyword.blockchainfull_notm}} Platform peuvent faire cela. Toutefois, si vous préférez que l'homologue instancie du code blockchain sur le canal, vous pouvez exécuter la commande suivante dans le conteneur d'outils Fabric :

```
CORE_PEER_TLS_ROOTCERT_FILE=/mnt/msp/tls/cacert.pem CORE_PEER_TLS_ENABLED=true CORE_PEER_ADDRESS=${PEERADDR} CORE_PEER_LOCALMSPID=${ORGID} CORE_PEER_MSPCONFIGPATH=/mnt/msp/ GOPATH=/ peer chaincode instantiate -o ${ORDERER_1} -C ${CHANNEL} -n ${CC_NAME} -v v0 -c '{"Args":[""]}' --tls --cafile /mnt/msp/orderer_tlscacert.pem -P ""
```
{:codeblock}

Lorsque cette commande est exécutée correctement, vous devriez voir un quelque chose de similaire à ceci :

```
2018-07-06 18:43:15.066 UTC [chaincodeCmd] checkChaincodeCmdParams -> INFO 001 Using default escc
2018-07-06 18:43:15.066 UTC [chaincodeCmd] checkChaincodeCmdParams -> INFO 002 Using default vscc
2018-07-06 18:43:50.227 UTC [main] main -> INFO 003 Exiting.....
```


## Redémarrage d'un homologue qui est en cours d'exécution dans AWS
{: #remote-peer-aws-operate-restart}

Vous pouvez démarrer, arrêter ou redémarrer votre homologue dans l'environnement sur lequel vous déployez l'homologue. Chaque fois qu'un certificat est ajouté à l'homologue, l'homologue doit être redémarré afin que le nouveau certificat puisse être reconnu. Il existe plusieurs façons de procéder :

- Dans la console AWS, redémarrez l'instance VPC de l'homologue.
- Depuis votre conteneur homologue, exécutez la commande suivante :

 ```
 docker restart peer
 ```
 {:codeblock}  

Vous pouvez également utiliser la [demande HEAD](/docs/services/blockchain/howto/monitor_network.html#monitor-blockchain-network-monitor-nodes) pour vérifier la disponibilité de votre homologue.

## Affichage des journaux de l'homologue

Lancez SSH dans l'instance homologue AWS VPC, puis exécutez la commande suivante pour afficher les journaux de l'homologue :

```
docker logs peer
```
{:codeblock}

## Mise à jour du code blockchain
{: #remote-peer-aws-operate-update-cc}

Il est probable qu'au fil du temps vous devrez modifier le code blockchain qui s'exécute sur l'homologue. Etant donne que le code blockchain est installé sur les homologues et instancié sur le canal, vous devez mettre à jour le code blockchain sur tous les homologues du canal.

Procédez comme suit pour mettre à jour votre code blockchain :

1. Pour mettre à jour le code blockchain sur chaque homologue dans AWS, relancez simplement le processus utilisé pour installer le code blockchain sur les homologues, au moyen d'une application client ou d'une commande d'interface de ligne de commande. Veillez à indiquer le même nom de code blockchain que celui utilisé initialement. Toutefois, cette fois incrémentez le numéro de `version` du code blockchain.

2. Une fois le nouveau code blockchain installé sur tous les homologues du canal, utilisez le Moniteur réseau ou la commande [peer chaincode upgrade](https://hyperledger-fabric.readthedocs.io/en/release-1.2/commands/peerchaincode.html#peer-chaincode-upgrade){: external} pour mettre à jour le canal qui va utiliser le nouveau code blockchain.

Consultez l'étape 2 des présentes [instructions](/docs/services/blockchain/howto/install_instantiate_chaincode.html#install-instantiate-chaincode-update-cc) pour plus d'informations sur l'utilisation du panneau "Installer le code" du Moniteur réseau pour la mise à jour du code blockchain sur le canal.

## Traitement des incidents
{: #remote-peer-aws-operate-troubleshooting}

### **Problème :** l'homologue distant ne peut pas se connecter au réseau de blockchain
{: #remote-peer-aws-operate-problem-1}

La création de la pile a abouti, mais les journaux Docker contiennent l'erreur suivante :

```
[main] main -> ERRO 001 Cannot run peer because error when setting up MSP of type bccsp from directory /etc/hyperledger/awspeer1/msp: Setup error: nil conf reference
```

**Solution :**  
Cette erreur peut être due au fait que vous avez oublié de spécifier un port sur CAUrl lors du déploiement du modèle de démarrage rapide.
Le CAUrl doit être similaire à `https://<network>-org1-ca.stage.blockchain.ibm.com:31011`.
Redéployez le modèle de démarrage rapide, en prenant soin d'indiquer la valeur adéquate pour CAUrl.

### **Problème :** l'instanciation du code blockchain échoue avec une erreur
{: #remote-peer-aws-operate-problem-2}

L'instanciation du code blockchain échoue avec l'erreur suivante :
```
Error: Error endorsing chaincode: rpc error: code = Unknown desc = chaincode error (status: 500, message: instantiation policy violation: signature set did not satisfy policy)
```

**Solution :**   
Vérifiez, après le téléchargement du certificat admin vers le Moniteur réseau, que les certificats sont ensuite synchronisées sur le canal. Reportez-vous à l'étape 5 des présentes [instructions](/docs/services/blockchain/howto/remote_peer_operate_aws.html#remote-peer-aws-operate-manage-certs) pour plus d'informations. Gardez à l'esprit qu'il est important de synchroniser le certificat de canal avant que l'homologue ne rejoigne le canal.
