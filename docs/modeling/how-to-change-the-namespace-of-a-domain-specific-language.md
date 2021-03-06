---
title: 'Cómo: Cambiar el espacio de nombres de los lenguajes específicos de dominio'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, namespace
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: a237664a30dacf351edc048c82d8c9cdc304aa45
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43775895"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>Cómo: Cambiar el espacio de nombres de los lenguajes específicos de dominio
Puede cambiar el espacio de nombres de un lenguaje específico de dominio. Debe realizar el cambio en el **DSL Explorer**, en las propiedades del proyecto de paquete de Dsl y en la información de ensamblado.

### <a name="to-change-the-namespace-of-a-domain-specific-language"></a>Para cambiar el espacio de nombres de un lenguaje específico de dominio

1.  En **DSL Explorer**, haga clic en el **Dsl** nodo.

2.  En el **propiedades** ventana, cambie el **Namespace** propiedad.

3.  Guarde la solución y transformar las plantillas.

4.  En el **proyecto** menú, haga clic en **Dsl propiedades**.

     Aparecerán las propiedades del proyecto.

5.  Haga clic en la pestaña **Aplicación** .

6.  Cambiar el **espacio de nombres predeterminado** propiedad para el nuevo nombre de espacio de nombres.

7.  Si también desea cambiar el nombre del ensamblado, cambie el **propiedad nombre de ensamblado.**

8.  Si ha cambiado el nombre del ensamblado, abra DslPackage\Package.tt y actualice esta línea:

     `string dslAssembly = "YourDSLassembly.Dsl.dll";`

9. Si ha escrito ningún código personalizado, asegúrese de cambiar las referencias de espacio de nombres y clase en los archivos de código.

10. Restablecer la instancia Experimental de Visual Studio.

    1.  Eliminar **\Users\\**_{su nombre}_**\AppData\Local\Microsoft\VisualStudio\\\*Exp**

    2.  En el Windows **iniciar** menú, elija **todos los programas**, **Microsoft Visual Studio 2010 SDK**, **herramientas**, **restablecer el Instancia experimental**.

11. En el **compilar** menú, elija **recompilar solución**.

## <a name="see-also"></a>Vea también

- [Glosario de las herramientas de lenguajes específicos de dominio](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)