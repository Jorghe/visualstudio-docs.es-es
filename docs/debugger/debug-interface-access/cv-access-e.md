---
title: CV_access_e | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CV_access_e enumeration
ms.assetid: 33c05d65-abb4-4800-a382-54a3805ea7b0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 35b10f8a98284fdec9e94043a4b827fab226d3aa
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
ms.locfileid: "31457932"
---
# <a name="cvaccesse"></a>CV_access_e
Especifica el ámbito de visibilidad (nivel de acceso) de las funciones miembro y variables.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
typedef enum CV_access_e {   
   CV_private   = 1,  
   CV_protected = 2,  
   CV_public    = 3  
} CV_access_e;  
```  
  
## <a name="elements"></a>Elementos  
 CV_private  
 Miembro tiene acceso privado.  
  
 CV_protected  
 Miembro con acceso protegido.  
  
 CV_public  
 Miembro tiene acceso público.  
  
## <a name="remarks"></a>Comentarios  
 El `friend` especificador de acceso no se incluye aquí porque se suelen usar las funciones no miembro que tiene acceso a los elementos privados y protegidos de la clase. Use la [idiasymbol:: Get_symtag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) método para buscar símbolos con `SymTagFriend` acceso.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: cvconst.h  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Idiasymbol:: Get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)   
 [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)