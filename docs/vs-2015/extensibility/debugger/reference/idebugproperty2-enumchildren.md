---
title: IDebugProperty2::EnumChildren | Documentos de Microsoft
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
- IDebugProperty2::EnumChildren
helpviewer_keywords:
- IDebugProperty2::EnumChildren
ms.assetid: cf79f666-65d1-417c-af7c-9271bac9a267
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 28321edf28a74aab3f888fe9fc1c6bc70de2e93c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49196370"
---
# <a name="idebugproperty2enumchildren"></a>IDebugProperty2::EnumChildren
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Recupera una lista de los elementos secundarios de la propiedad.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT EnumChildren (   
   DEBUGPROP_INFO_FLAGS      dwFields,  
   DWORD                     dwRadix,  
   REFGUID                   guidFilter,  
   DBG_ATTRIB_FLAGS          dwAttribFilter,  
   LPCOLESTR                 pszNameFilter,  
   DWORD                     dwTimeout,  
   IEnumDebugPropertyInfo2** ppEnum  
);  
```  
  
```csharp  
int EnumChildren (   
   enum_DEBUGPROP_INFO_FLAGS   dwFields,  
   uint                        dwRadix,  
   ref Guid                    guidFilter,  
   uint                        dwAttribFilter,  
   string                      pszNameFilter,  
   uint                        dwTimeout,  
   out IEnumDebugPropertyInfo2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwFields`  
 [in] Una combinación de marcas de la [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) enumeración que especifica qué campos de los enumerados [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) son estructuras que deben rellenarse.  
  
 `dwRadix`  
 [in] Especifica la base que se usará para dar formato a cualquier información numérica.  
  
 `guidFilter`  
 [in] GUID del filtro utilizado con el `dwAttribFilter` y `pszNameFilter` parámetros para seleccionar qué `DEBUG_PROPERTY_INFO` son elementos secundarios van a enumerar. Por ejemplo, `guidFilterLocals` filtros para las variables locales.  
  
 `dwAttribFilter`  
 [in] Una combinación de marcas de la [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) enumeración que especifica qué tipo de objetos para enumerar, por ejemplo `DBG_ATTRIB_METHOD` para todos los métodos que podrían ser elementos secundarios de esta propiedad. Puede usar en combinación con la `guidFilter` y `pszNameFilter` parámetros.  
  
 `pszNameFilter`  
 [in] El nombre del filtro utilizado con el `guidFilter` y `dwAttribFilter` parámetros para seleccionar qué `DEBUG_PROPERTY_INFO` son elementos secundarios van a enumerar. Por ejemplo, establecer este parámetro en los filtros "MyX" para todos los elementos secundarios con el nombre "MyX."  
  
 `dwTimeout`  
 [in] Especifica el tiempo máximo, en milisegundos para esperar antes de volver de este método. Use `INFINITE` para esperar indefinidamente.  
  
 `ppEnum`  
 [out] Devuelve un [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) objeto que contiene una lista de las propiedades secundarias.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve el código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)

