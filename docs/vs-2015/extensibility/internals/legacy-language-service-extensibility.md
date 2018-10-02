---
title: Extensibilidad de servicio de lenguaje heredado | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- language services
- Visual Studio, language services
ms.assetid: 2700cd4d-5f68-43fc-b62f-dc80c3f3aa85
caps.latest.revision: 43
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ea9ade367c2e10c228b149385fb0c40e3b803ad1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47580807"
---
# <a name="legacy-language-service-extensibility"></a>Extensibilidad de servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [extensibilidad de servicio de lenguaje heredado](https://docs.microsoft.com/visualstudio/extensibility/internals/legacy-language-service-extensibility).  
  
Un servicio de lenguaje proporciona compatibilidad específica del lenguaje para editar código fuente en el IDE.  
  
 Servicios de lenguaje heredado se implementan como parte de un paquete VSPackage, pero la forma más reciente para implementar características de servicio de lenguaje es usar las extensiones MEF. Para obtener más información acerca de la nueva forma de implementar un servicio de lenguaje, consulte [Editor y extensiones de servicio de lenguaje](../../extensibility/editor-and-language-service-extensions.md).  
  
 Esta sección describe la estructura y la implementación de un servicio de lenguaje heredado.  
  
## <a name="in-this-section"></a>En esta sección  
 [Migración de un servicio de lenguaje heredado](../../extensibility/internals/migrating-a-legacy-language-service.md)  
 Explica cómo actualizar un servicio de lenguaje de Visual Studio 2008 para la versión más reciente.  
  
 [Fundamentos de servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-essentials.md)  
 Proporciona información importante sobre cómo desarrollar servicios de lenguaje para integrar un lenguaje de programación en Visual Studio.  
  
 [Desarrollo de un servicio de lenguaje heredado](../../extensibility/internals/developing-a-legacy-language-service.md)  
 Proporciona vínculos a temas que pueden ayudarle a crear un servicio de lenguaje.  
  
 [Colores de la sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 Proporciona información sobre la compatibilidad con resaltado de sintaxis en un servicio de lenguaje.  
  
 [Implementación de un servicio de lenguaje heredado](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 Proporciona información sobre cómo usar managed package framework (MPF) para implementar un servicio de lenguaje completo en código administrado.  
  
 [Compatibilidad con herramientas de exploración de símbolos](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 Describe las bibliotecas y herramientas que permiten examinar vistas de árbol de símbolos en el IDE.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Editor y extensiones de servicio de lenguaje](../../extensibility/editor-and-language-service-extensions.md)  
 Proporciona información general de los editores de Visual Studio.  
  
 [Compatibilidad del servicio de lenguaje para la depuración](../../extensibility/internals/language-service-support-for-debugging.md)  
 Proporciona información acerca de y un vínculo a la depuración de SDK de Visual Studio, que contiene la información necesaria para crear y personalizar los componentes del depurador para depurar programas.
