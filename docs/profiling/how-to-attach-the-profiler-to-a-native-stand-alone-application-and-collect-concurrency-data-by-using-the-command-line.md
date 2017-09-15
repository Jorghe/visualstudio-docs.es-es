---
title: "Cómo: Adjuntar el generador de perfiles a una aplicación nativa independiente y recopilar datos de simultaneidad mediante la línea de comandos | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 12d3e0f3-4b74-4e66-8fbf-8ac99bd4f91c
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 8b83635ae6d727cdb0e589852e2ed167543d16ce
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-concurrency-data-by-using-the-command-line"></a>Cómo: Adjuntar el generador de perfiles a una aplicación nativa independiente y recopilar datos de simultaneidad utilizando la línea de comandos
En este tema se describe cómo utilizar las herramientas de línea de comandos de las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para adjuntar el generador de perfiles a una aplicación independiente nativa (C/C++) en ejecución y recopilar datos de contención de subprocesos.  
  
> [!NOTE]
>  Las herramientas de línea de comandos de las Herramientas de generación de perfiles se encuentran en el subdirectorio \Team Tools\Performance Tools del directorio de instalación de Visual Studio. En equipos de 64 bits, están disponibles las dos versiones de las herramientas, la de 64 bits y la de 32 bits. Para utilizar las herramientas de línea de comandos del generador de perfiles, debe agregar la ruta de acceso de las herramientas a la variable de entorno PATH de la ventana **Símbolo del sistema** o agregarla al propio comando. Para obtener más información, consulte [Especificar la ruta de acceso a las herramientas de línea de comandos](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Mientras el generador de perfiles está adjunto a la aplicación, puede pausar y reanudar la recolección de datos. Para finalizar una sesión de generación de perfiles, el generador de perfiles no debe estar ya adjunto a la aplicación y debe apagarse explícitamente.  
  
## <a name="attaching-the-profiler-to-a-running-native-application"></a>Adjuntar el generador de perfiles a una aplicación nativa en ejecución  
  
#### <a name="to-attach-the-profiler-to-a-running-native-application"></a>Para adjuntar el generador de perfiles a una aplicación nativa en ejecución  
  
1.  En un símbolo del sistema, escriba el siguiente comando:  
  
     [VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency**  
  
     Puede usar cualquiera de las opciones de la tabla siguiente con la opción **/start:concurrency**.  
  
    |Opción|Descripción|  
    |------------|-----------------|  
    |[/user](../profiling/user-vsperfcmd.md) **:**[`Domain\`]`Username`|Especifica el dominio y el nombre de usuario opcionales de la cuenta a la que se va a conceder acceso al generador de perfiles.|  
    |[/crosssession](../profiling/crosssession.md)|Habilita la generación de perfiles de procesos en otros inicios de sesión.|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Especifica un contador de rendimiento de Windows que se va a recopilar durante la generación de perfiles.|  
    |[/automark](../profiling/automark.md) **:** `Interval`|Utilizar solo con **/wincounter**. Especifica el número de milisegundos entre eventos de recopilación de contadores de rendimiento de Windows. El valor predeterminado es 500.|  
    |[/events](../profiling/events-vsperfcmd.md) **:** `Config`|Especifica un evento de Seguimiento de eventos para Windows (ETW) que se va a recopilar durante la generación de perfiles. Los eventos ETW se recopilan en un archivo (.etl) independiente.|  
  
2.  Adjunte el generador de perfiles a la aplicación de destino escribiendo el comando siguiente:  
  
     **VSPerfCmd**  [/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`}  
  
     `PID` especifica el identificador de proceso de la aplicación de destino. Puede ver los identificadores de todos los procesos que se están ejecutando en el Administrador de tareas de Windows.  
  
## <a name="controlling-data-collection"></a>Controlar la recolección de datos  
 Mientras se ejecuta la aplicación de destino, puede controlar la recolección de datos iniciando o deteniendo la escritura de los datos en el archivo con las opciones de VSPerfCmd.exe. Al controlar la recolección de datos, puede recopilar datos de una parte específica de la ejecución de un programa, como por ejemplo el inicio o el cierre de una aplicación.  
  
#### <a name="to-start-and-stop-data-collection"></a>Para iniciar y detener la recolección de datos  
  
-   Los pares de opciones de la tabla siguiente inician y detienen la recolección de datos. Especifique cada opción en una línea de comandos diferente. Puede activar y desactivar la recolección de datos varias veces.  
  
    |Opción|Descripción|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Inicia (**/globalon**) o detiene (**/globaloff**) la recolección de datos para todos los procesos.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Inicia (**/processon**) o detiene (**/processoff**) la recolección de datos para el proceso que especifica el identificador de proceso (`PID`).|  
    |[/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [/detach](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/attach** inicia la recolección de datos para el proceso especificado por el identificador de proceso (`PID`) o por el nombre de proceso (*ProcName*). **/detach** detiene la recolección de datos para el proceso especificado o para todos los procesos si no se especifica uno.|  
  
## <a name="ending-the-profiling-session"></a>Finalizar la sesión de generación de perfiles  
 Para finalizar la sesión de generación de perfiles, el generador de perfiles no debe estar recopilando datos. Para dejar de recopilar datos de una aplicación que se perfila con el método de muestreo, puede cerrar la aplicación o invocar la opción **VSPerfCmd /detach**. Después, invoque la opción **VSPerfCmd /shutdown** para desactivar el generador de perfiles y cerrar el archivo de datos de generación de perfiles.  
  
#### <a name="to-end-a-profiling-session"></a>Para finalizar una sesión de generación de perfiles  
  
1.  Desasocie el generador de perfiles de la aplicación de destino cerrándolo o escribiendo el siguiente comando:  
  
     **VSPerfCmd /detach**  
  
2.  Escriba el siguiente comando para apagar el generador de perfiles:  
  
     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)