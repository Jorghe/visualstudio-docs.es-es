---
title: Tarea GetFrameworkPath | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFrameworkPath task [MSBuild]
- MSBuild, GetFrameworkPath task
ms.assetid: 5b7bcdd7-d4a0-442d-af29-8aadb3b10598
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 792c6fd47882e0ff116859c80e3e406e875bf5fe
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47565762"
---
# <a name="getframeworkpath-task"></a>GetFrameworkPath (Tarea)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [GetFrameworkPath (tarea)](https://docs.microsoft.com/visualstudio/msbuild/getframeworkpath-task).  
  
  
Recupera la ruta de acceso a los ensamblados de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].  
  
## <a name="task-parameters"></a>Parámetros de tareas  
 En la siguiente tabla se describen los parámetros de la tarea `GetFrameworkPath`.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`FrameworkVersion11Path`|Parámetro de salida `String` opcional.<br /><br /> Contiene la ruta de acceso a los ensamblados de la versión 1.1 de Framework, si está presente. De lo contrario, devuelve `null`.|  
|`FrameworkVersion20Path`|Parámetro de salida `String` opcional.<br /><br /> Contiene la ruta de acceso a los ensamblados de la versión 2.0 de Framework, si está presente. De lo contrario, devuelve `null`.|  
|`FrameworkVersion30Path`|Parámetro de salida `String` opcional.<br /><br /> Contiene la ruta de acceso a los ensamblados de la versión 3.0 de Framework, si está presente. De lo contrario, devuelve `null`.|  
|`FrameworkVersion35Path`|Parámetro de salida `String` opcional.<br /><br /> Contiene la ruta de acceso a los ensamblados de la versión 3.5 de Framework, si está presente. De lo contrario, devuelve `null`.|  
|`FrameworkVersion40Path`|Parámetro de salida `String` opcional.<br /><br /> Contiene la ruta de acceso a los ensamblados de la versión 4.0 de Framework, si está presente. De lo contrario, devuelve `null`.|  
|`Path`|Parámetro de salida `String` opcional.<br /><br /> Contiene la ruta de acceso a los ensamblados de Framework más recientes, si alguno está disponible. De lo contrario, devuelve `null`.|  
  
## <a name="remarks"></a>Comentarios  
 Si están instaladas varias versiones de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], esta tarea devuelve la versión en la que puede ejecutarse [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].  
  
 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se usa la tarea `GetFrameworkPath` para almacenar la ruta de acceso a [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] en la propiedad `FrameworkPath`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="GetPath">  
        <GetFrameworkPath>  
            <Output  
                TaskParameter="Path"  
                PropertyName="FrameworkPath" />  
        </GetFrameworkPath>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)


