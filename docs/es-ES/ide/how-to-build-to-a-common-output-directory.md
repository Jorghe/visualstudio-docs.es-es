---
title: 'Cómo: Compilar en un directorio de salida común | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- output directory
- builds [Visual Studio], common directory
- common directory
ms.assetid: 1fcc2c48-07cb-4c4f-9556-36945e7dfc4e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7fccb55bb4c30a6ce18e94667d06f77cc5cb6592
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-build-to-a-common-output-directory"></a>Cómo: Compilar en un directorio de salida común
De manera predeterminada, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] compila cada proyecto en una solución en su propia carpeta dentro de la solución. Puede cambiar las rutas de salida de la compilación de los proyectos para forzar que todos los resultados se almacenen en la misma carpeta.  
  
### <a name="to-place-all-solution-outputs-in-a-common-directory"></a>Para colocar todas las soluciones que se generan en un mismo directorio  
  
1.  Haga clic en un proyecto de la solución.  
  
2.  En el menú **Proyecto**, haga clic en **Propiedades**.  
  
3.  Según el tipo de proyecto, haga clic en la pestaña **Compilar** o en la pestaña **Generar** y establezca la **Ruta de acceso de salida** en una carpeta que se utilizará para todos los proyectos de la solución.  
  
4.  Repita los pasos del 1 al 3 para todos los proyectos de la solución.  
  
## <a name="see-also"></a>Vea también  
 [Compilar y generar](../ide/compiling-and-building-in-visual-studio.md)   
 [Cómo: Cambiar el directorio de salida de compilación](../ide/how-to-change-the-build-output-directory.md)