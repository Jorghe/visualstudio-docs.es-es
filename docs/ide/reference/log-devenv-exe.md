---
title: -Log (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3373f1e1a23ae0373a9c49a39a924398ebe143e0
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704777"
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)
Registra toda la actividad en el archivo de registro para solucionar problemas. Este archivo aparece después de haber llamado a `devenv /log` por lo menos una vez. De manera predeterminada, el archivo de registro es:

 *% APPDATA %* \Microsoft\VisualStudio\\*Versión*\ActivityLog.xml

 en que *Versión* es la versión de Visual Studio. Sin embargo, puede especificar una ruta de acceso y un nombre de archivo distintos.

## <a name="syntax"></a>Sintaxis

```cmd
Devenv /log Path\NameOfLogFile
```

## <a name="remarks"></a>Comentarios
 Este modificador debe aparecer al final de la línea de comandos, después del resto de modificadores.

 El registro se escribe para todas las instancias de Visual Studio que se han invocado con el modificador /log. No registra las instancias de Visual Studio que se han invocado sin el modificador.

## <a name="see-also"></a>Vea también

- [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)