---
title: IDebugProgram2::EnumCodeContexts | Documentos de Microsoft
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
- IDebugProgram2::EnumCodeContexts
helpviewer_keywords:
- IDebugProgram2::EnumCodeContexts
ms.assetid: 478e06a2-07bb-4841-8887-deab0f42ebd0
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1a942cba5dd1840fd39bc7a421ea2e40e7309091
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47579987"
---
# <a name="idebugprogram2enumcodecontexts"></a>IDebugProgram2::EnumCodeContexts
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IDebugProgram2::EnumCodeContexts](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogram2-enumcodecontexts).  
  
Recupera una lista de los contextos de código para una posición determinada en un archivo de origen.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT EnumCodeContexts(   
   IDebugDocumentPosition2*  pDocPos,  
   IEnumDebugCodeContexts2** ppEnum  
);  
```  
  
```csharp  
int EnumCodeContexts(   
   IDebugDocumentPosition2     pDocPos,  
   out IEnumDebugCodeContexts2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pDocPos`  
 [in] Un [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) objeto que representa una posición abstracta en un archivo de origen que se sabe que el IDE.  
  
 `ppEnum`  
 [out] Devuelve un [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md) objeto que contiene una lista de los contextos de código.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Este método permite la depuración de la sesión manager (SDM) o el IDE para asignar una posición de archivo de origen en una posición de código. Más de un contexto de código se devuelve si el origen genera varios bloques de código (por ejemplo, las plantillas de C++).  
  
## <a name="see-also"></a>Vea también  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)   
 [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)
