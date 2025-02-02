---

copyright:
years: 2018, 2019
lastupdated: "2019-06-18"

keywords: IBM Blockchain Platform, IBM Cloud Private, system requirements, Kubernetes Helm chart, behind a firewall

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

# Acerca de {{site.data.keyword.blockchainfull_notm}} Platform for Multicloud
{: #console-icp-about}

{{site.data.keyword.blockchainfull}} Platform se puede desplegar en nubes públicas y privadas, como {{site.data.keyword.cloud_notm}}, su propio centro de datos y nubes públicas de terceros. Este despliegue multinube es posible a través de {{site.data.keyword.cloud_notm}} Private, la plataforma de organización de contenedores basada en Kubernetes de IBM. Este release proporciona una interfaz de usuario de consola que puede utilizar para desplegar y gestionar componentes de blockchain en un clúster de {{site.data.keyword.cloud_notm}} Private. {{site.data.keyword.blockchainfull}} Platform for {{site.data.keyword.cloud_notm}} Private utiliza la base de código de Hyperledger Fabric v1.4.1 y permite el despliegue en {{site.data.keyword.cloud_notm}} Private v3.2.
{:shortdesc}

Este release de {{site.data.keyword.blockchainfull_notm}} Platform incluye las siguientes características principales:

**CREAR ---- Experiencia integrada del desarrollador**
- **Codifique fácilmente** sus contratos inteligentes en Node.js, Golang o Java, escriba aplicaciones cliente con la nueva extensión de VS Code de {{site.data.keyword.blockchainfull_notm}}, aproveche la **integración de SDK** con la consola de la interfaz y aprenda con nuestras completas guías de aprendizaje y ejemplos.
- **DevOps simplificado** le permite pasar de la fase de desarrollo a la de prueba y producción en un solo entorno mediante la ampliación de los recursos de Kubernetes para añadir más componentes.
- **Integración del servicio Kubernetes.** Aproveche servicios como Grafana y Prometheus para el registro y Kibana para la supervisión.
- **Características principales de Fabric actualizadas**. Aproveche las características más recientes de Hyperledger Fabric v1.4.1:
  - [Servicio de ordenación Raft](https://hyperledger-fabric.readthedocs.io/en/release-1.4/orderer/ordering_service.html#raft){: external}
  - [Recopilaciones de datos privados](/docs/services/blockchain/howto/ibp-console-smart-contracts.html#ibp-console-smart-contracts-private-data) que mejoran la privacidad de los datos al garantizar que los datos del libro mayor solo se comparten entre iguales autorizados mediante el protocolo gossip.
  - [Service Discovery](https://hyperledger-fabric.readthedocs.io/en/release-1.4/discovery-overview.html){: external}, que le permite descubrir y actualizar de forma dinámica la forma en que la aplicación interactúa con la red.
  - [Listas de control de acceso de canal](https://hyperledger-fabric.readthedocs.io/en/release-1.4/access_control.html){: external}, que le ofrecen un control adicional sobre los canales y los contratos inteligentes.

**OPERAR --- Control total de los despliegues**
- **Despliegue solo los componentes que necesite**. Conecte un igual a varios canales y redes, o aloje un servicio de ordenación al que pueden conectarse los socios de la empresa.
- **Mantenga un control completo de sus identidades**. Almacene y gestione las claves que se utilizan para administrar los nodos en su propio entorno seguro.
- **Operaciones unificadas**. La consola de {{site.data.keyword.blockchainfull_notm}} Platform le permite desplegar y gestionar todas las organizaciones y nodos en **una consola** sin tener que depender de {{site.data.keyword.IBM_notm}} ni de otros proveedores para gestionar los clasificadores o la entidad emisora de certificados. También puede añadir o eliminar miembros de un consorcio de blockchain, crear y unir canales e instalar y crear instancias de contratos inteligentes desde la consola.
- **Aloje o únase a una red**. Despliegue iguales alojados en el clúster en varios canales en varias nubes, o invite a otras organizaciones a unirse a su consorcio o canales mientras las organizaciones gestionan sus nodos de forma independiente entre infraestructuras.
- **Gestione el acceso** de los usuarios que pueden administrar o supervisar los nodos.
- **Acceda directamente a los registros** de los nodos desde el servicio Kubernetes. Utilice cualquier servicio de terceros admitido para extraer y analizar los registros.
- **Interactúe directamente con los pods** mediante el servicio Kubernetes.
- **Recopilación de firmas dinámica**, que le permite un mejor control sobre la gestión de la colaboración a través de configuraciones de canal.

**CRECER --- Escalabilidad y flexibilidad**
- **Elija su capacidad de cálculo**. Tiene flexibilidad para decidir la cantidad de CPU, de memoria y de almacenamiento que desea suministrar en el clúster de Kubernetes. Para obtener más información, consulte [Cómo interactúa la consola con el clúster de Kubernetes](/docs/services/blockchain/howto/ibp-console-govern.html#ibp-console-govern-iks-console-interaction).
- **Escale** al alza o a la baja los recursos del clúster de Kubernetes y pague solo lo que necesite. Para obtener más información, consulte [Tarifas](/docs/services/blockchain/howto/pricing.html#ibp-pricing).
- **Recuperación tras desastre y alta disponibilidad multizona.** Esta prestación duplica el despliegue de Kubernetes entre zonas, ofreciendo alta disponibilidad (HA) de sus componentes y recuperación tras desastre (DR).
- **Ejecución en cualquier lugar**. Gracias al **código base unificado** de la consola de {{site.data.keyword.blockchainfull_notm}} Platform, es posible ejecutar los componentes en cualquier entorno al que dé soporte {{site.data.keyword.cloud_notm}} Private.

{{site.data.keyword.blockchainfull_notm}} Platform para {{site.data.keyword.cloud_notm}} Private es un producto empaquetado para {{site.data.keyword.cloud_notm}} Private y se suministra como un diagrama de Helm de Kubernetes. Para obtener más información acerca de {{site.data.keyword.cloud_notm}} Private, consulte la documentación de [{{site.data.keyword.cloud_notm}} Private versión 3.2.0](https://www.ibm.com/support/knowledgecenter/SSBS6K_3.2.0/kc_welcome_containers.html){: external}.

## Qué ofrece {{site.data.keyword.blockchainfull_notm}} Platform para {{site.data.keyword.cloud_notm}} Private

{{site.data.keyword.blockchainfull_notm}} Platform for {{site.data.keyword.cloud_notm}} Private le permite instalar la consola de {{site.data.keyword.blockchainfull_notm}} Platform en un despliegue de {{site.data.keyword.cloud_notm}} Private. Luego puede utilizar la consola para crear todos los componentes fundamentales de un blockchain de Fabric Manager Hyperledger, una entidad emisora de certificados, un servicio de ordenación e iguales, en el clúster local. Para obtener más información sobre los bloques de creación de las redes de Hyperledger Fabric, consulte [Visión general de componentes de Blockchain](/docs/services/blockchain/blockchain_component_overview.html#blockchain-component-overview). También puede utilizar la consola para trabajar con una red de varias nubes distribuidas mediante la importación de nodos desplegados en otros clústeres de {{site.data.keyword.cloud_notm}} Private o en {{site.data.keyword.cloud_notm}}.

## ¿Resulta {{site.data.keyword.blockchainfull_notm}} Platform para {{site.data.keyword.cloud_notm}} Private adecuada para usted?

La ejecución de {{site.data.keyword.blockchainfull_notm}} Platform fuera de {{site.data.keyword.cloud_notm}} le ofrece una mayor flexibilidad para crecer o unirse a una red blockchain. Resulta de ayuda para que los iniciadores de red hagan crecer sus redes al permitir la unión de nuevos miembros mientras utilizan la plataforma que han elegido. Permitirá que las organizaciones interesadas en unirse a redes blockchain coloquen sus iguales con sus aplicaciones existentes o los integren con sus sistemas de registro.

Los usuarios de esta oferta gestionarán su propia seguridad e infraestructura. {{site.data.keyword.cloud_notm}} no ofrece estos servicios. Revise las [Consideraciones y limitaciones](#console-icp-about-considerations) de la sección siguiente antes de comenzar.

## Consideraciones y limitaciones
{: #console-icp-about-considerations}

Antes de empezar, asegúrese de que comprende las limitaciones siguientes:

- El usuario es responsable de gestionar la supervisión del estado, la seguridad, el registro y el uso de recursos de los componentes de blockchain.
- La consola solo se puede utilizar para crear y controlar componentes basados en Hyperledger Fabric v1.4.1 o superior.
- Solo puede importar nodos que se hayan exportado de otras consolas de {{site.data.keyword.blockchainfull_notm}} Platform. Para poder utilizar un igual o un clasificador importado desde la consola, también debe importar la definición de MSP de la organización y la identidad de administrador de la organización del nodo asociado en la consola.

Para ver los entornos a los que da soporte {{site.data.keyword.cloud_notm}} Private, consulte [Entornos soportados](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_3.2.0/supported_environments/environments_overview.html){: external}.
{:important}

## Requisitos previos del sistema
{: #console-icp-about-prerequisites}

{{site.data.keyword.blockchainfull_notm}} Platform para {{site.data.keyword.cloud_notm}} Private admite los sistemas operativos siguientes:
- Red Hat Enterprise Linux (RHEL) 7.3, 7.4, 7.5
- Ubuntu 18.04 LTS y 16.04 LTS
- SUSE Linux Enterprise Server (SLES) 12 SP3

El diagrama de Helm de {{site.data.keyword.blockchainfull_notm}} Platform para {{site.data.keyword.cloud_notm}} Private se ha validado para su ejecución en clústeres de {{site.data.keyword.cloud_notm}} Private v3.2 en Ubuntu Linux utilizando los nodos trabajadores y el almacenamiento de reserva siguientes:

- **LinuxONE e {{site.data.keyword.IBM_notm}} Z**: z/VM y KVM, que utilizan NFS.
- **x86**: Linux de 64 bits que utiliza GlusterFS.

## Licencia
{: #console-icp-about-license}

Consulte [Precios de {{site.data.keyword.blockchainfull_notm}} Platform for Multicloud](/docs/services/blockchain?topic=blockchain-ibp-software-pricing) para obtener más información sobre licencias y precios.

## Instalación de {{site.data.keyword.blockchainfull_notm}} Platform para {{site.data.keyword.cloud_notm}} Private
{: #console-icp-about-install}

{{site.data.keyword.blockchainfull_notm}} Platform para {{site.data.keyword.cloud_notm}} Private se entrega como un archivo de diagrama de Helm que se puede instalar en un clúster de {{site.data.keyword.cloud_notm}} Private local. Después de instalar el diagrama de Helm, encontrará {{site.data.keyword.blockchainfull_notm}} Platform como una plataforma en el catálogo de {{site.data.keyword.cloud_notm}} Private. Para obtener instrucciones sobre cómo instalar el diagrama de Helm y los requisitos previos necesarios, consulte [Instalación de {{site.data.keyword.blockchainfull_notm}} Platform para {{site.data.keyword.cloud_notm}} Private](/docs/services/blockchain/howto/console-helm-install.html#helm-console-install).

Si es un usuario nuevo de {{site.data.keyword.cloud_notm}} Private y desea información y sugerencias sobre cómo instalar y desplegar {{site.data.keyword.cloud_notm}} Private, consulte [Configuración de {{site.data.keyword.cloud_notm}} Private](/docs/services/blockchain/ICP_console_setup.html#icp-console-setup).

Puede desplegar {{site.data.keyword.blockchainfull_notm}} Platform detrás de un cortafuegos, sin tener que acceder a Internet público. El paquete del diagrama de Helm descargado incluye todas las imágenes de Docker de los componentes de Fabric que utiliza la plataforma {{site.data.keyword.blockchainfull_notm}}, sin obtenerlos de DockerHub durante el despliegue.

## Consideraciones sobre seguridad
{: #console-icp-about-security}

Debido a que estos componentes se despliegan en su propia infraestructura, tendrá la responsabilidad de gestionar su seguridad. Esto incluye áreas importantes de seguridad, como la gestión de claves y el cifrado de datos. Examine los temas siguientes cuando tenga en cuenta la seguridad para los componentes.

### Seguridad de datos
{: #console-icp-about-security-data}

El plan Inicial y el plan Empresa de {{site.data.keyword.blockchainfull_notm}} Platform utilizan el cifrado de disco completo basado en el [cifrado de claves simétricas](https://www.ibm.com/support/knowledgecenter/en/SSB23S_1.1.0.14/gtps7/s7symm.html){: external} para proteger todos los datos que utilizan las redes. Debe seguir pasos similares en su propio entorno para proteger los datos de los iguales.

Los datos de la base de datos de estado, independientemente de si utiliza LevelDB o CouchDB, no se cifran. Puede utilizar un cifrado a nivel de aplicación para proteger los datos en reposo en la base de datos de estado.

### Residencia de datos
{: #console-icp-about-security-data-residency}

Los requisitos de residencia de datos pueden imponer que el proceso y el almacenamiento de todos los datos del libro mayor de blockchain permanezcan dentro de los límites de un solo país (o dentro de algún otro límite definido). Para obtener más información sobre cómo conseguir la residencia de datos, consulte [Residencia de los datos](#console-icp-about-data-residency).

### Gestión de claves
{: #console-icp-about-security-key-management}

La gestión de claves es un aspecto crítico de la seguridad. Si una clave privada se ve comprometida o se pierde, es posible que usuarios hostiles accedan a los datos y funciones. {{site.data.keyword.IBM_notm}} utiliza dispositivos físicos conocidos como [Módulos de seguridad de hardware](/docs/services/blockchain/glossary.html#glossary-hsm) (HSM) para almacenar las claves privadas de las redes del Plan empresarial de la plataforma {{site.data.keyword.blockchainfull_notm}}.

Cuando despliegue un componente en {{site.data.keyword.cloud_notm}} Private, usted es el responsable de gestionar las claves privadas. Aunque {{site.data.keyword.blockchainfull_notm}} Platform genera claves privadas, dichas claves no se almacenan en la plataforma. Es de vital importancia que almacene sus claves de forma segura para que no se vean comprometidas. Encontrará la clave privada del componente en la carpeta de almacén de claves de MSP del igual, en el directorio `/mnt/crypto/peer/peer/msp/keystore/` dentro del componente. Para obtener más información sobre los certificados que hay dentro de su igual, consulte la sección [Proveedor de servicios de pertenencia](/docs/services/blockchain/certificates.html#managing-certificates-msp) de la guía de aprendizaje sobre [Gestión de certificados en {{site.data.keyword.blockchainfull_notm}} Platform](/docs/services/blockchain/certificates.html#managing-certificates).

Puede utilizar Key Escrow para recuperar claves privadas perdidas. Esto hay que hacerlo antes de perder ninguna clave. Si una clave privada no se puede recuperar, tiene que obtener nuevas claves privadas registrando una nueva identidad con la entidad emisora de certificados. También debe eliminar y sustituir signCert de cualquier canal al que se haya unido.

### TLS
{: #console-icp-about-security-tls}

[Transport Layer Security](https://www.ibm.com/support/knowledgecenter/en/SSFKSJ_7.1.0/com.ibm.mq.doc/sy10660_.htm){: external} (TLS) está incorporada en el modelo de confianza de Hyperledger Fabric. Todos los componentes del Plan inicial o empresarial de {{site.data.keyword.blockchainfull_notm}} Platform utilizan TLS para autenticarse y comunicarse entre sí. Por lo tanto, los componentes de red de la plataforma deben ser capaces de completar un reconocimiento de TLS con sus iguales. Una implicación de este enfoque es que necesita activar el paso a través, usando por ejemplo una lista blanca, en el cortafuegos de las apps cliente a su igual.

### Configuración del proveedor de servicios de pertenencia
{: #console-icp-about-security-MSP}

Los componentes de {{site.data.keyword.blockchainfull_notm}} Platform consumen identidades a través de proveedores de servicios de pertenencia (MSP). Los MSP asocian los certificados que emiten las entidades emisoras de certificados con roles de red y de canal. Para obtener más información sobre cómo funcionan los MSP con el igual, consulte [Proveedores de servicios de pertenencia (MSP)](/docs/services/blockchain/certificates.html#managing-certificates-msp).

### Seguridad de las aplicaciones
{: #console-icp-about-security-appl}

Puesto que todas las invocaciones de código de encadenamiento están firmadas, Fabric gestiona la seguridad de las aplicaciones. Además, Fabric también incluye comprobaciones de nivel de aplicación basadas en ACL.

## Residencia de datos
{: #console-icp-about-data-residency}

Debido a que las redes blockchain no conocen qué tipo de datos se procesa, en ocasiones deben realizarse pasos adicionales para mantener seguros determinados tipos de datos. El requisito más común en cuanto a residencia de datos está asociado a las leyes de determinados países, según las cuales todos los datos que se procesan y almacenan en un sistema de TI deben permanecer dentro de las fronteras del país específico. Paralelamente, algunas empresas de sectores muy regulados, como las gubernamentales, de sanidad y de servicios financieros, obligan a que los datos se almacenen tras su cortafuegos. Por lo tanto, para conseguir la residencia de datos, todos los componentes de la red blockchain deben formar parte del mismo [canal](/docs/services/blockchain/glossary.html#glossary-channel) y deben residen dentro de las fronteras de un solo país.

Para hacer frente a los requisitos de residencia de datos, es importante comprender la arquitectura de Hyperledger Fabric subyacente a la plataforma {{site.data.keyword.blockchainfull_notm}}. La arquitectura se centra en torno a tres componentes clave: un servicio de ordenación (compuesto por clasificadores), entidades emisoras de certificados (CA) e iguales. Un igual recibe actualizaciones de estado ordenadas en forma de bloques desde el servicio de ordenación y mantiene el estado y el libro mayor. Por lo tanto, un igual y un servicio de ordenación tienen una relación directa. El libro mayor contiene los valores más recientes de todas las claves y los datos que incluyen los registros de transacciones.

Además, las aplicaciones cliente utilizan los [SDK de Fabric](https://hyperledger-fabric.readthedocs.io/en/release-1.4/getting_started.html){: external} para enviar transacciones a los iguales y al servicio de ordenación. Estas transacciones incluyen los datos del [conjunto de lectura y escritura](https://hyperledger-fabric.readthedocs.io/en/release-1.4/readwrite.html){: external}, que contiene los pares de clave-valor del libro mayor.

Si la residencia de datos en el país es un requisito, el clasificador, el igual y las aplicaciones cliente deben residir en el mismo país. Cuando se crea una red de {{site.data.keyword.blockchainfull_notm}} Platform en {{site.data.keyword.cloud_notm}}, tiene la opción de seleccionar la ubicación de la red. <!--For a Starter Plan network, you can select from US South, United Kingdom, and Sydney. For an Enterprise Plan network, you can select from currently available locations, which include Dallas, Frankfurt, London, Sao Paulo, Tokyo, and Toronto. -->Para obtener más información sobre regiones y ubicaciones, consulte el tema sobre [Regiones y ubicaciones de {{site.data.keyword.blockchainfull_notm}} Platform](/docs/services/blockchain/reference/ibp_regions.html#ibp-regions-locations).

### Un caso de uso para la residencia de datos

Tenga en cuenta una red de {{site.data.keyword.blockchainfull_notm}} Platform que incluye el clasificador y la entidad emisora de certificados junto con un consorcio de cuatro organizaciones. Las organizaciones tienen uno o más nodos de igual, las cuatro organizaciones forman parte de un único canal y todos los componentes de la red se encuentran en la región (por ejemplo, Frankfurt) donde se ha desplegado la red de la plataforma {{site.data.keyword.blockchainfull_notm}}. Por último, las aplicaciones cliente que interactúan con los iguales también residen en Alemania.

En este ejemplo, se mantiene la residencia de datos.

![Residencia de datos cuando todos los componentes se encuentran en el mismo país](images/remote_peer_data_res_1.png "Residencia de datos cuando todos los componentes se encuentran en el mismo país")

Ahora, tengamos en cuenta las implicaciones de que un **igual distribuido** se una a una de las organizaciones. Un igual distribuido puede residir en la misma región que el resto de la red o en cualquier lugar fuera de la región de la red de la plataforma
{{site.data.keyword.blockchainfull_notm}}:

-	Si el igual reside en el mismo país que el resto de la red, se mantiene la residencia de datos. Todos los datos del libro mayor permanecen dentro de Alemania, como indica la **Figura 1** anterior.
-	En caso de que el igual resida en un país distinto (como EE. UU. por ejemplo), ya no se mantiene la residencia de datos, pues los datos del libro mayor del igual se comparten fuera de la frontera del país.

Para resolver este problema, se pueden utilizar **canales** para aislar los datos en un subconjunto de iguales de la red. Cuando la red de {{site.data.keyword.blockchainfull_notm}} Platform contiene un igual distribuido y clasificadores entre fronteras, los canales proporcionan el aislamiento de los datos de libro mayor de organizaciones que tienen iguales fuera de la frontera del país.

**Nota:** las clasificadores siempre están ubicados en la región del centro de datos que haya seleccionado para alojar la red. No es posible tener varios clasificadores entre países. Sin embargo, los iguales pueden estar ubicados en el centro de datos o en una ubicación remota fuera de {{site.data.keyword.cloud_notm}}.

![Residencia de los datos cuando los iguales están fuera del país de la región de {{site.data.keyword.blockchainfull_notm}} Platform](images/remote_peer_data_res_2.png "Residencia de los datos cuando los iguales están fuera del país de la región de {{site.data.keyword.blockchainfull_notm}} Platform")

En la **Figura 2**, no se requiere residencia de datos para `OrgC` y `OrgD`. De hecho,
`OrgD` incluye ahora dos iguales distribuidos, `OrgD-peer1` y `OrgD-peer2`, que residen en *Estados Unidos*. Por lo tanto, para que `OrgA`, `OrgB` y sus respectivas aplicaciones cliente e iguales que residen en Alemania puedan aislar los datos de libro mayor en el canal `X`, se crea un nuevo canal `Y` para
`OrgC` y `OrgD`.

Para obtener más información sobre el flujo de datos de la red de {{site.data.keyword.blockchainfull_notm}} Platform, consulte la [documentación de Fabric sobre el flujo de transacciones](https://hyperledger-fabric.readthedocs.io/en/release-1.4/txflow.html){: external}.

En el futuro, la nueva tecnología de Hyperledger Fabric mejorará la posibilidad de obtener más datos residentes mediante el uso de [recopilaciones de datos privados](https://hyperledger-fabric.readthedocs.io/en/release-1.4/private-data/private-data.html){: external} y ZKF (zero knowledge proof).

- Una recopilación de datos privados garantiza que los datos privados se comparten entre igual e igual (mediante el protocolo gossip) solo con los iguales que tienen autorización para verlos, por ejemplo iguales que están dentro de las fronteras del país. Los datos se almacenan en una base de datos privada en el igual. El servicio de ordenación no está implicado y no ve los datos privados. Se escribe un hash de esos datos en los libros mayores de cada igual del canal. El hash que se utiliza para la validación de estado sirve como prueba de la transacción y se puede utilizar para fines de auditoría. Los datos privados están disponibles para las redes de {{site.data.keyword.blockchainfull_notm}} Platform que se ejecutan en la versión 1.2.1 o superior de Fabric. No obstante, la característica de datos privados no está disponible para los iguales que se ejecutan en {{site.data.keyword.cloud_notm}} Private, ya que las redes de {{site.data.keyword.cloud_notm}} Private no utilizan gossip (rumores) actualmente.

- Una ZKP (zero knowledge proof) permite que un "comprobador" asegure a un "verificador" que conoce un secreto sin tener que revelar el propio secreto.

Encontrará más información acerca de estas tecnologías en el documento técnico sobre [Transacciones privadas y confidenciales con Hyperledger Fabric](https://developer.ibm.com/tutorials/cl-blockchain-private-confidential-transactions-hyperledger-fabric-zero-knowledge-proof/){: external}.

## Obtención de soporte
{: #console-icp-about-support}

Para obtener más información sobre cómo obtener soporte en {{site.data.keyword.blockchainfull_notm}} Platform for {{site.data.keyword.cloud_notm}}, recursos gratuitos del desarrollador de blockchain y foros de soporte que puede utilizar para solucionar problemas, consulte [Obtención de soporte](/docs/services/blockchain/ibmblockchain_support.html#blockchain-support).

Si ha adquirido una licencia de {{site.data.keyword.blockchainfull_notm}} Platform for {{site.data.keyword.cloud_notm}} Private y desea ponerse en contacto con el servicio de atención al cliente, consulte la información sobre [acceso a la comunidad de soporte de {{site.data.keyword.IBM_notm}} y apertura de una incidencia de soporte](https://www-01.ibm.com/support/docview.wss?uid=ibm10740041){: external}.
