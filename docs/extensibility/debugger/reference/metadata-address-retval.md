---
title: METADATA_ADDRESS_RETVAL | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- METADATA_ADDRESS_RETVAL
helpviewer_keywords:
- METADATA_ADDRESS_RETVAL structure
ms.assetid: 5b0ec0fb-84b3-4ce7-8e24-becf3d881d7d
caps.latest.revision: 6
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
ms.openlocfilehash: c7da8b57554d8d9dca3dd7973d1afc7e7205bfc0
ms.contentlocale: es-es
ms.lasthandoff: 08/28/2017

---
# <a name="metadataaddressretval"></a>METADATA_ADDRESS_RETVAL
This structure represents a return value from a method or function.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_RETVAL {  
   _mdToken tokMethod;  
   DWORD    dwCorType;  
   DWORD    dwSigSize;  
   BYTE     rgSig[10];  
} METADATA_ADDRESS_RETVAL;  
```  
  
```csharp  
public struct METADATA_ADDRESS_RETVAL {  
   public int    tokMethod;  
   public uint   dwCorType;  
   public uint   dwSigSize;  
   public byte[] rgSig;  
}  
```  
  
## <a name="terms"></a>Terms  
 tokMethod  
 The ID of the method this return value is for.  
  
 dwCorType  
 The base type of return value. This is a value from the `CorElementType` enumeration defined in the [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] SDK corhdr.h file.  
  
 dwSigSize  
 The size of the return value signature (as stored in `rgSig`).  
  
 rgSig  
 An array of bytes forming the signature of the return value.  
  
## <a name="remarks"></a>Remarks  
 This structure is part of the union in the [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) structure when the `dwKind` field of the `DEBUG_ADDRESS_UNION` structure is set to `ADDRESS_KIND_RETVAL` (a value from the [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) enumeration).  
  
## <a name="requirements"></a>Requirements  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>See Also  
 [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)