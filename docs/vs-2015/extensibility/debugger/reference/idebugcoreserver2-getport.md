---
title: IDebugCoreServer2::GetPort | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugCoreServer2::GetPort
helpviewer_keywords:
- IDebugCoreServer2::GetPort
ms.assetid: 3f5ea4a8-6085-4600-980a-9e48f8b5be56
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cf11c769f1772ba11a514dec4e72bf7f2633ceaa
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49197165"
---
# <a name="idebugcoreserver2getport"></a>IDebugCoreServer2::GetPort
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Recupera un puerto específico.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT GetPort(   
   REFGUID       guidPort,  
   IDebugPort2** ppPort  
);  
```  
  
```csharp  
int GetPort(   
   ref Guid        guidPort,  
   out IDebugPort2 ppPort  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `guidPort`  
 [in] GUID del puerto que desea recuperar.  
  
 `ppPort`  
 [out] Devuelve un [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) objeto que representa el puerto deseado.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error. Devuelve `E_PORTSUPPLIER_NO_PORT` si no hay ningún puerto con el identificador proporcionado.  
  
## <a name="see-also"></a>Vea también  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)

