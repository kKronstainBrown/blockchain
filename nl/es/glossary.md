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

# Glosario
{: #glossary}

En este tema se definen términos específicos de {{site.data.keyword.blockchainfull}} Platform que aparecen en esta documentación. Para estudiar los términos con más detalle y ver un glosario de términos relacionados con los conceptos de Hyperledger Fabric, consulte el [Glosario de Hyperledger Fabric](https://hyperledger-fabric.readthedocs.io/en/release-1.4/glossary.html){: external}.
{:shortdesc}

## Activo
{: #glossary-asset}
Bienes, servicios o propiedades tangibles o intangibles que se representan como un elemento con el que se comercia en la red blockchain.

## Bloque
{: #glossary-block}
Conjunto ordenado de transacciones, que está vinculado criptográficamente al bloque anterior en un canal.

## CA
{: #glossary-CA}
Abreviatura de "entidad emisora de certificados"; es el componente que emite certificados a todos los miembros participantes. Estos certificados representan la identidad de un miembro. Todas las entidades de la red (iguales, clasificadores, clientes, etc.) deben tener una identidad para comunicarse, autenticarse y, finalmente, realizar transacciones. Estas identidades son necesarias para cualquier participación directa en la red blockchain.

## Cadena
{: #glossary-chain}
La cadena del libro mayor es un registro de transacciones estructurado como bloques de transacciones relacionadas con hash. Los iguales reciben bloques de transacciones del servicio de ordenación, marcan las transacciones del bloque como válidas o no válidas en función de las políticas de aprobación y de las infracciones de simultaneidad y añaden el bloque a la cadena hash en el sistema de archivos del igual.

## Código de encadenamiento
{: #glossary-chaincode}
También conocido como **contratos inteligentes**, el código de encadenamiento son fragmentos de software que contienen un conjunto de funciones para consultar o actualizar el libro mayor.

## Canal
{: #glossary-channel}
Consiste en una subred de miembros de la red que desean realizar transacciones en privado. Los canales proporcionan aislamiento de datos y confidencialidad permitiendo que los miembros de un canal establezcan normas específicas y un libro mayor separado, al que solo pueden acceder los miembros del canal. Los iguales, que son los nodos que funcionan como puntos finales de transacción para las organizaciones, se unen a los canales.

## Cliente
{: #glossary-client}
El cliente representa la entidad que actúa en nombre de un usuario. Debe conectarse a un igual para comunicarse con blockchain. El cliente puede conectarse al igual que desee. Los clientes crean, y por lo tanto invocan, transacciones. El cliente envía una invocación de transacción real a los aprobadores y difunde las propuestas de transacciones al servicio de ordenación.

## Perfil de conexión
{: #glossary-connection-profile}
El archivo de conexión se puede ver en la pantalla "Visión general" del supervisor de red cuando se pulsa el botón **Perfil de conexión**. La información está disponible en formato JSON y contiene la información de punto final de API y los ID de inscripción/secretos de los recursos de la red, es decir, iguales, clasificadores y CA. La aplicación interactúa con los recursos de red a través de estos puntos finales de API.

## Consenso
{: #glossary-consensus}
Proceso de colaboración para mantener las transacciones del libro mayor sincronizadas en la red. El consenso garantiza que los libros mayores se actualizan solo cuando los participantes adecuados apruebas las transacciones y que los libros mayores se actualizan con las mismas transacciones en el mismo orden. Existen muchas maneras algorítmicas diferentes para alcanzar un consenso.

## Consola
{: #glossary-console}
El nombre de la interfaz de usuario de {{site.data.keyword.blockchainfull_notm}} Platform. La consola permite que los usuarios puedan ver, crear y gestionar sus despliegues. Debido a que las claves pública y privada solo se almacenan localmente en el navegador en el que se ejecuta la consola, el usuario mantiene un control total sobre sus claves.

## Consorcio
{: #glossary-consortium}
El grupo de organizaciones que no son de clasificador y que aparecen en el canal del sistema del clasificador. Estas son las únicas organizaciones que pueden crear canales. En el momento de la creación del canal, todas las organizaciones que se añaden al canal deben formar parte del consorcio. No obstante, es posible añadir una organización que no esté definida en un consorcio a un canal existente. Aunque una red blockchain puede tener varios consorcios, la mayoría de las redes blockchain tienen un único consorcio.

## CouchDB
{: #glossary-couchdb}
Un almacén de documentos que permite consultas de datos optimizadas que se utiliza para la base de datos de estado en las redes de
{{site.data.keyword.blockchainfull_notm}} Platform y del Plan inicial. CouchDB es también una opción para las redes del Plan empresarial, junto con LevelDB.

## Estado actual
{: #glossary-current-state}
El estado actual del libro mayor representa los valores más recientes para todas las claves alguna vez incluidas en su registro de transacciones de encadenamiento. Dado que el estado actual representa todos los valores de claves más recientes conocidos en el canal, a veces se refiere al mismo como **escenario mundial**. Los contratos inteligentes ejecutan propuestas de transacción en los datos de estado actuales. El estado actual cambia cada vez que el valor de una clave cambia o que se añade una nueva clave, y es fundamental para un flujo de transacciones porque el valor clave-valor más reciente debe ser conocido para poder cambiarse. Los iguales confirman los valores más recientes en el estado actual del libro mayor para cada transacción válida de un bloque. El estado actual se almacena en la base de datos de estado asociada con un igual.

## Pertenencia dinámica
{: #glossary-dynamic-memership}
Un usuario con el privilegio de **registrador** puede añadir de forma dinámica un miembro a la red. A los miembros también se les asignan roles y atributos, que controlan su acceso y autoridad en la red. Sin embargo, ni los roles ni los atributos se pueden asignar de forma dinámica. Hyperledger Fabric permite añadir o eliminar miembros, iguales y nodos de servicio de ordenación sin poner en peligro las operaciones de la red general. La pertenencia dinámica resulta crítica cuando se tienen que añadir o eliminar ajustes de relaciones empresariales y entidades por diversos motivos.

## Aprobación
{: #glossary-endorsement}
Proceso por el que se validan las transacciones del código de encadenamiento. Las reglas de aprobación se implementan mediante la especificación de políticas de aprobación.

## Política de aprobación
{: #glossary-endorsement-policy}
Define los nodos iguales de un canal que deben ejecutar las transacciones que están conectadas a una aplicación específica de código de encadenamiento y la combinación de respuestas necesaria (aprobaciones). Una política podría requerir que una transacción sea aprobada por un número mínimo de iguales de aprobación, por un porcentaje mínimo de iguales de aprobación o por todos los iguales de aprobación asignados a una determinada aplicación de código de encadenamiento. Las políticas se pueden definir en función de la aplicación y del nivel deseado de resiliencia frente a un comportamiento inadecuado, ya sea deliberado o no, por parte de los iguales de aprobación. Una transacción enviada debe satisfacer la política de aprobación para que los iguales de confirmación la marquen como válida. También se necesita una política de aprobación distinta para instalar y crear instancias de transacciones.

## Bloque de origen
{: #glossary-genesis-block}
El bloque de configuración que inicializa una red blockchain o canal, y que también sirve como primer bloque en una cadena.

## Gossip
{: #glossary-gossip}
Hyperledger Fabric permite a los iguales recopilar información de red importante entre sí sin tener que depender del servicio de ordenación. El [protocolo de diseminación de datos de rumores (gossip)](https://hyperledger-fabric.readthedocs.io/en/release-1.4/gossip.html){: external} ofrece una forma segura, fiable y escalable de intercambiar mensajes entre sí. Por ejemplo, si los iguales pierden algunos bloques debido a retrasos, cortes de red u otras razones, pueden sincronizarse con el estado del libro mayor actual utilizando la mensajería de rumores para ponerse en contacto con otros iguales que están en posesión de estos bloques que faltan.

## HSM
{: #glossary-hsm}
Módulo de seguridad de hardware (Hardware Security Module). Proporciona funciones de cifrado bajo demanda, gestión de claves y almacenamiento de claves como un servicio gestionado. HSM es un dispositivo físico que maneja las tareas que consumen muchos recursos del proceso de cifrado y que reduce la latencia para las aplicaciones. Para obtener más información, consulte [Módulo de seguridad de hardware](https://www.ibm.com/cloud/hardware-security-module){: external}.

## Hyperledger Fabric
{: #glossary-hyperledger-fabric}
[Hyperledger Fabric](https://hyperledger-fabric.readthedocs.io/en/release-1.4/){: external} es una infraestructura de blockchain empresarial que aloja Linux Foundation para que actúe como base para desarrollar aplicaciones blockchain o soluciones con una arquitectura modular. Los componentes de Hyperledger Fabric, como los servicios de consenso y de pertenencia, son de tipo conectar y listo.

## Instalar
{: #glossary-install}
Proceso de colocar un código de encadenamiento en el sistema de archivos en un igual. Debe instalar el código de encadenamiento en cada igual que vaya a ejecutar dicho código de encadenamiento.

## Crear instancia
{: #glossary-instantiate}
Proceso de iniciar e inicializar un contenedor de código de encadenamiento en un canal específico. Una vez se ha instalado el código de encadenamiento en los iguales y cada igual se ha unido al canal, se debe crear una instancia del código de encadenamiento en el canal. La creación de una instancia realiza la inicialización necesaria del código de encadenamiento, lo que incluye definir los pares de clave y valor que forman el estado inicial de un código de encadenamiento. Después de crear la instancia, los iguales que tienen el código de encadenamiento instalado pueden aceptar invocaciones de código de encadenamiento.

## Kafka
{: #glossary-kafka}
Implementación de plug-in de consenso para Hyperledger Fabric que da lugar a un clúster de nodos de servicio de ordenación en la red blockchain. Las implementaciones de Kafka y las implementaciones de Raft están pensadas para redes de producción. No obstante, solo hay soporte nativo para clústeres de servicios de ordenación de Raft y se pueden crear utilizando {{site.data.keyword.blockchainfull_notm}} Platform.

## Libro mayor
{: #glossary-ledger}
Consta de una "cadena de bloques" literal que almacena el registro de transacciones inmutable y secuencial, así como una base de datos de estado que permite mantener el estado actual. Hay un libro mayor por canal y las actualizaciones en el mismo se gestionan mediante el proceso de consenso según las políticas de cada canal.

## LevelDB
{: #glossary-leveldb}
Un almacén de valor de claves que es una opción para la base de datos de estado para redes del Plan empresarial, junto con CouchDB. LevelDB almacena el estado actual como pares de clave-valor, y no admite el uso de índices ni de consultas enriquecidas.

## Miembro
{: #glossary-member}
También conocidos como "organizaciones", los miembros de una red blockchain, de forma similar a los miembros de cualquier grupo, forman la estructura de la red. Un miembro puede ser tan grande como una empresa multinacional o tan pequeño como un individuo. Los miembros se inscriben en la red con un certificado que les otorga permisos para utilizar la red como un proveedor de servicios (por ejemplo, para emitir certificados o validar y ordenar transacciones) o como un consumidor. El primero proporciona servicios básicos de blockchain que incluyen validación de transacciones, ordenación de transacciones y servicios de gestión de certificados. Los miembros consumidores utilizan la red para invocar transacciones sobre el libro mayor distribuido. Los miembros pueden tener varios iguales.

## MSP
{: #glossary-msp}
Abreviatura de **Proveedor de servicios de pertenencia**, que proporciona la definición de una organización, incluyendo el certificado raíz de la CA que emite certificados para las entradas asociadas con dicha organización, así como el signcert del administrador de la organización. Los MSP también existen en el nivel local de un nodo de igual o de ordenación, y constituyen el mecanismo de autenticación que verifica los usuarios administradores del nodo. En
{{site.data.keyword.blockchainfull_notm}} Platform, se pueden exportar los MSP de una consola a otra, permitiendo que los usuarios puedan crear una organización en una consola, importarla en otra consola y trabajar con ella (por ejemplo, para crear un canal). También se pueden importar MSP en un servicio de ordenación, formando un "consorcio", la lista de organizaciones que tienen permitido crear canales y unirse a ellos.

## Red
{: #glossary-network}
Instancia de un servicio de {{site.data.keyword.blockchainfull_notm}} Platform en {{site.data.keyword.cloud_notm}}.

## Credenciales de red
{: #glossary-network-credentials}
Visibles desde la pantalla "API" del supervisor de red. Las credenciales incluyen su "clave" (nombre de usuario) y "secreto" (contraseña) en la IU de Swagger. Debe utilizar estas credenciales de red para autenticarse antes de ejecutar las API REST.

## Supervisor de red
{: #glossary-network-monitor}
Panel de control de GUI que proporciona {{site.data.keyword.blockchainfull_notm}} Platform para las redes del Plan inicial o el Plan empresarial para ver y gestionar la red blockchain.

## Nodo
{: #glossary-node}
Entidad de comunicación de blockchain. Hay tres tipos de nodos: CA, igual y clasificador.

## Clasificador
{: #glossary-orderer}
El nodo que recopila transacciones de los miembros de la red, ordena las transacciones y las empaqueta en bloques. A continuación, se distribuyen estos bloques a los iguales, que verificarán luego los bloques y los añadirán a los libros mayores de cada canal. Las clasificadores contienen el material de identidad de cifrado que está vinculado a cada miembro y autentican la identidad de clientes e iguales para que puedan acceder a la red. La función global que proporciona un nodo o una recopilación de nodos clasificadores se conoce como **servicio de ordenación**.

## Organización
{: #glossary-organization}
Consulte [Miembro](/docs/services/blockchain/glossary.html#glossary-member).

## Participante
{: #glossary-participant}
Cualquier organización, individuo, aplicación o dispositivo que interactúa con la red blockchain. Bajo el término participante se distinguen dos grupos: los miembros y los usuarios.

## Igual
{: #glossary-peer}
Recurso de la red blockchain que proporciona los servicios para ejecutar y validar transacciones y para mantener libros mayores. El igual ejecuta código de encadenamiento y es el titular del historial de transacciones y del estado actual de los activos en los canales de la red, es decir, del libro mayor. Los iguales son propiedad de las organizaciones, que los gestionan, y se unen a canales.

## Raft
{: #glossary-raft}
Raft es un servicio de ordenación con tolerancia a errores de bloqueo (CFT) basado en una implementación del
[protocolo Raft](https://raft.github.io/raft.pdf){: external} en `etcd`. Raft sigue un modelo de "líder y seguidor", donde se elige un nodo líder (por canal) y sus decisiones se reproducen en los seguidores. Los servicios de ordenación de Raft deberían ser más fáciles de configurar y gestionar que los servicios de ordenación basados en Kafka, y se puede crear un clúster de estos nodos utilizando {{site.data.keyword.blockchainfull_notm}} Platform.

## Credenciales de servicio
{: #glossary-service-credentials}
Las credenciales de servicio están en formato JSON y contienen la información de punto final de API y los ID de inscripción/secretos de los componentes de red, es decir, CA, clasificadores e iguales. La aplicación interactúa con los recursos de red a través de estos puntos finales de API.

## SDK
{: #glossary-sdk}
Hyperledger Fabric admite dos kits de desarrollo de software (SDK). Un SDK de nodo y un SDK Java.  El SDK de nodo se puede instalar mediante NPM y el SDK Java mediante Maven.  Los SDK tienen sus propios repositorios git, es decir, [SDK de nodo de Fabric](https://github.com/hyperledger/fabric-sdk-node){: external} y [SDK de Java de Fabric](https://github.com/hyperledger/fabric-sdk-java){: external}, con documentación sobre las API disponibles. Los SDK de cliente de Hyperledger Fabric permiten la interacción entre la aplicación cliente y la red blockchain.

## SignCert
{: #glossary-sign-cert}
El certificado que las entidades, ya sean organizaciones o administradores, adjuntan a sus propuestas o a sus respuestas a propuestas. Estos signCerts son exclusivos para una entidad y el servicio de ordenación los comprueba para asegurarse de que coinciden con el signCert del archivo para dicha entidad.

## Contratos inteligentes
{: #glossary-smart-contracts}
Véase [Código de encadenamiento](/docs/services/blockchain/glossary.html#glossary-chaincode).

## Solo
{: #glossary-solo}
Implementación de plug-in de consenso para Hyperledger Fabric que da lugar a un solo nodo de servicio de ordenación en la red blockchain. La red del Plan inicial utiliza la implementación Solo. La implementación Solo no está pensada para una red de producción. Las alternativas a Solo son los clústeres Raft y Kafka.

## Base de datos de estado
{: #glossary-state-database}
Los datos del estado Actual se almacenan en una base de datos de los iguales para lecturas y consultas eficientes del código de encadenamiento. Las redes del Plan inicial utilizan CouchDB como la base de datos de estado. Las redes del Plan empresarial pueden utilizar LevelDB o CouchDB.

## Transacción
{: #glossary-transaction}
Mecanismo que utilizan los participantes en la red blockchain para interactuar con los activos. Una transacción crea código de encadenamiento nuevo o invoca una operación sobre código de encadenamiento existente.

## Usuario
{: #glossary-user}
Un usuario es un participante en una red blockchain que tiene acceso indirecto al libro mayor a través de una relación de confianza con un miembro existente.

## Escenario mundial
{: #glossary-world-state}
Consulte [Estado actual](/docs/services/blockchain/glossary.html#glossary-current-state).
