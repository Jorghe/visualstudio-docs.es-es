---
title: 'Idiaenumdebugstreams:: Clone | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreams::Clone method
ms.assetid: e85ec592-de97-4f95-a774-1623315ba415
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fd9c9f8cfe37cf54181fc9c76b450846c12d5b41
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
ms.locfileid: "31468661"
---
# <a name="idiaenumdebugstreamsclone"></a>IDiaEnumDebugStreams::Clone
Crea un enumerador que contiene el mismo estado de enumeración que el enumerador actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT Clone (   
   IDiaEnumDebugStreams** ppenum  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppenum`  
 [out] Devuelve un [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md) objeto que contiene un duplicado del enumerador. No se duplican las secuencias, solo el enumerador.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)