---

copyright:
  years: 2019
lastupdated: "2019-05-31"

keywords: key features, build, operate, grow, architecture, multizone clusters

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

# Informazioni su {{site.data.keyword.blockchainfull_notm}} Platform for {{site.data.keyword.cloud_notm}}
{: #ibp-console-overview}

{{site.data.keyword.blockchainfull}} Platform for {{site.data.keyword.cloud_notm}} è la prossima generazione delle offerte di {{site.data.keyword.blockchainfull_notm}} Platform, che ti offre il totale controllo sulle distribuzioni, sui certificati e sulle chiavi private. Include la nuova console {{site.data.keyword.blockchainfull_notm}}, un'interfaccia utente che può semplificare e accelerare il processo di distribuzione dei componenti in un servizio {{site.data.keyword.cloud_notm}} Kubernetes controllato e gestito da te. Per ulteriori informazioni su Kubernetes e sul servizio {{site.data.keyword.cloud_notm}} Kubernetes, vedi [Kubernetes](/docs/services/blockchain/reference/k8s.html).
{:shortdesc}

{{site.data.keyword.blockchainfull_notm}} Platform for {{site.data.keyword.cloud_notm}} si basa su Hyperledger Fabric 1.4.1. Per ulteriori informazioni sulle nuove funzioni di Hyperledger Fabric 1.4.1, vedi [What's new in 1.4](https://hyperledger-fabric.readthedocs.io/en/release-1.4/whatsnew.html){: external}.

## Cosa offre la nuova release
{: #ibp-console-overview-capabilities}

Questa release più recente è personalizzata per gli utenti di {{site.data.keyword.blockchainfull_notm}} e Hyperledger Fabric esperti e consente loro di ospitare reti o creare nuove organizzazioni che possono unirsi ad altre reti {{site.data.keyword.blockchainfull_notm}}. Se sei un cliente del piano Starter o del piano Enterprise esistente, invece di lasciare che {{site.data.keyword.IBM_notm}} gestisca la tua rete, hai ora il totale controllo, con la capacità di eseguire il provisioning, il monitoraggio e la gestione dei tuoi componenti all'interno del tuo cluster Kubernetes.

Questa release {{site.data.keyword.blockchainfull_notm}} Platform include le seguenti funzioni chiave:

**COMPILAZIONE ---- Esperienza di sviluppatore integrata**
- **Codifica facilmente** i tuoi smart contract in Node.js, Golang o Java, scrivi le applicazioni client utilizzando la nuova estensione {{site.data.keyword.blockchainfull_notm}} VS Code, avvaliti dell'**integrazione SDK** con la console e impara dalle nostre esercitazioni e dai nostri esempi molto esaurienti.
- **DevOps semplificato** ti consente di passare dallo sviluppo alla verifica e alla produzione aumentando le tue risorse Kubernetes per aggiungere ulteriori componenti.
- **Funzioni chiave di Fabric aggiornate**. Avvaliti delle funzioni più recenti di Hyperledger Fabric v1.4.1:
  -  [Servizio di ordine Raft](https://hyperledger-fabric.readthedocs.io/en/release-1.4/orderer/ordering_service.html#raft){: external}
  - **Integrazione del servizio {{site.data.keyword.cloud_notm}}.** Avvaliti dei servizi {{site.data.keyword.cloud_notm}} integrati, come il dashboard del servizio {{site.data.keyword.cloud_notm}} Kubernetes, l'analisi log {{site.data.keyword.IBM_notm}} con LogDNA e {{site.data.keyword.cloud_notm}} IAM (Identity and Access Management).
  - [Raccolte di **dati privati**](/docs/services/blockchain/howto/ibp-console-smart-contracts.html#ibp-console-smart-contracts-private-data) che forniscono una maggiore riservatezza dei dati garantendo che i dati del libro mastro siano condivisi solo con i peer autorizzati tramite il protocollo gossip.
  - Il [rilevamento dei servizi](https://hyperledger-fabric.readthedocs.io/en/release-1.4/discovery-overview.html){: external}, che ti consente di rilevare e aggiornare in modo dinamico il modo in cui la tua applicazione interagisce con la tua rete.
  - Gli [Access Control List di canale](https://hyperledger-fabric.readthedocs.io/en/release-1.4/access_control.html){: external}, che ti consentono un controllo aggiuntivo sulla governance dei tuoi canali e smart contract.

**UTILIZZO --- Controllo totale delle tue distribuzioni**
- **Distribuisci solo i componenti di cui hai bisogno**. Connetti un peer a più canali e reti oppure ospita un servizio di ordine a cui possono connettersi i business partner.
- **Mantieni un controllo completo delle tue identità**. Memorizza e gestisci le chiavi utilizzate per amministrare i tuoi nodi senza memorizzare le tue chiavi private in {{site.data.keyword.cloud_notm}}.
- **Gestione centralizzata**. La console {{site.data.keyword.blockchainfull_notm}} Platform ti consente di distribuire e gestire tutte le tue organizzazioni e tutti i tuoi nodi in **una singola console centrale** senza dover fare affidamento su {{site.data.keyword.IBM_notm}} o altri fornitori per gestire i tuoi ordinanti o la tua Certificate Authority. Puoi anche aggiungere o rimuovere membri da un consorzio blockchain, creare e unirti a canali e installare e istanziare smart contract dalla tua console.
- **Ospita o unisciti a una rete**. Distribuisci i peer ospitati nel tuo cluster a più canali su più cloud oppure invita altre organizzazioni a unirsi al tuo consorzio o ai tuoi canali mentre le organizzazioni gestiscono i loro nodi in modo indipendente nelle infrastrutture.
- **Gestisci l'accesso** degli utenti che possono amministrare o monitorare i tuoi nodi.
- **Accesso diretto ai log** dei tuoi nodi dal servizio {{site.data.keyword.IBM_notm}} Kubernetes. Utilizza il servizio di analisi log {{site.data.keyword.cloud_notm}} oppure un servizio di terze parti per estrarre e analizzare i tuoi log.
- **Interagisci direttamente con i tuoi pod** utilizzando il dashboard Kubernetes. Esegui il comando exec nei tuoi pod e nei tuoi contenitori per immettere comandi e aggiornare certificati dalla riga di comando.
- **Raccolta della firma dinamica** che permette un migliore controllo sulla governance collaborativa sulle configurazioni del canale.

**CRESCITA --- Scalabilità e flessibilità**
- **Scegli la tua capacità di calcolo**. Hai la flessibilità di decidere la quantità di CPU, memoria e archiviazione di cui desideri eseguire il provisioning nel tuo cluster Kubernetes. Per ulteriori informazioni, vedi [In che modo il servizio {{site.data.keyword.cloud_notm}} Kubernetes interagisce con la console](/docs/services/blockchain/howto/ibp-console-govern.html#ibp-console-govern-iks-console-interaction).
- **Ridimensiona** ampliando e riducendo le risorse nel tuo cluster Kubernetes, pagando solo per quello di cui hai bisogno. Per ulteriori informazioni, vedi [Prezzi](/docs/services/blockchain/howto/pricing.html#ibp-pricing).
- **Ripristino di emergenza e alta disponibilità multiregione.** Questa opzione duplica la tua distribuzione Kubernetes tra le regioni, abilitando l'alta disponibilità (HA, High Availability) dei tuoi componenti e il ripristino di emergenza (DR, Disaster Recovery).
- **Esegui ovunque** (istruzioni presto disponibili). Grazie alla **base di codice unificata** della console {{site.data.keyword.blockchainfull_notm}} Platform, è possibile eseguire i tuoi componenti su {{site.data.keyword.cloud_notm}}, {{site.data.keyword.cloud_notm}} Private e cloud pubblici di terze parti.

Consulta questo [blog](https://www.ibm.com/blogs/blockchain/2019/02/taking-the-next-step-towards-deploying-blockchain-anywhere){: external} per compiere il passo successivo verso la distribuzione di blockchain per scopi di business ovunque.

Questa offerta è pensata per gli utenti Fabric esperti che vogliono creare e gestire le loro reti.

## Considerazioni
{: #ibp-console-overview-considerations}

Prima di distribuire la console, assicurati di aver compreso le seguenti considerazioni:

- Poiché la disponibilità della versione di prova beta e della release generalmente disponibile (GA) di {{site.data.keyword.blockchainfull_notm}} Platform si sovrapporranno, è importante assicurarti di conoscere quale versione di {{site.data.keyword.blockchainfull_notm}} Platform stai utilizzando. Le nuove funzioni e correzioni non saranno trasmesse alla beta, ma saranno disponibili nella versione GA di {{site.data.keyword.blockchainfull_notm}} Platform. Di conseguenza, se stai utilizzando la versione beta di {{site.data.keyword.blockchainfull_notm}} Platform, è probabile che alcuni pannelli nella tua console non corrisponderanno alla documentazione corrente, che viene mantenuta aggiornata con l'istanza del servizio generalmente disponibile. Per avvalerti dei vantaggi di tutte le ultime funzionalità, ti incoraggiamo ad eseguire il provisioning a una nuova istanza del servizio GA. Per scoprire come farlo, vedi [Introduzione a {{site.data.keyword.blockchainfull_notm}} Platform for {{site.data.keyword.cloud_notm}}](/docs/services/blockchain/howto/ibp-v2-deploy-iks.html#ibp-v2-deploy-iks).
- Tutti i peer distribuiti con questa release utilizzano CouchDB come loro database dello stato.
- Sei responsabile della gestione del monitoraggio dell'integrità, della sicurezza e della registrazione del tuo cluster Kubernetes. Vedi queste [informazioni](https://cloud.ibm.com/docs/containers/cs_responsibilities.html#your-responsibilities-by-using-ibm-cloud-kubernetes-service){: external} per i dettagli su quanto gestito da {{site.data.keyword.cloud_notm}} e su quanto è una tua responsabilità.
- Sei anche responsabile del monitoraggio dell'utilizzo delle risorse del tuo cluster Kubernetes. Per monitorare le tue risorse Kubernetes, consigliamo di utilizzare lo strumento [{{site.data.keyword.cloud_notm}} SysDig](https://www.ibm.com/cloud/sysdig){: external} in combinazione con il tuo dashboard {{site.data.keyword.cloud_notm}} Kubernetes. Se devi aumentare la capacità di archiviazione o le prestazioni del tuo cluster, vedi queste informazioni su come [modificare il tuo volume esistente](https://cloud.ibm.com/docs/containers/cs_storage_file.html#change_storage_configuration){: external}.
- Sei responsabile della gestione e della protezione dei tuoi certificati e delle tue chiavi private. {{site.data.keyword.IBM_notm}} non archivia i tuoi certificati nel cluster Kubernetes o nella console. Sono conservati solo nell'archiviazione locale del tuo browser. Se passi a un altro browser, dovrai importare le tue identità create in tale browser.
- {{site.data.keyword.blockchainfull_notm}} Platform è disponibile in regioni selezionate. Fai riferimento a questo argomento sulle [Ubicazioni {{site.data.keyword.blockchainfull_notm}} Platform](/docs/services/blockchain/howto?topic=blockchain-ibp-regions-locations) per un elenco aggiornato.
- Kubernetes deve essere alla versione 1.11 o a una versione stabile successiva nel tuo cluster {{site.data.keyword.cloud_notm}} Kubernetes. Utilizza queste istruzioni per [eseguire un upgrade dei tuoi cluster nuovi ed esistenti](/docs/services/blockchain/howto/ibp-v2-deploy-iks.html#ibp-v2-deploy-iks-updating-kubernetes) a questa versione.
- Se non desideri utilizzare l'archiviazione file Bronze predefinita che è preselezionata per tuo conto quando esegui il provisioning di un cluster Kubernetes in {{site.data.keyword.cloud_notm}}, puoi eseguire il provisioning di archiviazione a tua scelta. Per ulteriori informazioni, vedi questo argomento sulle [Considerazioni sull'archiviazione persistente](/docs/services/blockchain?topic=blockchain-ibp-v2-deploy-iks#ibp-console-storage).
- Se decidi di includere il supporto multizona {{site.data.keyword.cloud_notm}} nel tuo cluster Kubernetes, devi eseguire il provisioning della tua archiviazione. Per ulteriori dettagli, vedi [Utilizzo dei cluster multizona (MZR) con {{site.data.keyword.blockchainfull_notm}} Platform](/docs/services/blockchain?topic=blockchain-ibp-v2-deploy-iks#ibp-console-mzr).
- Puoi visualizzare un'anteprima di {{site.data.keyword.blockchainfull_notm}} Platform gratuitamente per 30 giorni quando colleghi la tua istanza del servizio {{site.data.keyword.blockchainfull_notm}} Platform a un cluster gratuito {{site.data.keyword.cloud_notm}} Kubernetes.  Le prestazioni saranno limitate da velocità effettiva, archiviazione e funzionalità. {{site.data.keyword.cloud_notm}} eliminerà il tuo cluster dopo 30 giorni e non puoi migrare i nodi o i dati da un cluster gratuito a uno a pagamento. Mentre la versione di prova beta di {{site.data.keyword.blockchainfull_notm}} Platform è gratuita, se scegli un cluster Kubernetes a pagamento invece di un cluster gratuito limitato, ci saranno degli addebiti per il servizio Kubernetes sul tuo account {{site.data.keyword.cloud_notm}}.

## Migrazione
{: #ibp-console-overview-migration}

Al momento, la migrazione da una qualsiasi offerta della piattaforma {{site.data.keyword.blockchainfull_notm}} a {{site.data.keyword.blockchainfull_notm}} Platform for {{site.data.keyword.cloud_notm}} non è possibile.

Tutte le istanze del servizio della versione di prova beta di {{site.data.keyword.blockchainfull_notm}} Platform non possono essere migrate alla release generalmente disponibile (GA).

## Licenza e determinazione dei prezzi
{: #ibp-console-overview-license-and-pricing}

{{site.data.keyword.blockchainfull_notm}} Platform for {{site.data.keyword.cloud_notm}} introduce un nuovo modello di prezzi orario basato sull'utilizzo del VPC (virtual processor core). Il modello semplificato si basa sulla quantità di CPU (o VPC) che i tuoi nodi {{site.data.keyword.blockchainfull_notm}} Platform utilizzano su base oraria, a una tariffa forfettaria di **$0,29 USD/VPC-ora**, dove **1 VPC = 1 CPU**. Per ulteriori dettagli, vedi questo argomento sui [Prezzi](/docs/services/blockchain?topic=blockchain-ibp-console-overview).

## Introduzione
{: #ibp-console-overview-deploy}

Per informazioni su come distribuire {{site.data.keyword.blockchainfull_notm}} Platform for {{site.data.keyword.cloud_notm}}, vedi [Introduzione a {{site.data.keyword.blockchainfull_notm}} Platform for {{site.data.keyword.cloud_notm}}](/docs/services/blockchain/howto/ibp-v2-deploy-iks.html#ibp-v2-deploy-iks).

Per ulteriori informazioni su come utilizzare la console per iniziare a distribuire nodi e creare un consorzio, vedi l'esercitazione relativa alla [creazione della tua rete](/docs/services/blockchain/howto/ibp-console-build-network.html#ibp-console-build-network). Questa esercitazione ti guida nel processo di utilizzo della console per creare una rete di esempio con tre organizzazioni, un'organizzazione di ordine, due organizzazioni peer e un canale con due peer uniti a esso. Puoi utilizzare questa rete di esempio per demo o modelli di verifica (Proof of Concept) o regolare ed espandere i passi nell'esercitazione per creare una tua configurazione blockchain.

## Riferimento per l'architettura
{: #ibp-console-overview-architecture}

La seguente illustrazione mostra i componenti della tua rete blockchain e come interagiscono.
![Struttura di rete di esempio](../images/IBP_V2_Architecture.svg "Archtecture reference")

Nota in che modo viene creata una singola istanza della console, conosciuta anche come Operational Tooling, per ciascuna istanza del servizio {{site.data.keyword.blockchainfull_notm}} Platform. Quando un nodo CA, ordinante o peer viene distribuito utilizzando la console, ne viene eseguita la distribuzione nell'**Istanza del servizio cluster Kubernetes**.

| **Cluster Kubernetes di {{site.data.keyword.blockchainfull_notm}} Platform** | **Descrizione** |
| ------------------------- |-----------|
| Operational Tooling | Noto anche come `console`, si tratta della tua interfaccia utente centrale per gestire tutti i componenti della tua blockchain. Con questa console, poi ora creare nodi ordinante, peer e CA, creare canali e installare e istanziare smart contract sviluppati con l'estensione VS Code di Hyperledger Fabric v1.4. La console viene distribuita in un cluster appartenente a {{site.data.keyword.IBM_notm}}. Non c'è alcun addebito per questa strumentazione o per il cluster Kubernetes quando viene eseguito.|


| **Istanza del servizio cluster Kubernetes ** | **Descrizione** |
| ------------------------- |-----------|-----------|-----------|
| **Tiller** | Parte della [strumentazione Helm](https://docs.helm.sh/glossary/#tiller){: external}, il Tiller viene eseguito all'interno del cluster Kubernetes per gestire l'installazione dei tuoi grafici Helm di ordinanti, CA e peer. |
| **Ingress** | Un [oggetto Kubernetes](https://kubernetes.io/docs/concepts/services-networking/ingress/){: external} che consente l'accesso alle risorse cluster dall'esterno del cluster. |
| **Proxy** | Il proxy {{site.data.keyword.blockchainfull_notm}} Platform è responsabile per l'instradamento del traffico ai nodi peer, CA e ordinante corretti utilizzando l'instradamento di intestazione host. |
| **Peer, CA e ordinanti** | Sono i nodi creati dalla distribuzione dei grafici Helm sottostanti. Nota: questi nodi possono anche essere importati da altre istanze del servizio cluster Kubernetes. Poiché le chiavi non vengono mai memorizzate da {{site.data.keyword.IBM_notm}}, ogni nodo peer e ordinante include un proxy web gRPC che consente alla console di comunicare con ciascun nodo utilizzando le chiavi nel portafoglio della console. |
| **RBAC** | Acronimo di Role based access control, ossia del controllo dell'accesso basato sui ruoli.  {{site.data.keyword.blockchainfull_notm}} Platform configura l'[RBAC Kubernetes](https://kubernetes.io/docs/reference/access-authn-authz/rbac/){: external} nel cluster che è richiesto per gestire i componenti blockchain nel cluster.

## Richiesta di assistenza tecnica
{: #ibp-console-overview-support}

Per ulteriori informazioni su come ottenere supporto su {{site.data.keyword.blockchainfull_notm}} Platform for {{site.data.keyword.cloud_notm}}, e per risorse per sviluppatori di blockchain gratuite e forum di supporto che puoi utilizzare per risolvere i problemi, vedi [Richiesta di assistenza tecnica](/docs/services/blockchain/ibmblockchain_support.html#blockchain-support).

Il supporto per la versione di prova beta di {{site.data.keyword.blockchainfull_notm}} Platform è limitato al periodo di durata della beta che termina il 3 agosto 2019.
