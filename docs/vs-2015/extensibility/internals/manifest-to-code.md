---
title: Manifiesto a código | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17ecacea-397d-4a97-b003-01bd5d56e936
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f0809d44afb6777f26ea6b863ede765d93b5d24f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47566425"
---
# <a name="manifest-to-code"></a>Manifest to Code
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [manifiesto a código](https://docs.microsoft.com/visualstudio/extensibility/internals/manifest-to-code).  
  
El manifiesto de la herramienta de código es una aplicación de consola que toma un archivo .imagemanifest para el servicio de imágenes de Visual Studio y genera un archivo contenedor o archivos para hacer referencia a los valores del manifiesto de la imagen en C++, C#, VB o archivos .vsct para extensiones de Visual Studio. Esta herramienta genera archivos de contenedor que se pueden usar para solicitar las imágenes desde el servicio Visual Studio imagen directamente, o para pasar los valores del manifiesto a través de API si el código no controla cualquiera de su propia interfaz de usuario y la representación.  
  
## <a name="how-to-use-the-tool"></a>Cómo usar la herramienta  
 **Sintaxis**  
  
 / Manifest ManifestToCode:\<archivo de manifiesto de imagen >/Language:\<lenguaje de código > \<Args opcional >  
  
 **Argumentos**  
  
||||  
|-|-|-|  
|**Nombre del conmutador**|**Notas**|**Obligatorio u opcional**|  
|/ manifest|La ruta de acceso al manifiesto de la imagen se utiliza para crear o actualizar el contenedor de código.|Obligatorio|  
|/ Language|El idioma en que se va a generar el contenedor de código.<br /><br /> Los valores válidos: CPP, C++, CS, CSharp, C#, VB o VSCT los valores distinguen mayúsculas de minúsculas.<br /><br /> Para el idioma VSCT se omiten las opciones de opción, /monikerClass, /classAccess y/Namespace.|Obligatorio|  
|/imageIdClass|El nombre de la imageIdClass y el archivo asociado creado por la herramienta. La opción de lenguaje C++, solo los archivos .h se generan.<br /><br /> Valor predeterminado: \<ruta de acceso de manifiesto > \MyImageIds.\< Lang Ext >|Optional|  
|/monikerClass|El nombre de la monikerClass y el archivo asociado creado por la herramienta. La opción de lenguaje C++, solo los archivos .h se generan. Esto se omite para el lenguaje VSCT.<br /><br /> Valor predeterminado: \<ruta de acceso de manifiesto > \MyMonikers.\< Lang Ext >|Optional|  
|/classAccess|El modificador de acceso para el imageIdClass y el monikerClass. Asegúrese de que el modificador de acceso es válido para el idioma especificado. Se omite para la opción de idioma VSCT.<br /><br /> Predeterminado: público|Optional|  
|/ Namespace|El espacio de nombres definido en el contenedor de código. Se omite para la opción de idioma VSCT. Cualquier '.' o '::' son los separadores de espacio de nombres válido, independientemente de la opción de lenguaje elegido.<br /><br /> Predeterminado: MyImages|Optional|  
|/noLogo|Al establecer esta marca detiene la información de producto y copyright de impresión.|Optional|  
|/?|Imprimir información de ayuda.|Optional|  
|/help|Imprimir información de ayuda.|Optional|  
  
 **Ejemplos**  
  
-   ManifestToCode /manifest:D:\MyManifest.imagemanifest/Language: CSharp  
  
-   ManifestToCode /manifest:D:\MyManifest.imagemanifest /language:C++ Namespace/namespace: mi:: Namespace /imageIdClass:MyImageIds /monikerClass:MyMonikers /classAccess:friend  
  
-   ManifestToCode /manifest:D:\MyManifest.imagemanifest /language:VSCT /imageIdClass:MyImageIds  
  
## <a name="notes"></a>Notas  
  
-   Se recomienda usar esta herramienta con los manifiestos de imagen que se generaron mediante el manifiesto de la herramienta de recursos.  
  
-   La herramienta solo examina las entradas de símbolo para generar los contenedores de código. Si un manifiesto de imagen no contiene ningún símbolo, los contenedores de código generado estará vacíos. Si hay una imagen o un conjunto de imágenes en el manifiesto de imagen que no usan los símbolos, se excluirán del contenedor de código.  
  
## <a name="sample-output"></a>Resultados de ejemplo  
 **Contenedores de C#**  
  
 Las clases de un par de Id. de imagen simple y el moniker de imagen para C# será similar del siguiente código:  
  
```csharp  
//-----------------------------------------------------------------------------  
// <auto-generated>  
//     This code was generated by the ManifestToCode tool.  
//     Tool Version: 14.0.15198  
// </auto-generated>  
//-----------------------------------------------------------------------------  
  
using System;  
  
namespace MyImages  
{  
    public static class MyImageIds  
    {  
        public static readonly Guid AssetsGuid = new Guid("{442d8739-efde-46a4-8f29-e3a1e5e7f8b4}");  
  
        public const int MyImage1 = 0;  
        public const int MyImage2 = 1;  
    }  
}  
//-----------------------------------------------------------------------------  
// <auto-generated>  
//     This code was generated by the ManifestToCode tool.  
//     Tool Version: 14.0.15198  
// </auto-generated>  
//-----------------------------------------------------------------------------  
  
using Microsoft.VisualStudio.Imaging.Interop;  
  
namespace MyImages  
{  
    public static class MyMonikers  
    {  
        public static ImageMoniker MyImage1 { get { return new ImageMoniker { Guid = MyImageIds.AssetsGuid, Id = MyImageIds.MyImage1 }; } }  
        public static ImageMoniker MyImage2 { get { return new ImageMoniker { Guid = MyImageIds.AssetsGuid, Id = MyImageIds.MyImage2 }; } }  
    }  
}  
```  
  
 **Contenedores de C++**  
  
 Las clases de un par de Id. de imagen simple y el moniker de imagen para C++ será similar del siguiente código:  
  
```cpp  
//-----------------------------------------------------------------------------  
// <auto-generated>  
//     This code was generated by the ManifestToCode tool.  
//     Tool Version: 14.0.15198  
// </auto-generated>  
//-----------------------------------------------------------------------------  
  
#pragma once  
  
#include <guiddef.h>  
  
namespace MyImages {  
  
class MyImageIds {  
public:  
  
    static const GUID AssetsGuid;  
  
    static const int MyImage1 = 0;  
    static const int MyImage2 = 1;  
  
};  
  
__declspec(selectany) const GUID MyImageIds::AssetsGuid = {0x442d8739,0xefde,0x46a4,{0x8f,0x29,0xe3,0xa1,0xe5,0xe7,0xf8,0xb4}};  
  
}  
//-----------------------------------------------------------------------------  
// <auto-generated>  
//     This code was generated by the ManifestToCode tool.  
//     Tool Version: 14.0.15198  
// </auto-generated>  
//-----------------------------------------------------------------------------  
  
#pragma once  
  
#include "ImageParameters140.h"  
#include "MyImageIds.h"  
  
namespace MyImages {  
  
class MyMonikers {  
public:  
  
    static const ImageMoniker MyImage1;  
    static const ImageMoniker MyImage2;  
  
};  
  
__declspec(selectany) const ImageMoniker MyMonikers::MyImage1 = { MyImageIds::AssetsGuid, MyImageIds::MyImage1 };  
__declspec(selectany) const ImageMoniker MyMonikers::MyImage2 = { MyImageIds::AssetsGuid, MyImageIds::MyImage2 };  
  
}  
```  
  
 **Contenedores de Visual Basic**  
  
 Las clases de un par de Id. de imagen simple y el moniker de imagen para será similar a Visual Basic el siguiente código:  
  
```vb  
' -----------------------------------------------------------------------------  
'  <auto-generated>  
'      This code was generated by the ManifestToCode tool.  
'      Tool Version: 14.0.15198  
'  </auto-generated>  
' -----------------------------------------------------------------------------  
  
Imports System  
  
Namespace MyImages  
  
    Public Module MyImageIds  
  
        Public Shared ReadOnly AssetsGuid As Guid = New Guid("{442d8739-efde-46a4-8f29-e3a1e5e7f8b4}")  
  
        Public Const MyImage1 As Integer = 0  
        Public Const MyImage2 As Integer = 1  
  
    End Module  
  
End Namespace  
' -----------------------------------------------------------------------------  
'  <auto-generated>  
'      This code was generated by the ManifestToCode tool.  
'      Tool Version: 14.0.15198  
'  </auto-generated>  
' -----------------------------------------------------------------------------  
  
Imports Microsoft.VisualStudio.Imaging.Interop  
  
Namespace MyImages  
  
    Public Module MyMonikers  
  
        Public Readonly Property MyImage1  
            Get  
                Return New ImageMoniker With {.Guid = MyImageIds.AssetsGuid, .Id = MyImageIds.MyImage1}  
            End Get  
        End Property  
  
        Public Readonly Property MyImage2  
            Get  
                Return New ImageMoniker With {.Guid = MyImageIds.AssetsGuid, .Id = MyImageIds.MyImage2}  
            End Get  
        End Property  
  
    End Module  
  
End Namespace  
```  
  
 **Contenedor VSCT**  
  
 Un conjunto de identificadores de las imágenes de un archivo .vsct será similar al siguiente:  
  
```xml  
<?xml version='1.0' encoding='utf-8'?>  
<!--  
 [auto-generated]  
     This code was generated by the ManifestToCode tool.  
     Tool Version: 14.0.15198  
 [/auto-generated]  
-->  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable">  
  <Symbols>  
    <GuidSymbol name="AssetsGuid" value="{442d8739-efde-46a4-8f29-e3a1e5e7f8b4}">  
      <IDSymbol name="MyImage1" value="0" />  
      <IDSymbol name="MyImage2" value="1" />  
    </GuidSymbol>  
  </Symbols>  
</CommandTable>  
```
