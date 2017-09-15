---
title: IDebugProgramNode2::DetachDebugger_V7 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
ms.assetid: d2d4b78e-a2dd-4217-97a6-ab648fd2ee2f
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
ms.openlocfilehash: a281d92d93473dffeb8f488cd802a9cee4a779d7
ms.contentlocale: es-es
ms.lasthandoff: 09/06/2017

---
# <a name="idebugprogramnode2detachdebuggerv7"></a>IDebugProgramNode2::DetachDebugger_V7
EN DESUSO. NO UTILICE.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT DetachDebugger_V7 (   
   void   
);  
```  
  
```csharp  
int DetachDebugger_V7 ();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Siempre debe devolver una implementación `E_NOTIMPL`.  
  
## <a name="remarks"></a>Comentarios  
  
> [!WARNING]
>  Como de [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)], este método ya no se utiliza y siempre debe devolver `E_NOTIMPL`.  
  
 Este método se llama cuando el depurador se cierra inesperadamente. Cuando se llama a este método, la DE debe reanudar el programa como si el usuario se separa del mismo. No hay más eventos de depuración se deben enviar. El programa debe estar en un estado donde resulta adjuntable desde otra instancia del depurador.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)