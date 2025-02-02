---

copyright:
  years: 2019
lastupdated: "2019-05-31"

keywords: client application, Commercial Paper, SDK, wallet, generate a certificate, generate a private key, fabric gateway, APIs, smart contract

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

# Criando aplicativos
{: #ibp-console-app}

Depois de instalar contratos inteligentes e implementar seus nós, é possível usar os aplicativos clientes para transacionar com outros membros de sua rede. Os aplicativos podem chamar a lógica de negócios contida em contratos inteligentes para criar, transferir ou atualizar ativos no livro-razão do blockchain. Use este tutorial para aprender como usar os aplicativos clientes para interagirem com redes que você gerencia por meio do console do {{site.data.keyword.blockchainfull}} Platform.
{:shortdesc}

**Público-alvo:** este tópico é projetado para desenvolvedores de aplicativos que estejam interessados em aprender mais sobre como criar um aplicativo cliente que interage com uma rede de blockchain.

## Recursos de Aprendiz
{: #ibp-console-app-learning-resources}

É possível aprender mais sobre como os aplicativos e os contratos inteligentes funcionam juntos na amostra Commercial Paper. Visite o tópico sobre como [Executar a amostra de papel comercial no {{site.data.keyword.blockchainfull_notm}} Platform](/docs/services/blockchain/howto/ibp-console-create-app.html#ibp-console-app-commercial-paper)| no qual é possível aprender a implementar e chamar o contrato de papel comercial.

Desenvolver um aplicativo pode requerer coordenação entre dois usuários distintos de sua rede, o operador de rede e o desenvolvedor de aplicativos:
- **O operador de rede** é o administrador que usa o console do {{site.data.keyword.blockchainfull_notm}} Platform para implementar os nós de sua organização e instala os contratos inteligentes em sua rede.
- **O desenvolvedor de aplicativos** constrói o aplicativo cliente que será consumido pelos usuários finais. O desenvolvedor usa os [SDKs do Hyperledger Fabric](https://hyperledger-fabric.readthedocs.io/en/release-1.4/getting_started.html#hyperledger-fabric-sdks){: external} para chamar transações gravadas nos contratos inteligentes.

Se você for o **operador de rede**, será necessário concluir as etapas a seguir antes de o desenvolvedor de aplicativos poder interagir com a sua rede:
1. Use sua CA da organização para [ registrar uma identidade de aplicativo](/docs/services/blockchain/howto/ibp-console-create-app.html#ibp-console-app-identities).
2. [Faça download do perfil de conexão](/docs/services/blockchain/howto/ibp-console-create-app.html#ibp-console-app-profile) no painel de contratos inteligentes.
3. Envie ao desenvolvedor de aplicativos os objetos e informações a seguir:
  - O ID de inscrição e o segredo da identidade do aplicativo.
  - O perfil de conexão.
  - O nome do contrato inteligente.
  - O nome do canal em que o contrato inteligente foi instanciado.  

Se você for o ** desenvolvedor de aplicativos**, use as informações fornecidas pelo operador de rede para concluir as etapas a seguir:
1. Gere um certificado e uma chave privada usando o ID de inscrição e o segredo da identidade do aplicativo, junto com as informações do terminal de CA dentro de seu perfil de conexão.
2. Use o perfil de conexão, o nome do canal, o nome do contrato inteligente e as chaves do aplicativo para chamar o contrato inteligente.  

O perfil de conexão transferido por download do console do {{site.data.keyword.blockchainfull_notm}} Platform pode ser usado apenas para se conectar à sua rede usando os SDKs do Fabric do Node.js (JavaScript e TypeScript) e do Java.
{: note}

O desenvolvedor de aplicativos pode usar dois modelos de programação para interagir com a rede:

** APIs do High Level Fabric SDK **

Iniciando com o Fabric v1.4, os usuários podem tirar vantagem de um modelo de programação de aplicativo simplificado e de contrato inteligente. O novo modelo reduz o número de etapas e a quantia de código necessária para enviar uma transação. Esse modelo é suportado somente para aplicativos gravados em **Node.js**. Se desejar aproveitar o novo modelo, será possível usar este tutorial para concluir as ações a seguir em uma rede do {{site.data.keyword.blockchainfull_notm}} Platform:

- [Gere certificados para o seu aplicativo](/docs/services/blockchain/howto/ibp-console-create-app.html#ibp-console-app-enroll) usando o SDK.
- [Chame um contrato inteligente por meio do SDK](/docs/services/blockchain/howto/ibp-console-create-app.html#ibp-console-app-invoke).
- Aprenda sobre o desenvolvimento de aplicativo implementando o [tutorial de papel comercial](/docs/services/blockchain/howto/ibp-console-create-app.html#ibp-console-app-commercial-paper) para os nós gerenciados em seu console. Este tutorial fornecerá mais informações sobre como usar Carteiras eletrônicas e Gateways do Fabric.

**APIs do SDK do Fabric de baixo nível**

Se você quiser continuar usando o seu contrato inteligente e o código do aplicativo existentes ou outras linguagens do SDK do Fabric fornecidas pela comunidade do Hyperledger, será possível usar as [APIs do SDK do Fabric de baixo nível](/docs/services/blockchain/howto/ibp-console-create-app.html#ibp-console-app-low-level) para se conectar à sua rede.

## Registrando uma identidade de aplicativo
{: #ibp-console-app-identities}

Os aplicativos precisam assinar as transações que eles enviam para os nós do {{site.data.keyword.blockchainfull_notm}} e anexar um certificado de assinatura que é usado pelos nós para verificar se as transações estão sendo enviadas pela parte adequada. Isso assegura que as transações sejam enviadas pelas organizações que têm permissão para participar.

O operador de rede precisa usar a CA da organização para [registrar uma identidade de aplicativo](/docs/services/blockchain/howto?topic=blockchain-ibp-console-identities#ibp-console-identities-register), que pode, então, ser usada pelo desenvolvedor de aplicativos para gerar um certificado e uma chave privada. O operador pode fornecer o ID de inscrição e o segredo da identidade, junto com as informações sobre terminais de CA, a serem usadas pelo SDK para gerar certificados. Inscrevendo-se no lado do cliente, o desenvolvedor de aplicativos assegura que nenhuma outra parte tenha acesso à chave privada do aplicativo. Durante o registro, o operador de rede pode configurar o limite de inscrição a um para segurança adicional. Após a incrição do desenvolvedor de aplicativos, o ID de inscrição e o segredo não poderão ser usados para gerar outra chave privada.

Se você estiver menos preocupado com a segurança, o operador de rede poderá inscrever uma identidade de aplicativo usando a [guia CA](/docs/services/blockchain/howto/ibp-console-identities.html#ibp-console-identities-enroll). Em seguida, o operador pode fazer download da identidade ou exportá-la para a carteira eletrônica do console. Para usar os certificados do SDK, as chaves precisam ser decodificadas de base64 para formato PEM. É possível decodificar os certificados executando o comando a seguir em sua máquina local:

```
export FLAG=$(if [ "$(uname -s)" == "Linux" ]; then echo "-w 0"; else echo "-b 0"; fi)
echo <base64_string> | base64 --decode $FLAG > <key>.pem
```
{:codeblock}

## Fazendo download de seu perfil de conexão
{: #ibp-console-app-profile}

Os aplicativos são capazes de enviar transações somente para os contratos inteligentes que foram instanciados em canais. Como resultado, as informações de que você precisa para se conectar para interagir com um contrato inteligente podem ser localizadas na lista de contratos inteligentes instanciados em seu console. Isso significa que você já deve ter instalado e instanciado seu contrato inteligente.

O perfil de conexão transferido por download do console do {{site.data.keyword.blockchainfull_notm}} Platform pode ser usado apenas para se conectar à sua rede usando os SDKs do Fabric do Node.js (JavaScript e TypeScript) e do Java.
{: note}

O [fluxo de transação](https://hyperledger-fabric.readthedocs.io/en/release-1.4/txflow.html){: external} do Hyperledger Fabric abrange múltiplos componentes, com os aplicativos clientes coletando endossos de peers e enviando transações endossadas para o serviço de pedido. O perfil de conexão fornece a seu aplicativo os terminais dos peers e os nós de pedido que ele precisa para enviar uma transação. Ele também contém informações sobre a sua organização, tais como as autoridades de certificação e o ID do MSP. Os SDKs do Fabric podem ler o perfil de conexão diretamente, sem você ter que gravar o código que gerencia o fluxo de transação e endosso.

Para aproveitar o recurso [Descoberta de serviço](https://hyperledger-fabric.readthedocs.io/en/release-1.4/discovery-overview.html){: external} do Hyperledger Fabric, deve-se configurar peers de âncora. A descoberta de serviço permite que seu aplicativo aprenda quais peers no canal fora de sua organização precisam endossar uma transação. Sem a descoberta de serviço, você precisará obter as informações sobre terminais desses peers fora da banda de outras organizações e incluí-las em seu perfil de conexão. Para obter mais informações, consulte [Configurando peers de âncora](/docs/services/blockchain/howto/ibp-console-govern.html#ibp-console-govern-channels-anchor-peers).

Navegue para a guia **Contratos inteligentes** em seu console de plataforma. Próximo a cada contrato inteligente instanciado, navegue para o menu overflow. Clique no botão chamado **Conectar com SDK**. Isso abrirá um painel lateral que permitirá que você construa e faça download de seu perfil de conexão. Primeiro, é necessário selecionar a CA de sua organização que você usou para registrar sua identidade de aplicativo. Você também precisará selecionar a sua definição do MSP da organização. Então, você será capaz de fazer download do perfil de conexão que pode ser usado para gerar certificados e chamar o contrato inteligente.

## Inrolando usando o SDK
{: #ibp-console-app-enroll}

Quando o operador de rede fornece o ID de inscrição e o segredo da identidade de aplicativo e do perfil de conexão de rede, um desenvolvedor de aplicativos pode usar os SDKs do Fabric ou o cliente Fabric CA para gerar certificados do lado do cliente. É possível usar as etapas a seguir para inscrever uma identidade de aplicativo usando o [Fabric SDK for Node.js](https://fabric-sdk-node.github.io/){: external}.

1. Salve o perfil de conexão em sua máquina local e renomeie-o como `connection.json`.
2. Salve o bloco de códigos a seguir como `enrollUser.js` no mesmo diretório que o seu perfil de conexão:

    ```
    'use strict';

    const FabricCAServices = require('fabric-ca-client'); const { FileSystemWallet, X509WalletMixin } = require('fabric-network'); const fs = require('fs'); const path = require('path');

    const ccpPath = path.resolve(__dirname, 'connection.json');
    const ccpJSON = fs.readFileSync(ccpPath, 'utf8');
    const ccp = JSON.parse(ccpJSON);

    async function main() {
      try {

      // Create a new CA client for interacting with the CA.
      const caURL = ccp.certificateAuthorities['<CA_Name>'].url; const ca = new FabricCAServices(caURL);

      // Create a new file system based wallet for managing identities.
      const walletPath = path.join(process.cwd(), 'wallet');
      const wallet = new FileSystemWallet(walletPath);
      console.log(`Wallet path: ${walletPath}`);

      // Check to see if we've already enrolled the admin user.
      const userExists = await wallet.exists('user1'); if (userExists) {
        console.log('An identity for "user1" already exists in the wallet'); return; }

      // Enroll the admin user, and import the new identity into the wallet.
      const enrollment = await ca.enroll({ enrollmentID: '<app_enroll_id>', enrollmentSecret: '<app_enroll_secret>' });
      const identity = X509WalletMixin.createIdentity('<msp_id>', enrollment.certificate, enrollment.key.toBytes());
      await wallet.import('user1', identity);
      console.log('Successfully enrolled client "user1" and imported it into the wallet');

      } catch (error) { catch (error) {
        console.error(`Failed to enroll "user1": ${error}`); process.exit(1); }
    }

    main ();
    ```
    {:codeblock}

3. Edite `enrollUser.js` para substituir os valores a seguir:
  - Substitua ``<CA_Name>`` pelo nome de sua CA de organizações. É possível localizar o nome de sua CA na seção "organizações" de seu perfil de conexão em "Autoridades de certificação". Não use o "caName" na seção "Autoridades de certificação".
  - Substitua ``<app_enroll_id>`` pelo ID de inscrição de aplicativo fornecido por seu operador de rede.
  - Substitua ``<app_enroll_secret>`` pelo segredo de inscrição de aplicativo fornecido por seu operador de rede.
  - Substitua ``<msp_id>`` pelo ID do MSP de sua organização. É possível localizar seu ID do MSP sob a seção "organizações" de seu perfil de conexão.
4. Navegue para `enrollUser.js` usando um terminal e execute `node enrollUser.js`. Se o comando for executado com êxito, você verá a saída a seguir:

  ```
  Successfully enrolled client "user1" and imported it into the wallet
  ```
  O SDK criará e armazenará os seus certificados dentro do diretório `wallet/user1/` criado pelo comando. Esse diretório é a carteira eletrônica do Sistema de Arquivos usada para enviar transações futuras.

As carteiras usadas pelos SDKs do Fabric são diferentes da carteira eletrônica no console do {{site.data.keyword.blockchainfull_notm}} Platform. As identidades armazenadas em sua carteira eletrônica do console não podem ser usadas diretamente pelo SDK.
{: note}

## Chamando um contrato inteligente usando o SDK
{: #ibp-console-app-invoke}

Depois de ter gerado o certificado de assinatura e a chave privada do aplicativo e armazená-los em uma carteira eletrônica, você estará pronto para enviar uma transação. É necessário saber o nome do contrato inteligente e o nome do canal em que ele foi instanciado. É possível usar as etapas abaixo para chamar um contrato inteligente usando o [Fabric SDK for Node.js](https://fabric-sdk-node.github.io/){: external}.


1. Salve o arquivo abaixo em sua máquina local como `invoke.js`. Salve o arquivo no mesmo diretório que `enrollUser.js`

    ```
    'use strict';

    const { FileSystemWallet, Gateway } = require('fabric-network');
    const fs = require('fs');
    const path = require('path');

    async function main() {
      try {

        // Parse the connection profile. This would be the path to the file downloaded
        // from the IBM Blockchain Platform operational console.
        const ccpPath = path.resolve(__dirname, 'connection.json');
        const ccp = JSON.parse(fs.readFileSync(ccpPath, 'utf8'));

        // Configure uma carteira eletrônica. This wallet must already be primed with an identity that
        // the application can use to interact with the peer node.
        const walletPath = path.resolve(__dirname, 'wallet');
        const wallet = new FileSystemWallet(walletPath);

        // Create a new gateway, and connect to the gateway peer node(s). The identity
        // specified must already exist in the specified wallet.
        const gateway = new Gateway();
        await gateway.connect(ccp, { wallet, identity: 'user1' , discovery: {enabled: true, asLocalhost:false }});

        // Get the network channel that the smart contract is deployed to.
        const network = await gateway.getNetwork('<channel_name>');

        // Get the smart contract from the network channel.
        const contrato = network.getContract ('< smart_contract_name>');

        // Submit the 'createCar' transaction to the smart contract, and wait for it
        // to be committed to the ledger.
        await contract.submitTransaction('createCar', 'CAR12', 'Honda', 'Accord', 'Black', 'Tom');
        console.log('Transaction has been submitted');

        Aguarde gateway.disconnect ();

        } catch (error) { catch (error) {
          console.error(`Failed to submit transaction: ${error}`);
          process.exit(1);
        }
      } main();
    ```
    {:codeblock}

2. Edite o `invoke.js` para substituir os valores a seguir:
  - Substitua ``<channel_name>`` pelo nome do canal no qual o contrato inteligente foi instanciado. É possível localizar seu nome de CA sob a seção "Autoridades de certificação" de seu perfil de conexão.
  - Substitua ``<smart_contract_name>`` pelo nome do contrato inteligente instalado. É possível obter esse valor de seu operador de rede.
  - Edite os conteúdos de `submitTransaction` para chamar uma função dentro de seu contrato inteligente. O arquivo `invoke.js` é gravado para chamar o [contrato inteligente fabcar](https://github.com/hyperledger/fabric-samples/tree/release-1.4/chaincode/fabcar){: external}. Se você desejar executar o arquivo abaixo para enviar uma transação, instale o fabcar e instancie o contrato inteligente em um de seus canais.

3. Navegue para `invoke.js` usando um terminal e execute `node invoke.js`. Se o comando for executado com êxito, você verá a saída a seguir:

  ```
  Transaction has been submitted
  ```
  {:codeblock}
  Se navegar para o canal usando o console, você será capaz de ver outro bloco incluído pela transação.

## Executando a amostra Commercial Paper
{: #ibp-console-app-commercial-paper}

O [tutorial de papel comercial](https://hyperledger-fabric.readthedocs.io/en/release-1.4/tutorial/commercial_paper.html){: external} na Documentação do Hyperledger Fabric leva os desenvolvedores por meio de um caso de uso no qual várias partes compram, vendem e recuperam o papel comercial. Ele amplia o [tópico Desenvolvendo aplicativos](https://hyperledger-fabric.readthedocs.io/en/release-1.4/developapps/developing_applications.html){: external} fornecendo um contrato inteligente de amostra e um código de aplicativo que permite criar e trocar ativos em uma instância local do Fabric.

Também é possível implementar o código de amostra do tutorial de papel comercial em uma rede do {{site.data.keyword.blockchainfull_notm}} Platform. Isso permitirá que você inicie rapidamente a interação com sua rede e use a amostra para fazer download das dependências necessárias. O código de amostra também inclui exemplos de como é possível importar certificados em uma [carteira eletrônica](https://hyperledger-fabric.readthedocs.io/en/release-1.4/developapps/wallet.html){: external} e usar seu perfil de conexão para construir um [gateway do Fabric](https://hyperledger-fabric.readthedocs.io/en/release-1.4/developapps/gateway.html){: external}. O tutorial pode ser usado por duas organizações diferentes para concluir transações diferentes com um único ativo. Se você usou o [tutorial Construir uma rede](/docs/services/blockchain/howto/ibp-console-build-network.html#ibp-console-build-network) para implementar duas organizações de peer conectadas a um canal, é possível interagir com o tutorial usando ambas as organizações.

Siga as etapas abaixo para implementar a amostra em sua rede. É possível revisar o tutorial na Documentação do Fabric [tutorial de papel comercial](https://hyperledger-fabric.readthedocs.io/en/release-1.4/tutorial/commercial_paper.html){: external} para obter mais detalhes sobre os contratos inteligentes e a estrutura do aplicativo.

### Pré-requisitos

Antes de poder implementar a amostra de papel comercial, você precisará instalar as ferramentas necessárias em sua máquina local:
  * [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git){: external}
  * [ Node.js ](https://hyperledger-fabric.readthedocs.io/en/release-1.4/prereqs.html#node-js-runtime-and-npm){: external}

Você também precisará de um editor de texto de uso para editar e salvar arquivos na amostra. É possível usar muitos dos editores de alta qualidade que estão disponíveis gratuitamente, como o [Visual Studio Code](https://code.visualstudio.com/){: external}, o [Atom](https://atom.io/){: external}, o [Sublime text](http://www.sublimetext.com/){: external} ou o [Brackets](http://brackets.io/){: external}.

### Etapa um: Fazer download da amostra

Você faz download da amostra de papel comercial clonando o [Repositório de amostras do Fabric](https://github.com/hyperledger/fabric-samples){: external}:

```
git clone https://github.com/hyperledger/fabric-samples.git
```
{:codeblock}

Depois de ter transferido por download as amostras do Fabric, execute os comandos a seguir para assegurar-se de que você esteja usando a versão das amostras compatíveis com o Fabric v1.4.

```
cd fabric-samples
git checkout v1.4.1
```
{:codeblock}

É possível localizar a amostra na pasta `comercial paper` de `fabric-samples`.

```
cd $HOME/fabric-samples/comercial-paper
```
{:codeblock}

O tutorial contém duas organizações de amostra, **magnetocorp ** e **digibank**. Cada organização tem seu próprio código do aplicativo de amostra, armazenado em duas pastas separadas sob o diretório `organization`.

```
cd organização & & ls digibank magnetocorp
```
{:codeblock}

No curso do tutorial, você usará primeiro o código do aplicativo magnetocorp para emitir um papel comercial. É possível, então, usar o código do aplicativo Digbank para comprar e resgatar o papel. Ambos os diretórios contêm o mesmo contrato inteligente.

Navegue para o código do aplicativo dentro do diretório magnetocorp.

```
cd magnetocorp/aplicativo
```
{:codeblock}

Depois de estar dentro do diretório, é possível fazer download das dependências do aplicativo executando o comando a seguir:

```
npm install
```
{:codeblock}

### Etapa dois: instalar e instanciar o contrato inteligente

É possível localizar o contrato inteligente de papel comercial dentro da pasta `contract` do diretório `digibank` e `magnetocorp`. É necessário instalar esse contrato inteligente em todos os peers das organizações usando o tutorial. Você, então, precisará instanciar o contrato de papel comercial em um canal. O contrato inteligente precisa ser empacotado em [formato .cds](https://hyperledger-fabric.readthedocs.io/en/release-1.4/chaincode4noah.html#packaging){: external} para ser instalado usando o console.

É possível usar a [{{site.data.keyword.blockchainfull_notm}} extensão de código VS](/docs/services/blockchain/vscode-extension.html) para empacotar o contrato inteligente. Depois de instalar a extensão, use o Visual Studio Code para abrir a pasta `contracts` em sua área de trabalho. Abra a guia  _ {{site.data.keyword.blockchainfull_notm}}  Plataforma _ . Na área de janela do _{{site.data.keyword.blockchainfull_notm}} Platform_, navegue para a seção de pacotes de contrato inteligente e clique em **Empacotar um projeto de contrato inteligente**. A extensão do VS Code usará os arquivos na pasta `contracts` para criar um novo pacote denominado `papernet-js@.0.0.1.cds`. Clique com o botão direito nesse pacote para exportá-lo para seu sistema de arquivos local. É possível, então, usar seu console para [instalar os contratos inteligentes em seus peers](/docs/services/blockchain/howto/ibp-console-smart-contracts.html#ibp-console-smart-contracts-install) e, em seguida, [instanciar o contrato inteligente em um canal](/docs/services/blockchain/howto/ibp-console-smart-contracts.html#ibp-console-smart-contracts-instantiate).

### Etapa três: gerar certificados para sua carteira eletrônica

Os aplicativos precisam assinar as solicitações que eles enviam para os componentes de malha. Se os componentes não reconhecerem as organizações que enviam as transações, as transações serão rejeitadas e retornarão com um erro. A amostra de papel comercial cria uma carteira eletrônica do sistema de arquivos que armazenará seus certificados e assinará suas transações. Para obter mais informações sobre como os aplicativos usam carteiras eletrônicas, consulte o tópico [carteira eletrônica](https://hyperledger-fabric.readthedocs.io/en/release-1.4/developapps/wallet.html){: external} na Documentação do Fabric. As carteiras usadas pelos SDKs do Fabric são diferentes da carteira eletrônica no console do {{site.data.keyword.blockchainfull_notm}} Platform. As identidades armazenadas em sua carteira eletrônica do console não podem ser usadas diretamente pelo SDK.

A amostra original usa o arquivo `addToWallet.js` para criar uma carteira eletrônica do sistema de arquivos usando certificados da pasta de amostras de malha. Nós vamos criar um novo arquivo que use o SDK para gerar certificados do lado do cliente e armazená-los diretamente dentro de uma nova carteira eletrônica.

Escolha a CA da organização que você deseja usar para operar o tutorial como magnetocorp. Por exemplo, será possível usar o Org1 se você tiver concluído o tutorial Construir uma rede. Use a CA para [criar uma identidade de aplicativo](/docs/services/blockchain/howto/ibp-console-create-app.html#ibp-console-app-identities). **Salve** o ID de inscrição e o segredo.

Use seu console para [fazer download de seu perfil de conexão](/docs/services/blockchain/howto/ibp-console-create-app.html#ibp-console-app-profile). Salve o perfil de conexão em seu sistema de arquivos local e renomeie-o `connection.json`. Em seguida, use o comando a seguir para mover o perfil de conexão para um diretório no qual ele será referenciado por comandos futuros.

  ```
  mv $HOME/ < path_to_creds> /connection.json /gateway/connection.json
  ```
  {:codeblock}

Navegue para o diretório `/magnetocorp/application` e salve o bloco de códigos a seguir como `enrollUser.js`.

    ```
    'use strict';

    const FabricCAServices = require('fabric-ca-client'); const { FileSystemWallet, X509WalletMixin } = require('fabric-network'); const fs = require('fs'); const path = require('path');

    const ccpPath = path.resolve(__dirname, '../gateway/connection.json');
    const ccpJSON = fs.readFileSync(ccpPath, 'utf8');
    const ccp = JSON.parse(ccpJSON);

    async function main() {
      try {

        // Create a new CA client for interacting with the CA.
        const caURL = ccp.certificateAuthorities['<CA_Name>'].url; const ca = new FabricCAServices(caURL);

        // Create a new file system based wallet for managing identities.
        const wallet = new FileSystemWallet('../identity/user/isabella/wallet');

        // Check to see if we've already enrolled the admin user.
        const userExists = await wallet.exists('user1'); if (userExists) {
          console.log('An identity for "user1" already exists in the wallet'); return; }

        // Enroll the admin user, and import the new identity into the wallet.
        const enrollment = await ca.enroll({ enrollmentID: '<app_enroll_id>', enrollmentSecret: '<app_enroll_secret>' });
        const identity = X509WalletMixin.createIdentity('<msp_id>', enrollment.certificate, enrollment.key.toBytes());
        await wallet.import('user1', identity);
        console.log('Successfully enrolled client "user1" and imported it into the wallet');

        } catch (error) { catch (error) {
          console.error(`Failed to enroll "user1": ${error}`); process.exit(1); }
    } main();
    ```
    {:codeblock}

Devemos reservar um momento para estudar como esse arquivo funciona antes de editá-lo. Primeiro, `enrollUser.js` importa as classes `FileSystemWallet` e `X509WalletMixin` da biblioteca `fabric-network`.

```
const FabricCAServices = require('fabric-ca-client');
const { FileSystemWallet, X509WalletMixin } = require('fabric-network');
```
{:codeblock}

Em seguida, o arquivo usa a classe `FileSystemWallet` para construir uma carteira eletrônica em seu sistema de arquivos local. É possível editar a linha abaixo para armazenar a carteira eletrônica em um local diferente.

```
const carteira = new FileSystemWallet ('../identity/user/isabella/carteira ')
```
{:codeblock}

Após criar a carteira eletrônica, o fragmento de código usa o ID de inscrição e o segredo para se inscrever usando a autoridade de certificação da sua organização. Em seguida, cria uma identidade para o certificado de assinatura e a chave privada e as importa para a carteira eletrônica. Observe como o arquivo passa seu ID do MSP da organização para a carteira eletrônica também.

```
// Enroll the admin user, and import the new identity into the wallet.
const enrollment = await ca.enroll({ enrollmentID: '<app_enroll_id>', enrollmentSecret: '<app_enroll_secret>' }); const identity = X509WalletMixin.createIdentity('<msp_id>', enrollment.certificate, enrollment.key.toBytes()); wallet.import('user1', identity); console.log('Successfully enrolled client "user1" and imported it into the wallet');
```
{:codeblock}

**Edite** `enrollUser.js` para substituir os valores a seguir:
- Substitua `'<CA_Name>'` pelo nome de sua CA de organizações. É possível localizar o nome de sua CA na seção "organizações" de seu perfil de conexão em "Autoridades de certificação". Não use o "caName" na seção "Autoridades de certificação".
- Substitua `'<app_enroll_id>` pelo ID de inscrição de aplicativo fornecido por seu operador de rede.
- Substitua `'<app_enroll_secret>'` pelo segredo de inscrição de aplicativo fornecido por seu operador de rede.
- Substitua `'<msp_id>'` pelo ID do MSP de sua organização. É possível localizar esse ID do MSP sob a seção "organizações" de seu perfil de conexão.

Salve  ` enrollUser.js `  e feche-o. No diretório `magnetocorp`, execute o comando a seguir:
```
node enrollUser.js
```
{:codeblock}

Quando o comando for concluído com êxito, você deverá ver a saída a seguir:

```
Successfully enrolled client "user1" and imported it into the wallet
```
{:codeblock}

É possível localizar a carteira eletrônica que foi criada na pasta `identity` do diretório `magnetocorp`.

### Etapa quatro: usar o perfil de conexão para construir um gateway de malha

O [Fluxo de transação](https://hyperledger-fabric.readthedocs.io/en/release-1.4/txflow.html){: external} do Hyperledger Fabric abrange vários componentes, com os aplicativos clientes desempenhando uma função exclusiva. Seu aplicativo precisa se conectar aos peers que precisam endossar a transação e precisa se conectar ao serviço de pedido que irá solicitar a transação e incluí-la em um bloco. É possível fornecer os terminais desses nós para o seu aplicativo usando seu perfil de conexão para construir um Gateway do Fabric. O Gateway, então, conduz as interações de baixo nível com a sua rede de malha. Para saber mais, visite o tópico [Gateway do Fabric](https://hyperledger-fabric.readthedocs.io/en/release-1.4/developapps/gateway.html){: external} na Documentação do Fabric.

Você já transferiu por download seu perfil de conexão e o usou para se conectar à Autoridade de certificação de sua organização. Agora, usaremos o perfil de conexão para construir um gateway.

Abra o arquivo `issue.js` em um editor de texto. Antes de editar o arquivo, observe se ele importa as classes `FileSystemWallet` e `Gateway` da biblioteca fabric-network.

```
const { FileSystemWallet, Gateway } = require('fabric-network')
```
{:codeblock}

A classe `Gateway` é usada para construir um gateway que você usará para enviar sua transação.

```
const gateway = new Gateway ()
```
{:codeblock}

A classe `FileSystemWallet` é usada para carregar a carteira eletrônica que você criou na etapa anterior. **Edite** a linha abaixo se você tiver mudado o local da carteira eletrônica em seu sistema de arquivos.

```
const wallet = new FileSystemWallet('../identity/user/isabella/wallet');
```
{:codeblock}

Depois de importar sua carteira eletrônica, use o código a seguir para passar o perfil de conexão e a carteira eletrônica para o novo gateway. Será necessário fazer as **Edições** a seguir para o código para que ele se pareça com o fragmento de código abaixo. As linhas que imprimem logs foram removidas por questões de brevidade.
- Atualize o `userName` para corresponder ao valor que você selecionou para o `identityLabel` em `enrollUser.js`.
- Atualize as opções de descoberta para tirar proveito da descoberta de serviço em sua rede. Configure `discovery: { enabled: true, asLocalhost: false }`.  
- Atualize a seção importando seu perfil de conexão. O perfil de conexão do console está no formato JSON em vez de um arquivo YAML usado pela amostra.  

```
const userName = 'user1 ';

// Load connection profile; will be used to locate a gateway
const ccpPath = path.resolve(__dirname, '../gateway/connection.json');
const ccpJSON = fs.readFileSync(ccpPath, 'utf8');
const connectionProfile = JSON.parse(ccpJSON);

// Set connection options; identity and wallet let connectionOptions = {
  identity: userName,
  wallet: wallet,
  discovery: { enabled: true, asLocalhost: false }
};

await gateway.connect(connectionProfile, connectionOptions);
```
{:codeblock}

Esse fragmento de código usa o gateway para abrir conexões GRPC com os nós do peer e do solicitador e interagir com sua rede.

### Passo cinco: Invoque o contrato inteligente

Depois de configurar o gateway para se conectar à rede gerenciada por seu console, nós editaremos a parte do arquivo `issue.js` que se conecta ao contrato inteligente de papel comercial. Será necessário fornecer ao gateway o nome do contrato e o canal no qual você instanciou o contrato inteligente.

**Edite** a linha abaixo, substituindo `mychannel` pelo nome do canal.

```
const network = aguardar gateway.getNetwork ('mychannel');
```
{:codeblock}

Seguindo uma linha de código que imprime uma mensagem em seu console, é possível localizar uma linha que fornece ao gateway o nome do contrato inteligente. **Edite** a linha abaixo para mudar o nome `papercontract` para o nome do contrato que você instalou.

```
const contract = await network.getContract('papercontract-js', 'org.papernet.commercialpaper');
```
{:codeblock}

O gateway agora tem todas as informações que ele precisa para enviar uma transação. A linha a seguir chama a função `issue` no contrato de papel comercial, com os argumentos que definem o novo ativo de papel comercial.

```
const issueResponse = await contract.submitTransaction('issue', 'MagnetoCorp', '00001', '2020-05-31', '2020-11-30', '5000000');
```
{:codeblock}

Depois de enviar a transação usando o gateway, o arquivo `issue.js` desconecta a conexão de gateway.

```
gateway.disconnect ();
```
{:codeblock}

Esse comando fecha as conexões do GRPC abertas por seu gateway. O fechamento das conexões economizará recursos de rede e melhorará o desempenho.

Depois de concluir as edições desta etapa e da **Etapa quatro**, salve `issue.js` e feche-o. Envie a transação que cria o novo papel comercial usando o comando a seguir:

```
issue.js do nó
```
{:codeblock}

Se a transação for bem-sucedida, a saída a seguir será exibida em seu terminal:

```
Transação concluída.
Desconectar do gateway do Fabric.
Issue program complete.
```

### Etapa seis: operar a amostra como digibank

Após a criação do papel comercial operando como magnetocorp, é possível comprar e resgatar o papel comercial operando o tutorial como digibank. É possível usar o código do aplicativo digibank usando a mesma organização que magnetocorp ou usar a CA, os peers e o perfil de conexão de uma organização diferente. Se você concluiu o [tutorial Construir uma rede](/docs/services/blockchain/howto/ibp-console-build-network.html#ibp-console-build-network), essa é uma boa oportunidade de operar o tutorial como Org2.

Navegue para o diretório  ` digibank/application ` . É possível seguir as instruções fornecidas na **Etapa três** para criar e gerar os certificados e a carteira eletrônica que assinarão a transação como digibank. É possível, então, usar o arquivo `buy.js` para comprar o papel comercial de magnetocorp e, em seguida, usar `redeem.js` para resgatar o papel. É possível seguir a **Etapa quatro** e a **Etapa cinco** para editar esses arquivos para que eles apontem para o perfil de conexão, o canal e o contrato inteligente corretos.

## Conectando-se à sua rede usando APIs do SDK do Fabric de baixo nível
{: #ibp-console-app-low-level}

Se você estiver interessado em preservar o código do aplicativo existente ou usar os SDKs do Fabric para linguagens diferentes do Node.js, ainda será possível se conectar à sua rede usando as APIs do SDK do Fabric de nível inferior. Use o console para [fazer download de seu perfil de conexão](/docs/services/blockchain/howto/ibp-console-create-app.html#ibp-console-app-profile). Em seguida, é possível importar os terminais dos peers e os nós de pedido de seu canal diretamente do perfil de conexão ou usar as informações sobre terminais do nó para incluir manualmente objetos de peer e de solicitador. Você também precisará usar sua CA para [criar uma identidade do aplicativo](/docs/services/blockchain/howto/ibp-console-create-app.html#ibp-console-app-identities) e, em seguida, usar a inscrição de informações sobre terminais de CA no lado do cliente ou gerar certificados usando o console.

A documentação do [Fabric Node SDK](https://fabric-sdk-node.github.io){: external} fornece um tutorial sobre como [conectar-se à sua rede usando um perfil de conexão](https://fabric-sdk-node.github.io/tutorial-network-config.html){: external}. O tutorial usa as informações sobre terminais de CA em seu perfil de conexão para gerar chaves usando o SDK. Também é possível usar seu console para gerar um certificado de assinatura e uma chave privada e converter as chaves no formato PEM. Em seguida, é possível configurar um contexto do usuário passando suas chaves diretamente para a [classe de cliente do Fabric](https://fabric-sdk-node.github.io/Client.html){: external} dos SDKs usando o código abaixo:

```
fabric_client.createUser({
		username: 'admin',
		mspid:  'org1',
		cryptoContent: {
			privateKeyPEM: fs.readFileSync(path.join(__dirname,'./privateKey.pem')),
			signedCertPEM: fs.readFileSync(path.join(__dirname,'./certificate.pem'))
		}});
```
{:codeblock}

Se você estiver usando APIs do SDK de baixo nível para se conectar à sua rede, há etapas adicionais que podem ser tomadas para gerenciar o desempenho e a disponibilidade de seu aplicativo. Para obter mais informações, veja [Melhores práticas para conectividade do aplicativo e disponibilidade](/docs/services/blockchain/best_practices.html#best-practices-app-connectivity-availability).


## Usando índices com o CouchDB
{: #console-app-couchdb}

Se você usar o CouchDB como o banco de dados de estado, será possível executar consultas de dados JSON de seus contratos inteligentes com relação aos dados de estado do canal. É altamente recomendável que você crie índices para suas consultas JSON e use-os em seus contratos inteligentes. Os índices permitem que seus aplicativos recuperem dados de forma eficiente quando sua rede inclui blocos de transações e entradas adicionais no estado mundial. Para saber como usar índices com seus contratos inteligentes e seus aplicativos, veja [Melhores práticas ao usar o CouchDB](/docs/services/blockchain/best_practices.html#best-practices-app-couchdb-indices).
