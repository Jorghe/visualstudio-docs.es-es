---
title: IDebugProcessEx2 | Documentos de Microsoft
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
- IDebugProcessEx2
helpviewer_keywords:
- IDebugProcessEx2 interface
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ff9e8555df8041a8a4a61b3c4ecca27068419614
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47566712"
---
# <a name="idebugprocessex2"></a>IDebugProcessEx2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IDebugProcessEx2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprocessex2).  
  
Esta interfaz permite que la sesión de depuración manager (SDM) notificar a un proceso que está adjuntando a o cuando se desasocia del proceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugProcessEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Un proveedor de puerto personalizado implementa esta interfaz en el mismo objeto que el [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) con el fin de la interfaz:  
  
-   Compatibilidad con seguimiento de las sesiones conectadas a un proceso  
  
-   Compatibilidad con la asociación automática a través de varios motores de depuración  
  
 El proveedor del puerto personalizado puede implementar esta interfaz si así lo decide.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
  
-   Las llamadas SDM [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) en un `IDebugProcess2` interfaz para obtener esta interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugProcessEx2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[Asociar](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|Informa a los procesos que una sesión es ahora el proceso de depuración.|  
|[Desasociar](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|Informa a los procesos que una sesión ya no está depurando el proceso.|  
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|Agrega nodos de programa para obtener una lista de motores de depuración.|  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz es privada entre el SDM y el proceso.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Portpriv.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces del núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
