---
title: Función SccQueryChanges | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccQueryChanges
helpviewer_keywords:
- SccQueryChanges function
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d887c0cea989fa6a955edc2f39b9667e7421093d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31139827"
---
# <a name="sccquerychanges-function"></a>SccQueryChanges (función)
Esta función enumera una lista de archivos, proporcionar información acerca de los cambios de nombre de cada archivo a través de una función de devolución de llamada especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
SCCRTN SccQueryChanges(  
   LPVOID           pContext,  
   LONG             nFiles,  
   LPCSTR*          lpFileNames,  
   QUERYCHANGESFUNC pfnCallback,  
   LPVOID           pvCallerData  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 pContext  
 [in] El puntero de contexto de complemento de control de código fuente.  
  
 nFiles  
 [in] Número de archivos en `lpFileNames` matriz.  
  
 lpFileNames  
 [in] Matriz de nombres de archivo para obtener información acerca de.  
  
 pfnCallback  
 [in] Función de devolución de llamada que se llama para cada nombre de archivo en la lista (vea [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) para obtener más información).  
  
 pvCallerData  
 [in] Valor que se pasa sin cambios a la función de devolución de llamada.  
  
## <a name="return-value"></a>Valor devuelto  
 La implementación de complemento de control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC_OK|El proceso de consulta que se completó correctamente.|  
|SCC_E_PROJNOTOPEN|No se ha abierto el proyecto en el control de código fuente.|  
|SCC_E_ACCESSFAILURE|Hubo un problema al obtener acceso al sistema de control de código fuente, probablemente debido a problemas de red o de contención.|  
|SCC_E_NONSPECIFICERROR|Se produjo un error no especificado o general.|  
  
## <a name="remarks"></a>Comentarios  
 Cambios que se está consultas para se encuentran en el espacio de nombres: en concreto, el cambio de nombre, agregar y quitar un archivo.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)   
 [Códigos de error](../extensibility/error-codes.md)