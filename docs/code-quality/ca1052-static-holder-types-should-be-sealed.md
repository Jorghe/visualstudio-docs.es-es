---
title: 'CA1052: Los tipos titulares estáticos deben ser sealed'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- StaticHolderTypesShouldBeSealed
- CA1052
helpviewer_keywords:
- CA1052
- StaticHolderTypesShouldBeSealed
ms.assetid: 51a3165d-781e-4a55-aa0d-ea25fee7d4f2
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2c5d22db6a973947faf228e2e3844d63a916e24e
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/01/2018
ms.locfileid: "47859502"
---
# <a name="ca1052-static-holder-types-should-be-sealed"></a>CA1052: Los tipos titulares estáticos deben ser sealed

|||
|-|-|
|TypeName|StaticHolderTypesShouldBeSealed|
|Identificador de comprobación|CA1052|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo público o protegido contiene sólo miembros estáticos y no se ha declarado con el [sealed](/dotnet/csharp/language-reference/keywords/sealed) ([NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)) modificador.

## <a name="rule-description"></a>Descripción de la regla
 Esta regla supone que un tipo que contiene a sólo miembros estáticos no está diseñado para heredarse, porque el tipo no proporciona ninguna funcionalidad que se puede invalidar en un tipo derivado. Un tipo que no está diseñado para heredarse debería marcarse con el `sealed` modificador para prohibir su uso como un tipo base.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, marque el tipo como `sealed`. Si tiene como destino .NET Framework 2.0 o versiones posteriores, un mejor enfoque es marcar el tipo como `static`. De esta manera, se evita tener que declarar un constructor privado para evitar que la clase que se está creando.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 Suprima una advertencia de esta regla sólo si el tipo está diseñado para heredarse. La ausencia de la `sealed` modificador sugiere que el tipo es útil como tipo base.

## <a name="example-of-a-violation"></a>Ejemplo de una infracción

### <a name="description"></a>Descripción
 El ejemplo siguiente muestra un tipo que infringe la regla.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_1.cs)]
 [!code-vb[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/VisualBasic/ca1052-static-holder-types-should-be-sealed_1.vb)]
 [!code-cpp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CPP/ca1052-static-holder-types-should-be-sealed_1.cpp)]

## <a name="fix-with-the-static-modifier"></a>Corregir con el modificador "Static"

### <a name="description"></a>Descripción
 El ejemplo siguiente muestra cómo corregir una infracción de esta regla, marque el tipo con el `static` modificador.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Design.StaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_2.cs)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1053: Los tipos titulares estáticos no deben tener constructores](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)
