---
title: Terminación y separado | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fb6705c1189649b986776b99cd105f1e9532e160
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49305336"
---
# <a name="termination-and-detaching"></a>Terminación y desasociación
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A continuación describe la finalización normal.  
  
## <a name="discussion"></a>Explicación  
 Después de la [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) o [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) continúa la interfaz, si hay no hay puntos de interrupción, excepciones, errores de tiempo de ejecución o bucles infinitos en la aplicación que se desea depurar, el programa que se está depurando se ejecutará hasta su finalización. Se trata de una finalización normal.  
  
 Debe enviar un [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) para implementar la finalización normal. Esto requiere la implementación de la [IDebugProgramDestroyEvent2::GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) método.  
  
## <a name="see-also"></a>Vea también  
 [Creación de un motor de depuración personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)

