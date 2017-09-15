---
title: "Elegir una estrategia de actualizaci&#243;n de ClickOnce | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "actualizaciones de aplicaciones, ClickOnce"
  - "implementación ClickOnce, estrategias de actualización"
  - "actualizaciones, ClickOnce"
ms.assetid: d8b6e7bb-4ea0-47f3-91cd-48580bdceccc
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 23
---
# Elegir una estrategia de actualizaci&#243;n de ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] puede proporcionar actualizaciones automáticas de aplicaciones.  Una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] lee periódicamente su archivo de manifiesto de implementación para ver si hay actualizaciones disponibles para la aplicación.  En caso afirmativo, la nueva versión de la aplicación se descarga y se ejecuta.  Para una mayor eficiencia, se descargan sólo los archivos que han cambiado.  
  
 A la hora de diseñar una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], es necesario determinar qué estrategia utilizará la aplicación para comprobar si hay actualizaciones disponibles.  Se pueden utilizar tres estrategias básicas: comprobar si hay actualizaciones al inicio de la aplicación, comprobar si hay actualizaciones después del inicio de la aplicación \(ejecutándose en un subproceso de segundo plano\) o proporcionando una interfaz de usuario para las actualizaciones.  
  
 Además, puede determinar con qué frecuencia debe comprobar la aplicación si hay actualizaciones y puede hacer que las actualizaciones sean obligatorias.  
  
> [!NOTE]
>  Las actualizaciones de aplicaciones requieren conectividad de red.  Si no hay conexión de red, la aplicación se ejecutará sin comprobar si hay actualizaciones, independientemente de la estrategia de actualización elegida.  
  
> [!NOTE]
>  En .NET Framework 2.0 y .NET Framework 3.0, cada vez que la aplicación comprueba si hay actualizaciones, antes o después del inicio, o mediante las API de <xref:System.Deployment.Application>, debe establecer `deploymentProvider` en el manifiesto de implementación.  El elemento `deploymentProvider` corresponde, en Visual Studio, al campo **Ubicación de actualizaciones** del cuadro de diálogo **Actualizaciones** de la ficha **Publicar**.  Esta regla es más flexible en .NET Framework 3.5.  Para obtener más información, vea [Implementar aplicaciones ClickOnce para los servidores de pruebas y producción sin nueva firma](../deployment/deploying-clickonce-applications-for-testing-and-production-servers-without-resigning.md).  
  
## Comprobar si hay actualizaciones después del inicio de la aplicación  
 Con esta estrategia, la aplicación intentará buscar y leer en segundo plano el archivo de manifiesto de implementación mientras la aplicación se está ejecutando.  Si hay una actualización disponible, la próxima vez que el usuario ejecute la aplicación, se le pedirá que descargue e instale la actualización.  
  
 Esta estrategia funciona mejor para las conexiones de red con un bajo ancho de banda o para las aplicaciones de gran tamaño que podrían requerir mucho tiempo de descarga.  
  
 Para habilitar esta estrategia de actualización, haga clic en **Después de que se inicie la aplicación** en la sección **Elija cuándo debe buscar actualizaciones la aplicación** del cuadro de diálogo **Actualizaciones de la aplicación**.  A continuación, especifique un intervalo de actualización en la sección **Especifique la frecuencia con la que la aplicación buscará actualizaciones**.  
  
 Esto equivale a cambiar el elemento **Update** del manifiesto de implementación tal y como se indica a continuación:  
  
```  
<!-- When to check for updates -->  
<subscription>  
   <update>  
      <expiration maximumAge="6" unit="hours" />  
   </update>  
</subscription>  
```  
  
## Comprobar si hay actualizaciones antes del inicio de la aplicación  
 La estrategia predeterminada consiste en intentar buscar y leer el archivo de manifiesto de implementación antes de que se inicie la aplicación.  Con esta estrategia, la aplicación intentará buscar y leer el archivo de manifiesto de implementación cada vez que el usuario inicie la aplicación.  Si hay disponible alguna actualización, se descargará y se iniciará; de lo contrario, se iniciará la versión existente de la aplicación.  
  
 Esta estrategia funciona mejor para las conexiones de red de un ancho de banda elevado; el retraso en el inicio de la aplicación puede ser inaceptablemente largo en conexiones de ancho de banda reducido.  
  
 Para habilitar esta estrategia de actualización, haga clic en **Antes de que se inicie la aplicación** en la sección **Elija cuándo debe buscar actualizaciones la aplicación** del cuadro de diálogo **Actualizaciones de la aplicación**.  
  
 Esto equivale a cambiar el elemento **Update** del manifiesto de implementación tal y como se indica a continuación:  
  
```  
<!-- When to check for updates -->  
<subscription>  
   <update>  
      <beforeApplicationStartup />  
   </update>  
</subscription>  
```  
  
## Hacer que las actualizaciones sean obligatorias  
 Puede haber ocasiones en las que desea obligar a los usuarios a ejecutar una versión actualizada de su aplicación.  Por ejemplo, podría realizar un cambio en un recurso externo como un servicio Web que impediría que funcionara correctamente la versión anterior de su aplicación.  En este caso, debería marcar su actualización como obligatoria e impedir que los usuarios ejecuten la versión anterior.  
  
> [!NOTE]
>  Aunque es posible obligar a que se efectúen las actualizaciones utilizando las otras estrategias de actualización, comprobar su existencia **Antes de que se inicie la aplicación** es la única manera de garantizar que no se pueda ejecutar una versión antigua.  Si la actualización obligatoria se detecta al inicio, el usuario deberá aceptarla o cerrar la aplicación.  
  
 Para marcar una actualización como obligatoria, haga clic en **Especifique la versión mínima requerida para esta aplicación** en el cuadro de diálogo **Actualizaciones de la aplicación** y, a continuación, especifique la versión de publicación \(**Principal**, **Secundaria**, **Compilación**, **Revisión**\), que indica el número más bajo de versión de la aplicación que se puede instalar.  
  
 Es lo mismo que establecer el atributo **minimumRequiredVersion** del elemento **Deployment** del manifiesto de implementación; por ejemplo:  
  
```  
<deployment install="true" minimumRequiredVersion="1.0.0.0">  
```  
  
## Especificar intervalos de actualización  
 También puede especificar con qué frecuencia se comprueba si hay actualizaciones.  Para ello, especifique que la aplicación debe comprobar si hay actualizaciones tras el inicio, tal y como se ha descrito anteriormente en la sección "Comprobar si hay actualizaciones tras el inicio de la aplicación".  
  
 Para especificar el intervalo de actualización, establezca las propiedades de **Especifique la frecuencia con la que la aplicación buscará actualizaciones** en el cuadro de diálogo **Actualizaciones de la aplicación**.  
  
 Esto equivale a establecer los atributos **maximumAge** y **unit** del elemento **Update** del manifiesto de implementación.  
  
 Por ejemplo, puede desear comprobarlo cada vez que se ejecuta la aplicación, o una vez por semana o una vez al mes.  Si no hay ninguna conexión de red en el momento especificado, la comprobación de actualización se realizará la próxima vez que se ejecute la aplicación.  
  
## Proporcionar una interfaz de usuario para las actualizaciones  
 Con esta estrategia, el desarrollador de la aplicación proporciona una interfaz que permite al usuario elegir cuándo y con qué frecuencia comprobará la aplicación si hay actualizaciones.  Por ejemplo, podría proporcionar un elemento de menú "Comprobar ahora si hay actualizaciones" o un cuadro de diálogo "Configuración de actualizaciones" que ofrezca opciones para distintos intervalos de actualización.  Las API de implementación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] proporcionan un marco de trabajo para la programación de una interfaz de usuario de actualizaciones personalizada.  Para obtener más información, vea el espacio de nombres <xref:System.Deployment.Application>.  
  
 Si la aplicación utiliza las API de implementación para controlar su propia lógica de actualización, debería bloquear la comprobación de actualizaciones del modo en que se describe en la sección "Bloquear la comprobación de actualizaciones" que se muestra más adelante.  
  
 Esta estrategia es más adecuada cuando es necesario disponer de diferentes estrategias de actualización para los distintos usuarios.  
  
## Bloquear la comprobación de actualizaciones  
 También es posible impedir que su aplicación compruebe si hay actualizaciones disponibles.  Por ejemplo, podría tener una aplicación sencilla que no se vaya a actualizar nunca, pero desea aprovechar la facilidad de instalación que ofrece la implementación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
 Deberá bloquear también la comprobación de actualizaciones si la aplicación utiliza las API de implementación para realizar sus propias actualizaciones; vea la sección "Proporcionar una interfaz de usuario para las actualizaciones" anterior.  
  
 Para bloquear la comprobación de actualizaciones, desactive la casilla **La aplicación debe buscar actualizaciones** del cuadro de diálogo Actualizaciones de la aplicación.  
  
 También puede bloquear la comprobación de actualizaciones quitando la etiqueta `<Subscription>` del manifiesto de implementación.  
  
## Elevación de permisos y actualizaciones  
 Si una nueva versión de una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] exige un mayor nivel de confianza para ejecutarse que en la versión anterior, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] preguntará al usuario si desea que se conceda a la aplicación este nivel de confianza superior.  Si el usuario lo declina, la actualización no se instalará.  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] preguntará al usuario si desea volver a instalar la aplicación la próxima vez que se reinicie.  Si, en esta ocasión, el usuario vuelve a declinar que se conceda un mayor nivel de confianza y la actualización no está marcada como obligatoria, se ejecutará la versión anterior de la aplicación.  Sin embargo, si la actualización es obligatoria, la aplicación no se ejecutará de nuevo hasta que el usuario acepte el nivel de confianza superior.  
  
 Si utiliza la implementación de aplicaciones de confianza, no se realizará ninguna pregunta sobre los niveles de confianza.  Para obtener más información, vea [Información general sobre la implementación de aplicaciones de confianza](../deployment/trusted-application-deployment-overview.md).  
  
## Vea también  
 <xref:System.Deployment.Application>   
 [Seguridad e implementación ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Elegir una estrategia de implementación de ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [Proteger las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Cómo realiza ClickOnce actualizaciones de aplicaciones](../deployment/how-clickonce-performs-application-updates.md)   
 [Cómo: Administrar actualizaciones de aplicaciones ClickOnce](../deployment/how-to-manage-updates-for-a-clickonce-application.md)