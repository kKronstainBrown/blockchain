---

copyright:
  years: 2017, 2019
lastupdated: "2019-03-05"

keywords: Hyperledger Fabric, confidential channels, Membership Service Provider, Linux Foundation, SDKs, modular architecture, permissioned network

subcollection: blockchain

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}


# Hyperledger Fabric
{: #hyperledger-fabric}

La rete {{site.data.keyword.blockchainfull}} è sviluppata sullo stack Hyperledger Fabric, uno dei progetti blockchain nell'ambito del progetto Hyperledger della Linux Foundation. Si tratta di una rete "con autorizzazioni" in cui tutti gli utenti e i componenti hanno delle identità note. Una logica di firma/verifica è implementata a ogni punto di contatto delle comunicazioni e le transazioni sono consentite tramite una serie di controlli di approvazione e di convalida. In tale senso, è molto diversa dalle implementazioni blockchain tradizionali che promuovono l'anonimato e sono costrette a fare affidamento sulle criptovalute e su pesanti obblighi di elaborazione per convalidare le transazioni.
{:shortdesc}

Hyperledger Fabric offre un'architettura modulare per estendere la scalabilità e le prestazioni. Questo argomento introduce alcuni componenti chiave in Hyperledger Fabric. Per un'introduzione completa relativa a Hyperledger Fabric, vedi la [documentazione di Hyperledger Fabric](https://hyperledger-fabric.readthedocs.io/en/release-1.4/){: external}.

## Peer
{: #hyperledger-fabric-peer}

A un livello fisico, una rete blockchain è formata principalmente da nodi peer (o semplicemente peer). I peer sono gli elementi fondamentali della rete perché ospitano i libri mastro e gli smart contract (che sono contenuti in ["chaincode"](https://hyperledger-fabric.readthedocs.io/en/release-1.4/developapps/chaincodenamespace.html){: external}. Più precisamente, i peer ospitano le **istanze** del libro mastro e le **istanze** degli smart contract. Poiché gli smart contract e i libri mastri vengono utilizzati, rispettivamente, per incapsulare i processi condivisi e le informazioni condivise in una rete, questi aspetti di un peer li rendono un buon punto di partenza per comprendere cosa faccia realmente una rete Fabric.

Per maggiori informazioni specifiche sui peer, vedi [questo documento che si concentra solo sui peer](https://hyperledger-fabric.readthedocs.io/en/release-1.4/peers/peers.html){: external} dalla documentazione della community Fabric.

## CA (Certificate Authority - Autorità di certificazione)
{: #hyperledger-fabric-certificate-authority}

Come piattaforma per le reti blockchain **con autorizzazioni**, Hyperledger Fabric include un componente Autorità di certificazione (CA, **Certificate Authority)** per gestire le identità di rete di tutte le organizzazioni membro e dei loro utenti. Il requisito di un'identità con autorizzazioni per ogni utente consente un controllo basato su ACL sull'attività di rete e garantisce che ogni transazione sia alla fine tracciabile a un utente registrato.
* La CA emette un certificato root (**rootCert**) per ciascun **membro** (organizzazione o individuo) che è autorizzato ad aderire alla rete.
* La CA emette anche un certificato di iscrizione (**eCert**) per ciascun componente membro, per le applicazioni lato server e, di tanto in tanto, per gli utenti.
* A ogni utente registrato viene anche concessa un'allocazione di certificati di transazione (**tCerts**). Ogni **tCert** autorizza una singola transazione di rete.

Questo controllo basato sul certificato sull'adesione alla rete e sulle azioni consente ai membri di limitare l'accesso a canali, applicazioni e dati privati e confidenziali, in base a specifiche identità utente.

Per ulteriori informazioni sul componente Certificate Authority di Hyperledger Fabric, vedi il manuale [Fabric CA User’s Guide](https://hyperledger-fabric-ca.readthedocs.io/en/release-1.4/){: external}.

## Membership Service Provider
{: #hyperledger-fabric-membership-service-provider}

Hyperledger Fabric include un componente **MSP (Membership Service Provider)** per offrire un'astrazione di tutti i protocolli e i meccanismi crittografici dietro all'emissione e alla convalida di certificati e autenticazione utente. L'MSP è installato su ciascun peer del canale per garantire che le richieste di transazione emesse al peer abbiano origine da un'identità utente autenticata e autorizzata.

Per ulteriori informazioni sul componente MSP (Membership Services Provider) di Hyperledger Fabric, vedi l'argomento relativo all'[adesione](https://hyperledger-fabric.readthedocs.io/en/release-1.4/membership/membership.html){: external} nella [documentazione di Hyperledger Fabric](https://hyperledger-fabric.readthedocs.io/en/release-1.4/){: external}.

## Servizio di ordine
{: #hyperledger-fabric-ordering-service}

In altre blockchain distribuite, come Ethereum e Bitcoin, non esiste un'autorità centrale che ordini le transazioni e le invii ai peer. Hyperledger Fabric, la blockchain su cui si basa {{site.data.keyword.blockchainfull_notm}} Platform, funziona in modo diverso. Dispone di un nodo chiamato **ordinante**.

Gli ordinanti sono componenti chiave di una rete perché svolgono alcune funzioni essenziali:

- Essi, letteralmente, **ordinano** i blocchi di transazioni che vengono inviati ai peer per essere scritti nei loro libri mastro e questo processo è detto "ordinazione". Se queste transazioni fossero state invece raccolte e ordinate presso i peer stessi, sarebbe aumentata la possibilità di un peer che scrive una transazione nel suo libro mastro laddove un altro peer non l'ha fatto, creando quindi una biforcazione dello stato.
- Mantengono il **canale del sistema ordinante**, il posto in cui risiede il **consorzio**, l'elenco di organizzazioni peer a cui è consentito creare canali.
- Eseguono degli importanti controlli di convalida dell'identità. Ad esempio, se un'organizzazione prova a creare un canale quando non è un membro del consorzio dell'ordinante, la richiesta verrà rifiutata. Gli ordinanti eseguono anche una convalida rispetto alle modalità di funzionamento nei canali delle transazioni, come ad esempio le autorizzazioni per modificare una configurazione del canale.

Hyperledger Fabric attualmente supporta entrambe le implementazioni del servizio di ordine basato su Kafka e SOLO (un singolo nodo di ordine). Per ulteriori informazioni sul servizio di ordine Hyperledger Fabric, vedi [Bringing up a Kafka-based Ordering Service](https://hyperledger-fabric.readthedocs.io/en/release-1.4/kafka.html){: external} nella [documentazione di Hyperledger Fabric](https://hyperledger-fabric.readthedocs.io/en/release-1.4/){: external}.

## Gli SDK Fabric
{: #hyperledger-fabric-fabric-sdks}

Gli SDK Hyperledger Fabric consentono agli sviluppatori di applicazioni di creare applicazioni che interagiscono con una rete blockchain. Questi SDK facilitano la gestione del ciclo di vita di canali e chaincode alle applicazioni.

Hyperledger Fabric offre sia un SDK Node.js che un SDK Java e fornisce le seguenti funzioni per interagire con la rete blockchain:

* Registrare e iscrivere utenti
* Creare canali
* Unire i peer a un canale
* Aggiornare la configurazione del canale sistemi o del canale applicazioni
* Installare il chaincode sui peer
* Istanziare il chaincode su un canale
* Eseguire l'upgrade del chaincode su un canale
* Richiamare le funzioni chaincode per aggiornare il libro mastro
* Eseguire query del libro mastro per transazioni, blocchi o chiavi specifici
* Monitorare gli eventi su un canale (ad esempio, la corretta esecuzione del commit di una transazione)

Per ulteriori informazioni sugli SDK Fabric, vedi [Hyperledger Fabric SDKs](https://hyperledger-fabric.readthedocs.io/en/release-1.4/fabric-sdks.html){: external} nella [documentazione di Hyperledger Fabric](https://hyperledger-fabric.readthedocs.io/en/release-1.4/){: external}.

## Flusso di transazioni
{: #hyperledger-fabric-transaction-flow}

Per garantire la congruenza e l'integrità dei dati, Hyperledger Fabric implementa molteplici punti di controllo lungo il flusso delle transazioni, compresi l'autenticazione client, l'approvazione, gli ordini e l'esecuzione del commit nel libro mastro.

La **Figura 1** raffigura il flusso di transazioni su una rete blockchain di Hyperledger Fabric:
![Flusso di transazioni](../images/v10_txflow.svg "Flusso di transazioni su una rete Hyperledger Fabric")

Su una rete Hyperledger Fabric, il flusso di dati per le query e le transazioni è iniziato da un'applicazione lato client inoltrando una richiesta di transazione a un peer su un canale. Il flusso di dati iniziale attraverso la rete è comune sia alle query che alle transazioni:

1. Utilizzando le API disponibili nell'SDK, un'applicazione client firma e inoltra una proposta di transazione agli appropriati peer di approvazione sul canale specificato. Questa proposta di transazione iniziale è una **richiesta** di approvazione.
2. Ciascun peer sul canale verifica l'identità e l'autorizzazione del client che ha eseguito l'inoltro e (se valide) esegue il chaincode specificato sugli input forniti. In base ai risultati della transazione e alla politica di approvazione per il chaincode richiamato, ciascun peer restituisce una risposta affermativa (YES) o negativa (NO firmata all'applicazione. Ogni risposta affermativa (YES) firmata è un'**approvazione** della transazione.

	A questo punto nel flusso delle transazioni, il processo diverge per le query e le transazioni. Se la proposta ha richiamato una funzione query nel chaincode, l'applicazione restituisce i dati al client. Se la proposta ha richiamato una funzione nel chaincode per aggiornare il libro mastro, l'applicazione continua con i seguenti passi:
3. L'applicazione inoltra la transazione, che include l'insieme di lettura/scrittura e le approvazioni, al **servizio di ordine**.
4. La transazione viene quindi inoltrata al servizio di ordine. Tutti i peer del canale convalidano ciascuna transazione nel blocco applicando la politica di convalida specifica del chaincode ed eseguendo un Concurrency Control Version Check.
	* Le transazioni che non superano il processo di convalida sono contrassegnate come non valide nel blocco e il blocco viene accodato al libro mastro del canale.
	* Tutte le transazioni valide aggiornano il database dello stato in base alle coppie di chiave/valore modificate.

Il **protocollo di diffusione dei dati gossip** trasmette in modo continuo dati del libro mastro sul canale per garantire dei libri mastri sincronizzati tra i peer. Per ulteriori informazioni, vedi [Gossip data dissemination protocol](https://hyperledger-fabric.readthedocs.io/en/release-1.4/gossip.html){: external} nella [documentazione di Hyperledger Fabric](https://hyperledger-fabric.readthedocs.io/en/release-1.4/){: external}.

Per un'introduzione dettagliata relativa al flusso di transazioni, vedi [Transaction Flow](https://hyperledger-fabric.readthedocs.io/en/release-1.4/txflow.html){: external} nella [documentazione di Hyperledger Fabric](https://hyperledger-fabric.readthedocs.io/en/release-1.4/){: external}.
