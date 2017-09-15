---
title: IDebugThread2::GetLogicalThread | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugThread2::GetLogicalThread
helpviewer_keywords:
- IDebugThread2::GetLogicalThread
ms.assetid: bce6230e-41d4-49b7-a050-2dde5efb6805
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: d7a5362aad3a8044ec484f70e71812e45e6a3a8d
ms.contentlocale: es-es
ms.lasthandoff: 09/06/2017

---
# <a name="idebugthread2getlogicalthread"></a>IDebugThread2::GetLogicalThread
Motores de depuración no implementan este método.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetLogicalThread(   
   IDebugStackFrame2*     pStackFrame,  
   IDebugLogicalThread2** ppLogicalThread  
);  
```  
  
```csharp  
int GetLogicalThread(   
   IDebugStackFrame2        pStackFrame,  
   out IDebugLogicalThread2 ppLogicalThread  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pStackFrame`  
 [in] Un [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) objeto que representa el marco de pila.  
  
 `ppLogicalThread`  
 [out] Devuelve un `IDebugLogicalThread2` interfaz que representa el subproceso lógico asociado. Una implementación de motor de depuración debe establecer esto en un valor null.  
  
## <a name="return-value"></a>Valor devuelto  
 Depurar las implementaciones de motor siempre devuelven `E_NOTIMPL`.  
  
## <a name="see-also"></a>Vea también  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)