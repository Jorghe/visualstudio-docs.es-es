---
title: Referencia circular en un argumento de valor no admitida | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5034
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 5d06f0fa-86f5-49d1-8d50-af1759990f43
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d25489065ceece41108a75c9d3763a95e4adb924
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633145"
---
# <a name="circular-reference-in-value-argument-not-supported"></a>Referencia circular en un argumento de valor no admitida
Se ha realizado un intento de invocar `JSON.stringify` con un valor que no es válido. El `value` argumento, matriz u objeto, contiene una referencia circular.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Quite la referencia circular del argumento.  
  
## <a name="example"></a>Ejemplo  
 El código de este ejemplo produce un error de tiempo de ejecución porque `john` tiene una referencia a `mary` y `mary` tiene una referencia a `john`. Para quitar la referencia circular, quitar o sin establecer la propiedad `brother` desde el `mary` objeto o la `sister` propiedad desde el `john` objeto.  
  
```JavaScript  
var john = new Object();  
var mary = new Object();  
john.sister = mary;  
mary.brother = john;  
  
// This line causes a runtime error.  
var error = JSON.stringify(john);  
```  
  
## <a name="see-also"></a>Vea también  
 [Objeto JSON](../../javascript/reference/json-object-javascript.md)   
 [JSON.parse (función)](../../javascript/reference/json-parse-function-javascript.md)   
 [Errores en tiempo de ejecución de JavaScript](../../javascript/reference/javascript-run-time-errors.md)