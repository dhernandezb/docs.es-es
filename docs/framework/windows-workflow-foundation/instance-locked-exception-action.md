---
title: "Acci&#243;n de excepci&#243;n de instancia bloqueada | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 164a5419-315c-4987-ad72-54cbdb88d402
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# Acci&#243;n de excepci&#243;n de instancia bloqueada
La propiedad <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceLockedExceptionAction%2A> del almacén de instancias de flujo de trabajo de SQL le permite especificar qué acción debe realizar el proveedor de persistencia de SQL cuando recibe <xref:System.Runtime.DurableInstancing.InstanceLockedException>.El proveedor de persistencia recibe esta excepción cuando intenta bloquear una instancia de servicio del flujo de trabajo que ya está bloqueada actualmente por otro host del servicio.Los valores de esta propiedad son <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction>, <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction> y <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction>.El valor predeterminado es <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction>.En la lista siguiente se describen las tres opciones:  
  
-   <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction>.El host del servicio no intenta bloquear la instancia de servicio de flujo de trabajo y pasa <xref:System.Runtime.DurableInstancing.InstanceLockedException> al autor de llamada. Si el flujo de trabajo permanece en memoria durante un período que supera los 60 segundos, use <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction> como intento.El valor predeterminado es <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction>.  
  
-   <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction>.El host del servicio vuelve a intentar bloquear la instancia de servicio de flujo de trabajo con un intervalo lineal entre los reintentos y pasa <xref:System.Runtime.DurableInstancing.InstanceLockedException> al autor de llamada al final de la secuencia.Si el flujo de trabajo permanece en memoria aproximadamente entre 5 y 60 segundos, y llegan mensajes en lotes donde es más probable que los mensajes se envíen a la misma instancia del mismo host para procesar todos los mensajes antes de descargar el flujo de trabajo, use <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction> para lograr la mejor latencia sin desperdiciar recursos.  
  
-   <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction>.El host del servicio vuelve a intentar bloquear la instancia de servicio de flujo de trabajo con un intervalo de interrupción exponencial entre los reintentos y pasa la excepción al autor de llamada al final de la secuencia.Si el flujo de trabajo permanece en memoria durante un tiempo muy corto \(menos de 5 segundos\), o una granja de servidores web es grande y la posibilidad de que se entregue otro mensaje al mismo host no es muy alta, use <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction> para lograr la mejor latencia.  
  
 La característica Acción de excepción bloquedada de instancia admite los siguientes escenarios.En todos los escenarios, si la propiedad instanceLockedExceptionAction de SqlWorkflowInstanceStore está establecida en <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction> o <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction>, el host reintenta adquirir el bloqueo en instancias periódicamente de forma transparente.  
  
1.  **Permitir el apagado estable y el reciclaje superpuesto de dominios de aplicación.** Supongamos que se está reciclando un **AppDomain** con un host de servicio que esté ejecutando instancias de servicio de flujo de trabajo y que se plantea un nuevo **AppDomain** para administrar las nuevas solicitudes en paralelo mientras se acaba sin contratiempos con el **AppDomain** antiguo.El apagado espera hasta que las instancias de servicio del flujo de trabajo estén inactivas, y, a continuación, conserva y descarga las instancias.Cualquier intento por parte de los hosts en el nuevo **AppDomain** para bloquear una instancia producirá una <xref:System.Runtime.DurableInstancing.InstanceLockedException>.  
  
2.  **Escalado horizontal de flujos de trabajo de duración en una granja homogénea de servidores.** Supongamos que hay un nodo de una granja de servidores en el que una instancia de flujo de trabajo está ejecutando bloqueos y el host del flujo de trabajo no puede quitar los bloqueos en la instancia que está ejecutando.Cuando un host del servicio que se ejecuta en otro nodo de la granja recibe un mensaje para esa instancia de flujo de trabajo, intenta adquirir los bloqueos en estas instancias y recibirá <xref:System.Runtime.DurableInstancing.InstanceLockedException>.Los bloqueos expirarán después de algún tiempo porque el host que se suponía que iba a renovar el bloqueo ya no existe.  
  
     **Escalado horizontal de flujos de trabajo de duración en una granja homogénea de servidores.**  Supongamos que desea escalar un flujo de trabajo de duración de manera horizontal usando varios hosts detrás de un NLB \(equilibrador de carga de red\). El host del flujo de trabajo que se ejecuta en un nodo de la granja carga una instancia de flujo de trabajo y está procesando un mensaje, y el mensaje siguiente a la instancia se enruta hacia el host que se está ejecutando en otro nodo porque el NLB no tiene el algoritmo de enrutamiento para entregar los mensajes al host que ya está ejecutando la instancia.Al recibir el mensaje, el segundo host intenta cargar la instancia de flujo de trabajo y recibe <xref:System.Runtime.DurableInstancing.InstanceLockedException> porque el primer host tiene un bloqueo en la instancia.El primer host desbloqueará la instancia cuando haya terminado de procesar el primer mensaje y el segundo host adquirirá el bloqueo cuando lo vuelva a intentar la próxima vez, cargue la instancia y procese el segundo mensaje.