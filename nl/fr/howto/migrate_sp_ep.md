---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-31"

keywords: Starter Plan network, Starter Plan, Enterprise Plan network, Enterprise Plan, migration

subcollection: blockchain

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Migration d'un plan Starter vers un plan Enterprise
{: #migrate_starter_to_enterprise}

Le [plan Starter](/docs/services/blockchain/starter_plan.html#starter-plan-about) d'{{site.data.keyword.blockchainfull}} Platform offre un environnement de test et de développement pour l'exécution de vos concepts, de vos démos, et les essais de votre code blockchain et de vos applications. Lorsque vous êtes prêt à passer à un environnement de production, vous pouvez migrer d'un réseau de plan Starter vers un réseau de [plan Enterprise](/docs/services/blockchain/enterprise_plan.html#enterprise-plan-about).
{:shortdesc}

Les réseaux de plan Enterprise offrent les fonctionnalités prêtes pour la production suivantes pour le support de charge de travail :

- Réseaux de blockchain disponibles sur davantage de sites internationaux supplémentaires que les réseaux de plan Starter.
- Aucune limite de stockage, qui est de type 20 Go pour le plan Starter.
- Gestion UC et RAM améliorée pour garantir que tous les réseaux fonctionnent sans problème.
- Sécurité améliorée avec les fonctions suivantes :
  - SSC (Secure Service Container) garantit que l'image de blockchain ne peut pas être altérée et chargée à un moment donné et le code et les données de dispositif sont protégées en termes de confidentialité à la volée et au repos.
  - [HSM (Hardware secure module)](/docs/services/blockchain/glossary.html#glossary-hsm) pour la gestion et le stockage des clés.
  - Chiffrement de disque répandu.
- Haute disponibilité, Reprise après incident, Tolérance aux pannes et Mises à jour en continu.
- Support avancée en option.

## Remarques
{: #migrate_starter_to_enterprise_considerations}

Avant de migrer depuis votre réseau de plan Starter vers un réseau de plan Enterprise, vous devez lire les remarques suivantes.

- **Tarification :** Les frais mensuels de votre organisation pour l'utilisation d'un réseau de plan Enterprise inclut des frais d'appartenance de 1000 $ par instance et des frais d'homologue de 1000 $ par homologue. Pour plus d'informations, voir [A propos du plan Enterprise](/docs/services/blockchain/howto/pricing.html#ibp-pricing-enterprise-plan).
- **Version d'Hyperledger Fabric :** Les réseaux de plan Enterprise s'exécutent sur Hyperledger Fabric v1.1. Les réseaux Starter Plan s'exécutent dans la version 1.2 de Fabric.
- **Ressources affectées :** Code blockchain (contrats intelligents), applications client. Tenez compte également du fait que votre code blockchain optimise composant en version 1.2 de Fabric ou une fonctionnalité qui n'est pas compatible avec les réseaux en version 1.1.
- **Temps nécessaire :** Une demi-journée est au moins nécessaire pour migrer un réseau de base d'un plan Starter vers un plan Enterprise.
- **Données de registre existant** : Elles ne peuvent pas être déplacées de réseaux de plan Starter vers des réseaux de plan Enterprise car il n'est pas approprié que des données de test existent dans un environnement de production.
- **Hyperledger Composer:** {{site.data.keyword.IBM_notm}} n'assure pas de support pour les réseaux utilisant Hyperledger Composer en production, y compris l'interface CLI Composer, les API JavaScript, le serveur REST et l'aire de jeu Web.

**Remarque :** Un réseau *de base* comporte deux organisations avec deux homologues, un seul canal et un seul code blockchain ou fichier. Le temps réel nécessaire à la migration peut varier selon la taille et la complexité des composants réseau dont vous avez besoin dans le réseau de plan Enterprise.

## Liste de contrôle de migration
{: #migrate_starter_to_enterprise_checklist}

Un certain nombre de tâches sont nécessaires à la préparation du déplacement vers un réseau de plan Enterprise à partir d'un réseau Starter. Vous pouvez trouver des instructions détaillées dans les sections suivantes, mais voici un récapitulatif :

- Créer un réseau de plan Enterprise.
- Recréez la configuration souhaitée des organisations et des homologues à partir de votre réseau de plan Starter.
- Identifiez le code blockchain, écrit en Go ou Node, qui s'exécutera dans le réseau de plan Enterprise.
- Mettez à jour les applications client avec de nouvelles informations de noeud final d'API pour le réseau de plan Enterprise.

### Création d'un réseau de plan Enterprise
{: #migrate_starter_to_enterprise_create_network}

Vous devez créer un réseau de plan avant de migrer. Pour plus d'informations, voir [Création d'un réseau de plan Enterprise](/docs/services/blockchain/get_start.html#getting-started-with-enterprise-plan-create-network).

### Recréation d'une configuration de réseau
{: #migrate_starter_to_enterprise_config_network}

Vous pourriez recréer la configuration des organisations (membres), des canaux et des homologues du réseau de votre plan Starter dans votre réseau de plan Enterprise. Vous pouvez utiliser l'interface utilisateur du Moniteur réseau pour recréer ces ressources réseau en invitant les organisations appropriées (notez que vous ne pourrez pas **basculer** entre les organisations comme dans le plan Starter), créer des canaux et créer des homologues (encore une fois, les organisations invitées devront créer leurs propres homologues).

1. Connectez-vous au réseau de votre plan Enterprise sur {{site.data.keyword.cloud_notm}} et accédez au Moniteur réseau.
2. Recréez des organisations (membres) à l'écran "Membres", recréez des canaux à l'écran "Canaux", puis recréez des homologues à l'écran "Présentation". Pour plus d'informations sur la création de ressources réseau, voir [Utilisation du Moniteur réseau](/docs/services/blockchain/v10_dashboard.html#ibp-dashboard-overview).
3. Configurez des canaux en ajoutant des membres et en définissant des règles de canal de la même manière que dans votre réseau de plan Starter.

**Remarque **: Pour atteindre une haute disponibilité, vous devez créer au moins deux homologues pour votre organisation, les joindre au même canal et aux applications client de code de manière appropriée pour basculer d'un homologue à l'autre lorsque nécessaire.

### Migration du code blockchain
{: #migrate_starter_to_enterprise_cc}

Le code blockchain est développé en externe dans votre environnement local et il est appelé par vos applications client. Pour installer et instancier du code blockchain, qui a été testé dans votre réseau de plan Starter, sur certains homologues de votre réseau de plan Enterprise, suivez les instructions de la section [Installation, instanciation et mise à jour d'un code blockchain](/docs/services/blockchain/howto/install_instantiate_chaincode.html#install-instantiate-chaincode-install-cc).

### Mise à jour des applications client
{: #migrate_starter_to_enterprise_app}

Vous devez mettre à jour les applications client existantes qui sont testées sur le réseau de plan Starter, avec de nouvelles informations de noeud final d'API pour le réseau de plan Enterprise. Pour plus de détails, voir [Extraction des données d'identification réseau et du profil de connexion](/docs/services/blockchain/get_start.html#getting-started-with-enterprise-plan-retrieve-credentials).

Concernant la haute disponibilité, il est de la responsabilité des applications client de détecter lorsqu'un homologue ne répond pas et achemine les transactions vers un homologue différent.

## Que faire avec des réseau de plan Starter existants
{: #migrate_starter_to_enterprise_existing_network}

Vous pouvez continuer à utiliser votre réseau de plan Starter existant en tant qu'environnement de bac à sable pour l'incubation de nouveaux projets et le test des modifications apportées à du code blockchain existant. Vous pouvez aussi gérer les données de registre de test dans votre réseau de plan Starter, qui ne sont pas migrées vers le réseau de plan Enterprise.

Ne supprimez pas votre réseau Starter tant que vous n'avez pas terminé tous les tests et vérifié que tout fonctionne correctement. Toutefois, une fois que vous n'avez plus besoin de votre réseau Starter et de ses données de registre, vous pouvez supprimer le réseau en toute sécurité. Pour plus d'informations, voir [Suppression ou sortie d'un réseau](/docs/services/blockchain/get_start_starter_plan.html#getting-started-with-starter-plan-delete-network).
