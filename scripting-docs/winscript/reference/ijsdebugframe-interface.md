---
title: "IJsDebugFrame (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 5af46b18-9d25-4a23-b8d1-fa23bea3efcf
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IJsDebugFrame (Interfaz)
Representa un marco de pila.  
  
## Sintaxis  
  
```  
IJsDebugFrame : public IUnknown;  
```  
  
## Miembros  
  
### Métodos públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[IJsDebugFrame::Evaluate \(Método\)](../../winscript/reference/ijsdebugframe-evaluate-method.md)|Evalúa una expresión en el contexto de este marco de pila.|  
|[IJsDebugFrame::GetDebugProperty \(Método\)](../../winscript/reference/ijsdebugframe-getdebugproperty-method.md)|Devuelve un explorador de propiedades para este marco de pila.|  
|[IJsDebugFrame::GetDocumentPositionWithId \(Método\)](../../winscript/reference/ijsdebugframe-getdocumentpositionwithid-method.md)|Devuelve la posición actual de este marco de pila dentro del documento de nivel de usuario.|  
|[IJsDebugFrame::GetDocumentPositionWithName \(Método\)](../../winscript/reference/ijsdebugframe-getdocumentpositionwithname-method.md)|Devuelve la posición actual de este marco de pila dentro del documento de nivel de usuario.|  
|[IJsDebugFrame::GetName \(Método\)](../../winscript/reference/ijsdebugframe-getname-method.md)|Obtiene el nombre descriptivo del marco de pila.|  
|[IJsDebugFrame::GetReturnAddress \(Método\)](../../winscript/reference/ijsdebugframe-getreturnaddress-method.md)|Obtiene la dirección de devolución insertada en el 'inicio' \(vea GetStackRange\) del marco.|  
|[IJsDebugFrame::GetStackRange \(Método\)](../../winscript/reference/ijsdebugframe-getstackrange-method.md)|Devuelve el intervalo de direcciones absolutas del marco de pila de JavaScript lógico.|  
  
## Requisitos  
 **Encabezado:** jscript9diag.h  
  
## Vea también  
 [Referencia de interfaces de Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)