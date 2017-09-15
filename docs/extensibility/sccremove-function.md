---
title: SccRemove Function | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccRemove
helpviewer_keywords:
- SccRemove function
ms.assetid: 20830fdc-c0e9-4a5f-bf60-33f28874442f
caps.latest.revision: 13
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
ms.openlocfilehash: 02a6aedc192bed7dbe0947ceae1ea55d9f50e3ed
ms.contentlocale: es-es
ms.lasthandoff: 08/28/2017

---
# <a name="sccremove-function"></a>SccRemove Function
This function deletes files from the source control system.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
SCCRTN SccRemove(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LPCSTR    lpComment,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 pvContext  
 [in] The source control plug-in context structure.  
  
 hWnd  
 [in] A handle to the IDE window that the source control plug-in can use as a parent for any dialog boxes that it provides.  
  
 nFiles  
 [in] Number of files specified in the `lpFileNames` array.  
  
 lpFileNames  
 [in] Array of fully qualified local path names of files to be removed.  
  
 lpComment  
 [in] The comment to be applied to each file being removed.  
  
 fOptions  
 [in] Command flags (unused).  
  
 pvOptions  
 [in] Source control plug-in-specific options.  
  
## <a name="return-value"></a>Return Value  
 The source control plug-in implementation of this function is expected to return one of the following values:  
  
|Value|Description|  
|-----------|-----------------|  
|SCC_OK|Removal was successful.|  
|SCC_E_FILENOTCONTROLLED|The selected file is not under source control.|  
|SCC_E_OPNOTSUPPORTED|The source control system does not support this operation.|  
|SCC_E_ISCHECKEDOUT|Cannot remove a file because a user currently has it checked out.|  
|SCC_E_ACCESSFAILURE|There was a problem accessing the source control system, probably due to network or contention issues.|  
|SCC_E_NOTAUTHORIZED|The user is not allowed to perform this operation.|  
|SCC_E_NONSPECIFICERROR|Nonspecific failure; file was not removed.|  
|SCC_I_OPERATIONCANCELED|The operation was cancelled before completion.|  
  
## <a name="remarks"></a>Remarks  
 This function removes the files from the source control system but does not delete them from the user's local hard drive.  
  
## <a name="see-also"></a>See Also  
 [Source Control Plug-in API Functions](../extensibility/source-control-plug-in-api-functions.md)