---
title: "Depurar c&#243;digo de GPU | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: c7e77a5a-cb57-4b11-9187-ecc89acc8775
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Depurar c&#243;digo de GPU
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede depurar el código de C\+\+ que se está ejecutando en la unidad central de gráficos \(GPU\).  La compatibilidad con la depuración de GPU en Visual Studio incluye la detección de carrera, el inicio de procesos y su asociación y la integración en las ventanas de depuración.  
  
## Plataformas compatibles  
 La depuración se admite en [!INCLUDE[win7](../debugger/includes/win7_md.md)], [!INCLUDE[win8](../debugger/includes/win8_md.md)], [!INCLUDE[winsvr08_r2](../debugger/includes/winsvr08_r2_md.md)], y [!INCLUDE[winserver8](../debugger/includes/winserver8_md.md)].  Para depurar en el emulador de software, se requiere [!INCLUDE[win8](../debugger/includes/win8_md.md)] o [!INCLUDE[winserver8](../debugger/includes/winserver8_md.md)].  Para depurar en el hardware, debe instalar los controladores de su tarjeta gráfica.  No todos los proveedores de hardware implementan todas las características del depurador.  Vea la documentación del proveedor para conocer las limitaciones.  
  
> [!NOTE]
>  Los proveedores de hardware independientes que deseen admitir la depuración de GPU en Visual Studio deben crear un archivo DLL que implemente la interfaz VSD3DDebug y esté diseñado para sus propios controladores.  
  
## Configurar la depuración de GPU  
 El depurador no puede interrumpir el código de CPU y el código de GPU en la misma ejecución de la aplicación.  De forma predeterminada, el depurador interrumpe el código de CPU.  Para depurar el código de GPU, siga uno de estos dos pasos:  
  
-   En la lista **Depurar tipo** de la barra de herramientas **Estándar**, elija **Solo GPU**.  
  
-   En el **Explorador de soluciones**, en el menú contextual del proyecto, elija **Propiedades**.  En el cuadro de diálogo **Páginas de propiedades**, seleccione **Depuración** y, a continuación, elija **Solo GPU** en la lista **Tipo de depurador**.  
  
## Iniciar y asociar a aplicaciones  
 Puede utilizar los comandos de depuración de Visual Studio para iniciar y detener la depuración de GPU.  Para obtener más información, vea [Desplazarse por el código con el depurador](../debugger/navigating-through-code-with-the-debugger.md).  También puede asociar el depurador de GPU a un proceso en ejecución, pero únicamente si dicho proceso ejecuta código de GPU.  Para obtener más información, vea [Crear asociaciones con procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
## Ejecutar Tile actual hasta el cursor y Ejecutar hasta el cursor  
 Al depurar en la GPU, tiene dos opciones para ejecutar hasta la ubicación del cursor.  Los comandos de ambas opciones están disponibles en el menú contextual del editor de código.  
  
1.  El comando **Ejecutar hasta el cursor** ejecuta la aplicación hasta que llega a la ubicación del cursor y, a continuación, se interrumpe.  Esto no implica que el subproceso actual se ejecute hasta el cursor; más bien significa que el primer subproceso que alcanza la ubicación del cursor desencadena la interrupción.  Vea [Desplazarse por el código con el depurador](../debugger/navigating-through-code-with-the-debugger.md).  
  
2.  El comando **Ejecutar Tile actual hasta el cursor** ejecuta la aplicación hasta que todos los subprocesos del icono actual alcanzan el cursor y, a continuación, se interrumpe.  
  
## Ventanas de depuración  
 Mediante determinadas ventanas de depuración, puede examinar, marcar e inmovilizar subprocesos de GPU.  Para obtener más información, vea:  
  
-   [Uso de la ventana Tareas paralelas](../debugger/using-the-parallel-stacks-window.md)  
  
-   [Usar la ventana Tareas](../debugger/using-the-tasks-window.md)  
  
-   [Cómo: Utilizar la Ventana Inspección paralela](../debugger/how-to-use-the-parallel-watch-window.md)  
  
-   [Depurar procesos y subprocesos](../debugger/debug-threads-and-processes.md) \(Barra de herramientas de la ubicación de depuración\)  
  
-   [Cómo: Utilizar la ventana Subprocesos de GPU](../debugger/how-to-use-the-gpu-threads-window.md)  
  
## Excepciones de la sincronización de datos  
 El depurador puede identificar varias condiciones de sincronización de datos durante la ejecución.  Cuando se detecta una condición, el depurador entra en el estado de interrupción.  Tiene dos opciones: **Interrumpir** o **Continuar**.  Mediante el cuadro de diálogo **Excepciones**, puede configurar si el depurador detectará estas condiciones y también para qué condiciones se interrumpirá.  Para obtener más información, vea [Administración de excepciones con el depurador](../debugger/managing-exceptions-with-the-debugger.md).  También puede utilizar el cuadro de diálogo **Opciones** para especificar que el depurador omita las excepciones si los datos escritos no cambian el valor de los datos.  Para obtener más información, vea [General, Depuración, Opciones \(Cuadro de diálogo\)](../debugger/general-debugging-options-dialog-box.md).  
  
## Solución de problemas  
  
### Especificar un acelerador  
 Los puntos de interrupción del código de GPU solo se visitan si el código se ejecuta en el acelerador [accelerator::direct3d\_ref](../Topic/accelerator::direct3d_ref%20Data%20Member.md) \(REF\).  Si no especifica un acelerador en el código, el acelerador REF se selecciona automáticamente como el **Tipo de acelerador de depuración** en las propiedades del proyecto.  Si el código selecciona explícitamente un acelerador, el acelerador REF no se usará durante la depuración y los puntos de interrupción no se visitarán a menos que el hardware de GPU sea compatible con la depuración.  Puede resolverlo escribiendo código para que utilice el acelerador REF durante la depuración.  Para obtener más información, vea las propiedades del proyecto y [Usar objetos accelerator y accelerator\_view](/visual-cpp/parallel/amp/using-accelerator-and-accelerator-view-objects) y [Configuración del proyecto para una configuración de depuración de C\+\+](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
### Puntos de interrupción condicionales  
 Se admiten puntos de interrupción condicionales en el código de GPU, pero no todas las expresiones se pueden evaluar en el dispositivo.  Cuando una expresión no se puede evaluar en el dispositivo, se evalúa en el depurador.  Es probable que el depurador se ejecute más despacio que el dispositivo.  
  
### Error: problema de configuración con el tipo de acelerador de depuración seleccionado.  
 Este error se produce cuando existe una incoherencia entre la configuración del proyecto y la configuración del equipo en el que está depurando.  Para obtener más información, vea [Configuración del proyecto para una configuración de depuración de C\+\+](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
### Error: el controlador de depuración del tipo de acelerador de depuración seleccionado no está instalado en la máquina de destino.  
 Este error se produce si está depurando en un equipo remoto.  El depurador no puede determinar si los controladores están instalados en el equipo remoto hasta el momento de la ejecución.  Los controladores los suministra el fabricante de la tarjeta gráfica.  
  
### Error: la función de detección del tiempo de espera y recuperación \(TDR\) debe estar deshabilitada en el sitio remoto.  
 Es posible que para los cálculos de C\+\+ AMP se supere el intervalo de tiempo predeterminado establecido por la detección de tiempo de espera de Windows y el proceso de recuperación \(TDR\).  Cuando ocurre esto, se cancela el cálculo y se pierden los datos.  Para obtener más información, vea [Control de los TDR en C\+\+ AMP](http://go.microsoft.com/fwlink/p/?LinkId=249154).  
  
## Vea también  
 [Tutorial: Depurar una aplicación de C\+\+ AMP](../Topic/Walkthrough:%20Debugging%20a%20C++%20AMP%20Application.md)   
 [Configuración del proyecto para una configuración de depuración de C\+\+](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Iniciar la depuración de GPU en Visual Studio](http://go.microsoft.com/fwlink/p/?LinkId=255381)