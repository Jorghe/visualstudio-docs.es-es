---
title: IntelliSenseHostFlags | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IntellisenseHostFlags
helpviewer_keywords:
- IntelliSense, IntellisenseHostFlags enumeration
- IntellisenseHostFlags enumeration
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2fdc08f6e71a6da718f37e88f40d71df00ee89ab
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49191003"
---
# <a name="intellisensehostflags"></a>IntelliSenseHostFlags
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Especifica las marcas de host de IntelliSense.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
enum IntellisenseHostFlags  
{  
    IHF_READONLYCONTEXT      = 0x00000001  
    IHF_NOSEPARATESUBJECT    = 0x00000002  
    IHF_SINGLELINESUBJECT    = 0x00000004  
    IHF_FORCECOMMITTOCONTEXT = 0x00000008  
    IHF_OVERTYPE             = 0x00000010  
};  
```  
  
#### <a name="parameters"></a>Parámetros  
  
|Miembros|Descripción|  
|-------------|-----------------|  
|`IHF_READONLYCONTEXT`|Búfer de contexto es de solo lectura.|  
|`IHF_NOSEPARATESUBJECT`|No hay texto de asunto. Búfer de contexto contiene el destino de IntelliSense (implica `!IHF_READONLYCONTEXT`).|  
|`IHF_SINGLELINESUBJECT`|Texto del asunto no es capaz varias líneas.|  
|`IHF_FORCECOMMITTOCONTEXT`|Igual a `CanCommitIntoReadOnlyBuffer`.|  
|`IHF_OVERTYPE`|Edición (en el asunto o el contexto) debe realizarse en modo de reemplazo.|  
  
## <a name="requirements"></a>Requisitos  
 SingleFileeditor.idl  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.TextManager.Interop>

