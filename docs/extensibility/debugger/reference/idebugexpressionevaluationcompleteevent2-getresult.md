---
title: IDebugExpressionEvaluationCompleteEvent2::GetResult | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugExpressionEvaluationCompleteEvent2::GetResult
helpviewer_keywords:
- IDebugExpressionEvaluationCompleteEvent2::GetResult
ms.assetid: d9ad3e22-b6b2-421e-9a43-6bb8c70d12a9
caps.latest.revision: 10
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
ms.openlocfilehash: 75b7ce59e39c857e9cc506b02c952b5fe531daeb
ms.contentlocale: es-es
ms.lasthandoff: 08/28/2017

---
# <a name="idebugexpressionevaluationcompleteevent2getresult"></a>IDebugExpressionEvaluationCompleteEvent2::GetResult
Gets the result of expression evaluation.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetResult(   
   IDebugProperty2** ppResult  
);  
```  
  
```csharp  
int GetResult(   
   out IDebugProperty2 ppResult  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `ppResult`  
 [out] Returns an [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) object that represents the result of the expression evaluation.  
  
## <a name="return-value"></a>Return Value  
 If successful, returns `S_OK`; otherwise, returns an error code.  
  
## <a name="remarks"></a>Remarks  
 The returned [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) object contains the value of the evaluated expression. Note that this value could be a complex value such as an array but the final result must be a numerical or string value that is displayed to the user.  
  
## <a name="see-also"></a>See Also  
 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)