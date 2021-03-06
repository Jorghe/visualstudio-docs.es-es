---
title: Envío de eventos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 87087a2087591b01170b82c0335e4bbffc579cc2
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/25/2018
ms.locfileid: "39252458"
---
# <a name="send-events"></a>Envío de eventos
El mecanismo para la comunicación entre el depurador y el motor de depuración (DE) es un modelo de eventos en función de DCOM. Los eventos se envían como objetos COM, y cada evento tiene parámetros que especifican:  
  
-   La DE que llama el evento.  
  
-   Una descripción de lo que sucedió.  
  
-   El proceso, el programa y la información de subproceso que identifica el contexto de dónde se produjo el evento. El proceso no se envía para eventos enviados desde un DE.  
  
-   El tipo de evento que indica si el evento es sincrónica o asincrónica.  
  
 Todos los eventos de depuración se envían mediante el método [IDebugEventCallback2::Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="in-this-section"></a>En esta sección  
 [Orígenes de eventos](../../extensibility/debugger/event-sources-visual-studio-sdk.md)  
 Explica los dos orígenes de eventos: el motor de depuración (DE) y la sesión de depuración manager (SDM).  
  
 [Tipos de evento compatibles](../../extensibility/debugger/supported-event-types.md)  
 Describe los tipos de eventos actualmente admitidos: sincrónicas y asincrónicas.  
  
 [Descripciones de evento](../../extensibility/debugger/event-descriptions.md)  
 Define los eventos y los motivos para su uso.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Creación de un motor de depuración personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Describe cómo funciona a DE con el sistema operativo o intérprete para proporcionar servicios de depuración.