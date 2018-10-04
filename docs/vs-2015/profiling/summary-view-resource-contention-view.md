---
title: 'Vista Resumen: vista de contención de recursos | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Summary view
ms.assetid: 6da57b83-7b42-4d7c-9aea-8e0a830faf6b
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bf83509cd56343001a94da619b9246464ed75bdf
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47565900"
---
# <a name="summary-view---resource-contention-view"></a>Vista Resumen: vista de contención de recursos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [vista Resumen: vista de contención de recursos](https://docs.microsoft.com/visualstudio/profiling/summary-view-resource-contention-view).  
  
La vista Resumen muestra información sobre los eventos de la aplicación en el que se suspendió un proceso o subproceso mientras esperaba el acceso a un recurso.  
  
 Para obtener más información, incluyendo una descripción de los vínculos de notificación y las listas de informes, consulte [Vista Resumen](../profiling/summary-view.md).  
  
## <a name="timeline-graph"></a>Gráfico de escala de tiempo  
 El gráfico de escala de tiempo en la vista Resumen muestra el número de eventos de contención de la aplicación de la que se generan perfiles durante el tiempo que se generaron perfiles. Puede usar el gráfico de escala de tiempo para filtrar la vista en un intervalo de tiempo seleccionado. Para obtener más información, consulte [Cómo: Filtrar vistas de informe desde la escala de tiempo de resumen](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
## <a name="most-contended-resources"></a>Recursos más contenidos  
 **Recursos más contenidos** enumera los recursos de la aplicación que provocaron más eventos de contención. Puede hacer clic en un nombre de recurso para mostrar la vista Contenciones. La vista Contenciones proporciona una escala de tiempo detallada de las contenciones de recursos por subproceso.  
  
 **Recursos más contenidos** incluye los siguientes datos para cada recurso.  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Name**|Nombre del recurso.|  
|**Porcentaje de contenciones**|El porcentaje de todos los eventos de contención de los datos de generación de perfiles que eran contenciones de este recurso.|  
  
## <a name="most-contended-thread"></a>Subprocesos más contenidos  
 **Subprocesos más contenidos** enumera los subprocesos de la aplicación con el mayor número de eventos de contención. Puede hacer clic en el nombre de un subproceso para mostrar la vista Contenciones que proporciona una escala de tiempo detallada de las contenciones de recursos por el subproceso.  
  
 **Subprocesos más contenidos** incluye los siguientes datos para cada subproceso.  
  
|Columna|Descripción|  
|------------|-----------------|  
|**ID**|Identifiador del subproceso.|  
|**Name**|Nombre del proceso que posee el subproceso.|  
|**Porcentaje de contenciones**|El porcentaje de todos los eventos de contención de los datos de generación de perfiles que eran contenciones de este recurso.|


