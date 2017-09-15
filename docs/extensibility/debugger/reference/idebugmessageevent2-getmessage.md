---
title: IDebugMessageEvent2::GetMessage | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugMessageEvent2::GetMessage
helpviewer_keywords:
- GetMessage method
- IDebugMessageEvent2::GetMessage method
ms.assetid: 9fca7285-f7f1-422d-8565-92bf0e0db60a
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
ms.openlocfilehash: 190d4dab907e1c0934cb91f7fef6f87989569cad
ms.contentlocale: es-es
ms.lasthandoff: 09/06/2017

---
# <a name="idebugmessageevent2getmessage"></a>IDebugMessageEvent2::GetMessage
Obtiene el mensaje que se mostrará.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetMessage(   
   MESSAGETYPE* pMessageType,  
   BSTR*        pbstrMessage,  
   DWORD*       pdwType,  
   BSTR*        pbstrHelpFileName,  
   DWORD*       pdwHelpId  
);  
```  
  
```csharp  
int GetMessage(   
   out enum_MESSAGETYPE pMessageType,  
   out string           pbstrMessage,  
   out uint             pdwType,  
   out string           pbstrHelpFileName,  
   out uint             dwHelpId  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pMessageType`  
 [out] Devuelve un valor de la [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) enumeración que describe el tipo del mensaje.  
  
 `pbstrMessage`  
 [out] Devuelve el mensaje.  
  
 `pdwType`  
 [out] Devuelve el tipo del mensaje, usando las convenciones de Win32 `MessageBox` función. Consulte la [AfxMessageBox](http://msdn.microsoft.com/Library/d66d0328-cdcc-48f6-96a4-badf089099c8) función para obtener más información.  
  
 `pbstrHelpFileName`  
 [entrada, salida] Devuelve el nombre de archivo de ayuda. Puede ser un null (C++) o un valor vacío (C#) si no hay ningún archivo de ayuda.  
  
 `pdwHelpId`  
 [entrada, salida] Devuelve el identificador de ayuda. Puede ser 0 si no hay ninguna ayuda asociado a este mensaje.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)   
 [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)   
 [AfxMessageBox](http://msdn.microsoft.com/Library/d66d0328-cdcc-48f6-96a4-badf089099c8)