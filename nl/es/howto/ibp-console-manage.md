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


# Administración de la consola
{: #ibp-console-manage-console}

Hay varias acciones que puede realizar para gestionar el comportamiento de la consola. En este tema se describen las acciones externas a las operaciones de nodo de blockchain que le ayudan en el uso cotidiano de la consola.
{:shortdesc}

**Audiencia de destino:** este tema está diseñado para los operadores de red responsables de crear, supervisar y gestionar la red blockchain.

## Adición y eliminación de usuarios de la consola
{: #ibp-console-manage-console-add-remove}

Cada usuario que acceda a la consola debe tener asignada una política de acceso con un rol de usuario de {{site.data.keyword.cloud}} Identity and Access Management (IAM) definido. La política determina qué acciones puede realizar el usuario dentro de la consola. La consola de {{site.data.keyword.blockchainfull_notm}} Platform se suministra con la dirección de correo electrónico del propietario de {{site.data.keyword.cloud_notm}} como administrador de la consola.  De forma predeterminada, se otorga a este usuario de {{site.data.keyword.cloud_notm}} el rol de **Gestor** para el servicio {{site.data.keyword.blockchainfull_notm}} Platform en IAM. A continuación, el administrador de la consola puede otorgar acceso a la consola a otros usuarios mediante la interfaz de usuario de IAM. Para obtener más información sobre IAM, consulte [Qué es IAM](/docs/iam?topic=iam-iamoverview#iamoverview){: external}.  

Cuando [utilice IAM para invitar usuarios](/docs/iam?topic=iam-iamuserinv#iamuserinv){: external}, tendrá que seguir los pasos siguientes para configurar sus roles y el acceso a la consola:
 1. En la barra de menús, pulse **Gestionar** > **Acceso (IAM)** y, a continuación, seleccione **Usuarios**.
 2. Pulse **Invitar usuario**.
 3. Escriba la dirección de correo electrónico del usuario o los usuarios.
 4. En la lista desplegable **Servicios**, seleccione **Blockchain Platform**.
 5. Desplácese hacia abajo hasta **Seleccionar roles**.
 6. En **Asignar roles de acceso al servicio**, elija un rol para el usuario, que puede ser **Gestor**, **Escritor** y **Lector**.
 7. Pulse **Invitar a usuarios**.

| Rol | Funciones |
|--------|----------|
| Gestor | Como Gestor, tiene permisos más allá del rol Escritor. Puede hacer todo lo que puede hacer un Lector y un Escritor, además de: <ul><li>Suministrar nuevos componentes utilizando la consola o las API.</li><li>Suprimir componentes suministrados utilizando la consola o las API.</li><li>Cambiar los niveles de registro de la consola utilizando la consola o las API.</li><li>Reiniciar la consola utilizando una API.</li></ul> |
| Escritor | Como Escritor, tiene permisos más allá del rol Lector, incluyendo: <ul><li>Importar componentes utilizando la consola o las API.</li><li>Eliminar componentes importados utilizando la consola o las API.</li><li>Registrar usuarios en una CA.</li><li> Añadir o eliminar notificaciones utilizando la consola o las API.</li></ul>  |
| Lector | Como lector, puede realizar acciones de solo lectura, incluyendo: <ul><li>Ver la interfaz de usuario de la consola.</li><li>Ver el registro de la consola.</li><li>Exportar componentes.</li><li>Emitir cualquier API GET.</li></ul> | |

 Los permisos son acumulativos. Si selecciona un rol **Gestor**, el usuario también podrá realizar todas las acciones de **Escritor** y de **Lector** sin que necesite marcar dichos roles de forma adicional.   Del mismo modo, un usuario con el rol `Escritor` podrá realizar todas las acciones del rol **Lector**. Para el acceso a la consola, solo necesita seleccionar un rol en **Roles de acceso al servicio**; no es necesario que seleccione nada en **Roles de acceso a la plataforma**. Marque el rol correspondiente en **Asignar rol de acceso a la plataforma** cuando sea importante que la instancia de servicio sea visible en el panel de control de {{site.data.keyword.cloud_notm}} del usuario invitado.

![Añadir usuarios](../images/AddICPUser.gif){: gif}


Tras añadir nuevos usuarios a la consola, es posible que los usuarios no puedan ver todos los nodos, canales o código de encadenamiento que despliegan otros usuarios. Para trabajar con estos componentes, cada usuario necesita importar las identidades asociadas en su propia cartera de consola. Para obtener más información, consulte [Almacenamiento de identidades en la cartera de la consola](/docs/services/blockchain/howto/ibp-console-identities.html#ibp-console-identities-wallet).
{:important}

Si necesita modificar el rol de un usuario:
 1. En la barra de menús, pulse **Gestionar** > **Acceso (IAM)** y, a continuación, seleccione **Usuarios**.
 2. Pulse el menú Acciones situado junto al usuario que desee modificar y seleccione **Asignar acceso**.
 3. Seleccione el mosaico **Asignar acceso a recursos**.
 4. En la lista desplegable **Servicios**, seleccione **Blockchain Platform 2.0**.
 5. Desplácese hacia abajo hasta **Seleccionar roles**.
 6. En **Asignar roles de acceso al servicio**, elija un rol para el usuario, que puede ser **Gestor**, **Escritor** y **Lector**.
 7. Pulse **Asignar**.

Cuando tenga que eliminar el acceso de un usuario a la consola, siga las instrucciones del [tema sobre eliminación de usuarios de IAM](/docs/iam?topic=iam-remove#remove){: external}.

### Asignación de roles de acceso a usuarios individuales o a grupos de usuarios en IAM
{: #ibp-console-manage-console-users-groups}

Cuando establezca políticas de {{site.data.keyword.cloud_notm}} IAM, puede asignar roles a un usuario individual o a un grupo de usuarios.

<dl>
<dt>Usuarios individuales</dt>
<dd>Es posible que un usuario específico necesite más o menos permisos que el resto de su equipo. Puede personalizar los permisos de forma individual de forma que cada persona tenga los permisos que necesita para realizar sus tareas. Puede asignar más de un rol de {{site.data.keyword.cloud_notm}} IAM a cada usuario.</dd>
<dt>Varios usuarios de un grupo de acceso</dt>
<dd>Puede crear un grupo de usuarios y luego asignar permisos a dicho grupo. Por ejemplo, puede agrupar a todos los jefes de equipo y asignar acceso de administrador al grupo. A continuación, puede agrupar todos los desarrolladores y asignar solo acceso de escritura a dicho grupo. Puede asignar más de un rol de {{site.data.keyword.cloud_notm}} IAM a cada grupo de acceso. Cuando asigne permisos a un grupo, cualquier usuario que se añada o se elimine de dicho grupo se verá afectado. Si añade un usuario al grupo, también recibe el acceso adicional. Si se elimina, su acceso se revoca.</dd>
</dl>

Los usuarios que añada en IAM son simplemente direcciones de correo electrónico de usuarios que pueden iniciar una sesión en la consola. No tienen ninguna relación con las **Organizaciones disponibles** en el separador Organizaciones ni con las identidades almacenadas por la cartera de la consola.
{:note}

## Actualización de la dirección de correo electrónico del administrador

Si utilizan la consola varias personas u organizaciones, se recomienda crear una dirección de correo electrónico funcional para acceder a la red. El uso de un correo electrónico funcional le permite acceder a la consola aunque el administrador original abandone la organización o si su dirección de correo electrónico queda suspendida. Solo se pueden utilizar una única dirección de correo electrónico como contacto del administrador.

Para actualizar la dirección de correo electrónico del administrador de la consola que se ha configurado al desplegar la consola, debe haber iniciado la sesión como administrador de la consola. Vaya al separador **Usuarios** y pulse **Configurar** en el mosaico **ID de {{site.data.keyword.IBM_notm}}**. En el panel que aparece, especifique una nueva dirección de correo electrónico para el administrador de la consola.

## Visualización de los registros
{: #ibp-console-manage-logs}

Cuando utilice la consola de {{site.data.keyword.blockchainfull_notm}} Platform, es posible que necesite ver los registros para depurar un problema.

### Visualización de los registros de la consola
{: #ibp-console-manage-console-logs}

Puede acceder fácilmente a los registros de la consola si tiene que depurar los problemas que encuentre al utilizar la consola o al trabajar con los nodos. También puede establecer el nivel de registro para aumentar o reducir la cantidad de registros que recopila la consola. Los registros de la consola se recopilan de forma independiente de los [registros de nodo](/docs/services/blockchain/howto/ibp-console-manage.html#ibp-console-manage-console-node-logs), que recopila el servicio {{site.data.keyword.cloud_notm}} Kubernetes.

Vaya al separador **Valores** en el navegador de la consola para cambiar los valores de registro. Los registros de la consola se recopilan de dos fuentes distintas:

  * **Registros de cliente:** estos registros se recopilan cuando se envían mandatos desde el navegador a la consola.
  * **Registros de servidor:** estos registros se recopilan cuando la consola envía mandatos a los nodos y desde el despliegue de la consola. Estos registros incluyen la salida de registro de Hyperledger Fabric.

Establezca la cantidad de registros recopilados utilizando la lista desplegable para cada tipo de registro. Por ejemplo, **Error** y **Aviso** recopilan la cantidad mínima de registros, mientras que **Depuración** y **Todos** recopilan la mayor cantidad.

Solo puede ver los registros de la consola si ha iniciado la sesión como administrador de la consola. Para ver los registros desde el separador **Valores**, sustituya la palabra `settings` en el URL del navegador por `api/v1/logs`. Por ejemplo, si el url de su consola es `localhost:3001/settings`, para ver los registros debe ir a `localhost:3001/api/v1/logs`. Los registros de cliente y de servidor se recopilan en archivos independientes. Los registros más recientes se encuentran en la parte superior de la página.

### Visualización de los registros de la consola
{: #ibp-console-manage-console-node-logs}

El servicio {{site.data.keyword.IBM_notm}} Kubernetes recopila los registros de sus iguales, clasificadores y entidades emisoras de certificados. Siga los pasos siguientes para ver los registros de los nodos desde el clúster en el que ha desplegado la red de {{site.data.keyword.blockchainfull_notm}} Platform.

Para localizar más fácilmente los registros de nodo, resulta útil filtrar por el espacio de nombres que se utilizó cuando se desplegaron los nodos.
Para localizar el espacio de nombres, abra cualquier nodo de CA en la consola y pulse el icono **Valores**. Visualice el valor del **URL de punto final de entidad emisora de certificados**. Por ejemplo: `https://n2734d0-paorg10524.ibpv2-cluster.us-south.containers.appdomain.cloud:7054`.

El espacio de nombres es la primera parte del URL que empieza por la letra `n` y va seguida de una serie aleatoria de seis caracteres alfanuméricos. En el ejemplo anterior, el valor del espacio de nombres es `n2734d0`.

1. Abra el [panel de control de {{site.data.keyword.cloud_notm}}](https://cloud.ibm.com/resources){: external} y vaya a la pantalla de visión general del clúster del servicio {{site.data.keyword.IBM_notm}} Kubernetes.
2. Sobre la pantalla de visión general del clúster, pulse **Panel de control de Kubernetes**.
3. En el panel de control de Kubernetes, utilice la lista desplegable **Espacio de nombres** de navegación de la izquierda para cambiar al espacio de nombres correspondiente a la instancia de servicio de {{site.data.keyword.blockchainfull_notm}} Platform que ha descubierto arriba.
4. En el panel de navegación izquierdo, pulse **Pods** para ver la lista de los pods de nodo que ha desplegado.
5. Pulse sobre un pod. Luego pulse **Registros** en el menú superior para abrir los registros del nodo. Sobre los registros, puede utilizar el menú desplegable que hay después de **Registros de** para ver los registros de los distintos contenedores del pod. Por ejemplo, el igual y la base de datos de estado (CouchDB, por ejemplo) se ejecutan en distintos contenedores y generan registros diferentes.

De forma predeterminada, los registros de los nodos se recopilan localmente dentro del clúster. También puede utilizar los servicios de {{site.data.keyword.cloud_notm}}
o un servicio de terceros para recopilar, almacenar y analizar los registros de la red. Para obtener más información, consulte [Registro y supervisión para el servicio Kubernetes de {{site.data.keyword.IBM_notm}}](https://cloud.ibm.com/docs/containers?topic=containers-health#health){: external}. Se recomienda utilizar el servicio [LogDNA de {{site.data.keyword.cloud_notm}}](https://cloud.ibm.com/docs/services/Log-Analysis-with-LogDNA?topic=LogDNA-kube#kube){: external}, que le permite analizar fácilmente los registros en tiempo real.

### Visualización de los registros de contenedor de contratos inteligentes
{: #ibp-console-manage-console-container-logs}

Si detecta problemas con el contrato inteligente, puede consultar los registros del contrato inteligente, o el código de encadenamiento, y del contenedor para depurar un problema:

- Abra el panel de control de Kubernetes, filtre por [espacio de nombres](#ibp-console-manage-console-node-logs) y pulse el pod igual en el que se ejecuta el contrato inteligente.
- Pulse el enlace `Registros` en el panel de control. De forma predeterminada, apunta a un contenedor igual.
- Vaya al contenedor `fluentd` seleccionándolo en la lista desplegable.  

Todos los registros de contrato inteligentes se pueden ver en esta ventana y se pueden descargar mediante el icono de descarga del panel.

## Instalación de parches para los nodos
{: #ibp-console-manage-patch}

Es posible que sea necesario actualizar con el tiempo las imágenes de docker subyacentes de {{site.data.keyword.IBM_notm}} Hyperledger Fabric para los nodos de igual, CA y clasificador, por ejemplo, con actualizaciones de seguridad o a un nuevo release puntual de Fabric. El texto **Parche disponible** sobre el mosaico de un nodo es el indicador de que hay un parche disponible y se puede instalar en el nodo siempre que esté preparado. Estos parches son opcionales, pero recomendables.  No puede aplicar parches a nodos que se han importado en la consola.

Los parches se aplican a los nodos de uno en uno. Mientras se aplica un parche, el nodo no estará disponible para procesar solicitudes ni transacciones. Por lo tanto, para evitar cualquier interrupción del servicio, siempre que sea posible debe asegurarse de que haya otro nodo del mismo tiempo disponible para procesar solicitudes. La instalación de parches en un nodo tarda alrededor de un minuto en completarse y, cuando la actualización haya finalizado, el nodo estará listo para procesar solicitudes.
{:note}

Para aplicar un parche a un nodo, abra el mosaico del nodo y pulse el botón **Instalar parche**.

## Caducidad del clúster de Kubernetes
{: #ibp-console-manage-console-cluster-expiration}

Si utiliza un clúster gratuito del servicio {{site.data.keyword.cloud_notm}} Kubernetes, caducará después de 30 días. Cuando esto ocurra, ya no podrá acceder a la consola. Todos los nodos y certificados asociados se suprimirán también. Solo puede tener un clúster gratuito al mismo tiempo. Por lo tanto, para poder crear otra instancia de servicio de blockchain, debe asegurarse de que se haya suprimido el clúster caducado y su instancia de servicio asociada de {{site.data.keyword.cloud_notm}}. Para confirmar que ya se han suprimido o para suprimir manualmente estos recursos, siga estos pasos:

1. En el panel de control de {{site.data.keyword.cloud_notm}}, pulse el menú de hamburguesa y abra la **Lista de recursos**.
2. Desplácese hasta el triángulo **Servicios** y amplíelo para ver la instancia de servicio.
3. Si la instancia aparece en la lista, pulse sobre el menú de acción para la instancia de servicio y luego pulse **Suprimir** para suprimir esta instancia de servicio.
4. Desplácese hasta el triángulo **Clústeres de Kubernetes** y amplíelo para ver el clúster gratuito.
5. Si aparece su clúster gratuito, pulse sobre el menú de acción y, a continuación, pulse **Suprimir** para suprimir el clúster gratuito.

Cuando se hayan completado estas acciones, puede seguir los [pasos originales](/docs/services/blockchain/howto/ibp-v2-deploy-iks.html#ibp-v2-deploy-iks) para crear un nuevo clúster de Kubernetes y una instancia de servicio de blockchain desde la página del catálogo de {{site.data.keyword.cloud_notm}}.
