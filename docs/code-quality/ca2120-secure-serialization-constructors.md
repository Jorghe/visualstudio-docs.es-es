---
title: 'CA2120: Secure serialization constructors | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2120
- SecureSerializationConstructors
helpviewer_keywords:
- SecureSerializationConstructors
- CA2120
ms.assetid: e9989da1-55a0-43f8-9aa9-da86afae3b41
caps.latest.revision: 16
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
ms.openlocfilehash: 8183854c3fce2d3f838435696786355b0e94f5c8
ms.contentlocale: es-es
ms.lasthandoff: 08/30/2017

---
# <a name="ca2120-secure-serialization-constructors"></a>CA2120: Secure serialization constructors
|||  
|-|-|  
|TypeName|SecureSerializationConstructors|  
|CheckId|CA2120|  
|Category|Microsoft.Security|  
|Breaking Change|Breaking|  
  
## <a name="cause"></a>Cause  
 The type implements the <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interface, is not a delegate or interface, and is declared in an assembly that allows partially trusted callers. The type has a constructor that takes a <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> object and a <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> object (the signature of the serialization constructor). This constructor is not secured by a security check, but one or more of the regular constructors in the type is secured.  
  
## <a name="rule-description"></a>Rule Description  
 This rule is relevant for types that support custom serialization. A type supports custom serialization if it implements the <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interface. The serialization constructor is required and is used to de-serialize, or re-create objects that have been serialized using the <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> method. Because the serialization constructor allocates and initializes objects, security checks that are present on regular constructors must also be present on the serialization constructor. If you violate this rule, callers that could not otherwise create an instance could use the serialization constructor to do this.  
  
## <a name="how-to-fix-violations"></a>How to Fix Violations  
 To fix a violation of this rule, protect the serialization constructor with security demands that are identical to those protecting other constructors.  
  
## <a name="when-to-suppress-warnings"></a>When to Suppress Warnings  
 Do not suppress a violation of the rule.  
  
## <a name="example"></a>Example  
 The following example shows a type that violates the rule.  
  
 [!code-csharp[FxCop.Security.SerialCtors#1](../code-quality/codesnippet/CSharp/ca2120-secure-serialization-constructors_1.cs)]  
  
## <a name="related-rules"></a>Related Rules  
 [CA2229: Implement serialization constructors](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2237: Mark ISerializable types with SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
## <a name="see-also"></a>See Also  
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>   
 <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>   
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>