---
title: Análisis de código de FxCop y analizadores de FxCop
ms.date: 09/06/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: overview
helpviewer_keywords:
- code analysis FAQ
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: e05dd0e01254bf1222a8a7de497b11ec2a808bfb
ms.sourcegitcommit: b9a32c3d94b19e7344f4872bc026efd3157cf220
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46136371"
---
# <a name="frequently-asked-questions-about-fxcop-and-fxcop-analyzers"></a>Preguntas más frecuentes acerca de FxCop y FxCop analizadores

Puede ser un poco confuso para comprender las diferencias entre heredadas FxCop y FxCop analizadores. En este artículo pretende abordar algunas de las preguntas que pudiera tener.

## <a name="whats-the-difference-between-legacy-fxcop-and-fxcop-analyzers"></a>¿Qué es la diferencia entre heredadas FxCop y FxCop analizadores?

FxCop heredado ejecuta un análisis posterior a la compilación en un ensamblado compilado. Se ejecuta como un archivo ejecutable independiente denominado **FxCopCmd.exe**. Carga el ensamblado compilado, se ejecuta el análisis de código y, a continuación, informa de los resultados FxCopCmd.exe (o *diagnósticos*).

Los analizadores de FxCop se basan en .NET Compiler Platform («Roslyn»). Le [instalarlos como un paquete NuGet](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-nuget-package) que hace referencia el proyecto o solución. Análisis basado en analizadores de FxCop, ejecute el código fuente durante la ejecución del compilador. Los analizadores de FxCop se hospedan dentro del proceso del compilador, ya sea **csc.exe** o **vbc.exe**, y ejecutar el análisis cuando se compila el proyecto. Se notifican los resultados del analizador, junto con los resultados del compilador.

> [!NOTE]
> También puede [instalar analizadores de FxCop como una extensión de Visual Studio](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-vsix). En este caso, los analizadores execute cuando escribe en el editor de código, pero no se ejecutan en tiempo de compilación. Si desea ejecutar analizadores de FxCop como parte de la integración continua (CI), instálelos en su lugar como un paquete NuGet.

## <a name="does-the-run-code-analysis-command-run-fxcop-analyzers"></a>¿El comando Ejecutar análisis de código se ejecuta los analizadores de FxCop?

No. Al seleccionar **analizar** > **ejecutar análisis de código** en Visual Studio 2017, ejecuta el análisis de código estático o FxCop heredado. **Ejecutar análisis de código** no tiene ningún efecto en los analizadores basados en Roslyn, incluidos los analizadores de FxCop basados en Roslyn.

## <a name="does-the-runcodeanalysis-msbuild-project-property-run-analyzers"></a>¿La propiedad de proyecto de msbuild RunCodeAnalysis ejecuta los analizadores?

No. El **RunCodeAnalysis** propiedad en un archivo de proyecto (por ejemplo, *.csproj*) solo se usa para ejecutar FxCop heredado. Se ejecuta una tarea de msbuild posterior a la compilación que invoca **FxCopCmd.exe**. Esto equivale a seleccionar **analizar** > **ejecutar análisis de código** en Visual Studio.

## <a name="so-how-do-i-run-fxcop-analyzers-then"></a>¿Cómo ejecutar analizadores de FxCop, a continuación?

Que se ejecute primero los analizadores de FxCop, [instalar el paquete NuGet](install-fxcop-analyzers.md) para ellos. A continuación, compilar el proyecto o solución en Visual Studio o con msbuild. Aparecerán las advertencias y errores que generan los analizadores de FxCop en el **lista de errores** o la ventana de comandos.

## <a name="see-also"></a>Vea también

- [Información general de los analizadores de .NET Compiler Platform](roslyn-analyzers-overview.md)
- [Introducción a los analizadores](fxcop-analyzers.yml)
- [Instalar analizadores de FxCop](install-fxcop-analyzers.md)
