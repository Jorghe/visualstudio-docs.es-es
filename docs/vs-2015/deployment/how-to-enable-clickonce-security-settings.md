---
title: 'Cómo: habilitar la configuración de seguridad de ClickOnce | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- security [Visual Studio], ClickOnce applications
- ClickOnce deployment, security settings
- security settings, ClickOnce deployment
ms.assetid: 73cd3e9d-cd72-4ad2-8cae-94d6bb6b01e0
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 65cba913afdee2379e5f702dda460cea2a33598f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47567977"
---
# <a name="how-to-enable-clickonce-security-settings"></a>Cómo: Habilitar la configuración de seguridad para aplicaciones ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Cómo: habilitar la configuración de seguridad de ClickOnce](https://docs.microsoft.com/visualstudio/deployment/how-to-enable-clickonce-security-settings).  
  
Debe estar habilitada la seguridad de acceso del código para aplicaciones ClickOnce para publicar la aplicación. Esto se realiza automáticamente al publicar una aplicación mediante el Asistente para publicación.  
  
 En algunos casos, habilitar la seguridad de acceso del código puede afectar al rendimiento cuando se compila o depurar la aplicación; en estos casos, es posible que desea deshabilitar temporalmente la configuración de seguridad.  
  
 Configuración de seguridad de ClickOnce puede habilitarse o deshabilitarse en el **seguridad** página de la **Diseñador de proyectos**.  
  
### <a name="to-enable-clickonce-security-settings"></a>Para habilitar a la configuración de seguridad de ClickOnce  
  
1.  Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2.  Haga clic en la pestaña **Seguridad** .  
  
3.  Active la casilla **Habilitar configuración de seguridad de ClickOnce** .  
  
     Ahora puede personalizar la configuración de seguridad de la aplicación en la página de seguridad.  
  
    > [!NOTE]
    >  Esta casilla se activa automáticamente cada vez que se publica la aplicación con el **publicar** asistente.  
  
### <a name="to-disable-clickonce-security-settings"></a>Para deshabilitar la configuración de seguridad de ClickOnce  
  
1.  Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2.  Haga clic en la pestaña **Seguridad** .  
  
3.  Desactive el **Enable ClickOnce Security Settings** casilla de verificación.  
  
     La aplicación se ejecutará con la configuración de seguridad de plena confianza; cualquier configuración de la **seguridad** se omitirá la página.  
  
    > [!NOTE]
    >  Cada vez que se publica la aplicación con el Asistente para publicación, se seleccionará esta casilla de verificación; debe desactivarla nuevo después de cada publicación correcta.  
  
## <a name="see-also"></a>Vea también  
 [Proteger las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Seguridad de acceso del código para aplicaciones ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [Proteger las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md)


