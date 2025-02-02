---

copyright:
  years: 2017, 2019
lastupdated: "2019-03-05"

keywords: IBM Blockchain offerings, Linux Foundation, Hyperledger Fabric, open source, community contribution

subcollection: blockchain

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}
{:note: .note}
{:important: .important}
{:tip: .tip}
{:external: target="_blank" .external}

# Clause de protection
{: #disclaimer}

**ATTENTION :** Vous devez prendre connaissance des informations suivantes avant d'utiliser des plans {{site.data.keyword.blockchainfull}}.

## Déclaration de prise en charge {{site.data.keyword.IBM_notm}}
{: #disclaimer-support-statement}

{{site.data.keyword.IBM_notm}} est depuis longtemps chef de file en matière d'innovation, et cela se poursuit avec les offres {{site.data.keyword.blockchainfull_notm}} Platform sur {{site.data.keyword.cloud_notm}}. La blockchain est une technologie qui connaît un essor rapide et qui devrait engendrer des perturbations dans le secteur financier, les chaînes d'approvisionnement locales et globales, ainsi que le soutien logistique dans un certain nombre d'espaces professionnels. Dans le cadre de programmes d'adoption précoces, les clients et partenaires commerciaux {{site.data.keyword.IBM_notm}} étudient la blockchain en tant que solution industrielle. {{site.data.keyword.blockchainfull_notm}} Platform for {{site.data.keyword.cloud_notm}} est l'un de ces programmes. **Comme pour toute nouvelle technologie, les utilisateurs d'{{site.data.keyword.blockchainfull_notm}} Platform for {{site.data.keyword.cloud_notm}} doivent se préparer à des changements rapides et essentiels**.
{:shortdesc}

L'architecture d'{{site.data.keyword.blockchainfull_notm}} repose sur le projet Hyperledger Fabric de Linux Foundation. Chaque contribution de communauté en code source ouvert améliore Hyperledger Fabric mais peut représenter un défi en termes d'adoption. **{{site.data.keyword.IBM_notm}} met en garde contre toute définition ou échange d'actifs financiers<!--, or any assets of value,-->, directement sur un réseau de blockchain Hyperledger Fabric**.

{{site.data.keyword.IBM_notm}} n'assure pas de support pour les réseaux utilisant Hyperledger Composer en production, y compris l'interface CLI Composer, les API JavaScript, le serveur REST et l'aire de jeu Web.{:note}

## Instruction en code source ouvert
{: #disclaimer-open-source-statement}

Les plans de l'offre {{site.data.keyword.blockchainfull_notm}} on {{site.data.keyword.cloud_notm}} reposent sur la pile Hyperledger Fabric de Linux Foundation. Les membres du projet Hyperledger, y compris {{site.data.keyword.IBM_notm}}, continuent à contribuer aux différents sous-projets sous l'égide de Hyperledger.  Toutes les contributions sont passées en revue, certifiées et testées par la communauté.

## Déclaration du support du code blockchain
{: #disclaimer-chaincode-support-statement}

Les pratiques de codage suivantes NE sont PAS prises en charge sur les réseaux {{site.data.keyword.blockchainfull_notm}} :

1. Utilisation de tableaux associatifs avec itération (l'ordre est aléatoire en Go).
2. Lecture d'une liste d'éléments d'une table KVS (l'ordre n'est pas garanti).
3. Ecriture de code blockchain dangereux (query et invoke peuvent être appelés en parallèle).
4. Substitution de mémoire globale ou de mémoire cache pour les variables d'état de registre dans le code blockchain.
5. Accès à des services externes, comme les bases de données, directement depuis le code blockchain.
6. Utilisation de bibliothèques ou de variables globales qui pourraient introduire du non déterminisme (utilisation de "random" ou "time", par exemple).

En outre, il n'est pas recommandé d'écrire du code blockchain non déterministe, car cela présente un risque pour la cohérence et l'intégrité des données. Il est à noter que l'architecture Hyperledger Fabric est conçue pour contrer le code blockchain non déterministe via une série de vérifications d'adhésion et de validation. Cependant, vous êtes quand même fortement encouragé à coder des fonctions déterministes qui ne reposent pas sur des variables globales non statiques (par exemple, le temps).
