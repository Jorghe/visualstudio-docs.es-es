---
title: IDebugProgram2::Continue | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::Continue
helpviewer_keywords:
- IDebugProgram2::Continue
ms.assetid: e5a6e02a-d21b-4a03-a034-e8de1f71ce2e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f52fccf640cca32d4291b3d6fb8626c38370ded3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31116752"
---
# <a name="idebugprogram2continue"></a>IDebugProgram2::Continue
Continúa ejecutando este programa desde un estado de detención. Se conserva un estado de ejecución anterior (por ejemplo, un paso), y el programa empieza a ejecutarse de nuevo.  
  
> [!NOTE]
>  Este método está en desuso. Use la [continuar](../../../extensibility/debugger/reference/idebugprocess3-continue.md) método en su lugar.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT Continue(   
   IDebugThread2* pThread  
);  
```  
  
```csharp  
int Continue(   
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pThread`  
 [in] Un [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objeto que representa el subproceso.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Se llama a este método en este programa sin tener en cuenta la cantidad de programas que se están depurando o el programa que generó el evento de detención. La implementación debe conservar el estado de ejecución anterior (por ejemplo, un paso) y continuar la ejecución como si nunca había dejado antes de completar su ejecución anterior. Es decir, si un subproceso en este programa estaba realizando una operación de paso y se detuvo porque otro programa se detiene y, a continuación, se llama a este método, el programa debe completar la operación de paso original.  
  
> [!WARNING]
>  No se envía ningún evento de detención o a un evento (sincrónico) inmediato [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) al controlar esta llamada; en caso contrario, el depurador puede dejar de responder.  
  
## <a name="see-also"></a>Vea también  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)