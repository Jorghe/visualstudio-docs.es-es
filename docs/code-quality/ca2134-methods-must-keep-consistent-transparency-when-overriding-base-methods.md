---
title: 'CA2134: Methods must keep consistent transparency when overriding base methods | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2134
ms.assetid: 3b17e487-0326-442e-90e1-dc0ba9cdd3f2
caps.latest.revision: 9
author: stevehoag
ms.author: shoag
manager: wpickett
translation.priority.ht:
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
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: d4ef9c4baadcdc6c26906664b24827948de1c5c9
ms.contentlocale: es-es
ms.lasthandoff: 08/30/2017

---
# <a name="ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods"></a>CA2134: Methods must keep consistent transparency when overriding base methods
|||  
|-|-|  
|TypeName|MethodsMustOverrideWithConsistentTransparency|  
|CheckId|CA2134|  
|Category|Microsoft.Security|  
|Breaking Change|Breaking|  
  
## <a name="cause"></a>Cause  
 This rule fires when a method marked with the <xref:System.Security.SecurityCriticalAttribute> overrides a method that is transparent or marked with the <xref:System.Security.SecuritySafeCriticalAttribute>. The rule also fires when a method that is transparent or marked with the <xref:System.Security.SecuritySafeCriticalAttribute> overrides a method that is marked with a <xref:System.Security.SecurityCriticalAttribute>.  
  
 The rule is applied when overriding a virtual method or implementing an interface.  
  
## <a name="rule-description"></a>Rule Description  
 This rule fires on attempts to change the security accessibility of a method further up the inheritance chain. For example, if a virtual method in a base class is transparent or safe-critical, then the derived class must override it with a transparent or safe-critical method. Conversely, if the virtual is security critical, the derived class must override it with a security critical method. The same rule applies for implementing interface methods.  
  
 Transparency rules are enforced when the code is JIT compiled instead of at runtime, so that the transparency calculation does not have dynamic type information. Therefore, the result of the transparency calculation must be able to be determined solely from the static types being JIT-compiled, regardless of the dynamic type.  
  
## <a name="how-to-fix-violations"></a>How to Fix Violations  
 To fix a violation of this rule, change the transparency of the method that is overriding a virtual method or implementing an interface to match the transparency of the virtual or interface method.  
  
## <a name="when-to-suppress-warnings"></a>When to Suppress Warnings  
 Do not suppress warnings from this rule. Violations of this rule will result in a runtime <xref:System.TypeLoadException> for assemblies that use level 2 transparency.  
  
## <a name="examples"></a>Examples  
  
### <a name="code"></a>Code  
 [!code-csharp[FxCop.Security.CA2134.MethodsMustOverrideWithConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods_1.cs)]  
  
## <a name="see-also"></a>See Also  
 [Security-Transparent Code, Level 2](http://msdn.microsoft.com/Library/4d05610a-0da6-4f08-acea-d54c9d6143c0)