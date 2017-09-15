---
title: "Compilador de Color VSIX | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 99395da7-ec34-491d-9baa-0590d23283ce
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# Compilador de Color VSIX
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La herramienta compilador de Color de extensión de Visual Studio es una aplicación de consola que toma un archivo .xml que representa los colores de los temas de Visual Studio existentes y convierta en un .pkgdef archivo para que los colores se pueden utilizar en Visual Studio. Dado que es más fácil comparar diferencias entre archivos .xml, esta herramienta es útil para administrar los colores personalizados en el control de código fuente. Se también puede enlazar en entornos de compilación para que el resultado de la compilación es un archivo .pkgdef válido.  
  
 **Esquema XML de tema**  
  
 Un archivo .xml de tema completo tiene el siguiente aspecto:  
  
```xml  
<Themes>  
      <!—one or Theme elements -->  
      <Theme>  
        <!-- one or more Category elements -->  
        <Category>  
          <!-- one or more Color elements -->  
          <Color>  
            <!-- zero or one Background element -->  
            <Background />  
            <!-- zero or one Foreground element -->  
            <Foreground />  
          </Color>  
        </Category>  
      </Theme>  
</Themes>  
```  
  
 **Tema**  
  
 El \< tema> elemento define un tema completo. Un tema debe contener al menos un \< categoría> elemento. Elementos de tema se definen como esta:  
  
```xml  
<Theme Name="name" GUID="guid">  
      <!-- one or more Category elements -->  
</Theme>  
```  
  
|||  
|-|-|  
|**Atributo**|**Definición**|  
|Nombre|[Required] El nombre del tema|  
|GUID|[Required] GUID del tema (deben coincidir con formato de GUID)|  
  
 Al crear colores personalizados para Visual Studio, estos colores deben definirse para los temas siguientes. Si no existe ningún color para un tema determinado, Visual Studio intenta cargar los colores que faltan desde el tema claro.  
  
|||  
|-|-|  
|**Nombre del tema**|**GUID de tema**|  
|Claro|{de3dbbcd-f642-433c-8353-8f1df4370aba}|  
|Oscuro|{1ded0138-47ce-435e-84ef-9ec1f439b749}|  
|Azul|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|  
|Contraste alto|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|  
  
 **Categoría**  
  
 El \< categoría> elemento define una colección de colores en un tema. Nombres de categoría proporcionan agrupaciones lógicas y deben definirse como restrictiva como sea posible. Una categoría debe contener al menos un \< Color> elemento. Elementos de categoría se definen así:  
  
```xml  
<Category Name="name" GUID="guid">  
      <!-- one or more Color elements -->  
 </Category>  
```  
  
|||  
|-|-|  
|**Atributo**|**Definición**|  
|Nombre|[Required] El nombre de la categoría|  
|GUID|[Required] GUID de la categoría (deben coincidir con formato de GUID)|  
  
 **Color**  
  
 El \< Color> elemento define un color para un componente o el estado de la interfaz de Usuario. El esquema de denominación preferido para un color es [tipo de interfaz de Usuario] [estado]. No use la palabra "color", ya que es redundante. Un color debe indicar claramente el tipo de elemento y las situaciones o "state", para el que se aplicará el color. Un color no debe estar vacío y debe contener uno o ambos de un \< fondo> y \< Foreground> elemento. Elementos de color se definen como esta:  
  
```xml  
<Color Name="name">  
        <Background /> <!-- zero or one Background element -->  
        <Foreground /> <!-- zero or one Foreground element -->  
 </Color>  
```  
  
|||  
|-|-|  
|**Atributo**|**Definición**|  
|Nombre|[Required] El nombre del color|  
  
 **Fondo y primer plano**  
  
 El \< fondo> y \< Foreground> elementos definen el valor y el tipo de fondo o de primer plano de un elemento de interfaz de Usuario de un color. Estos elementos no tienen elementos secundarios.  
  
```xml  
<Background Type="type" Source="int" />  
<Foreground Type="type" Source="int" />  
```  
  
|||  
|-|-|  
|**Atributo**|**Definición**|  
|Tipo|[Required] El tipo de color. Puede ser uno de los siguientes:<br /><br /> *CT_INVALID:* el color no es válida o no.<br /><br /> *CT_RAW:* un valor ARGB sin formato.<br /><br /> *CT_COLORINDEX:* NO UTILICE.<br /><br /> *CT_SYSCOLOR:* de SysColor un color del sistema de Windows.<br /><br /> *CT_VSCOLOR:* un color de Visual Studio desde __VSSYSCOLOREX.<br /><br /> *CT_AUTOMATIC:* color automático.<br /><br /> *CT_TRACK_FOREGROUND:* NO UTILICE.<br /><br /> *CT_TRACK_BACKGROUND:* NO UTILICE.|  
|Origen|[Required] El valor del color representado en formato hexadecimal|  
  
 Todos los valores admitidos por la enumeración __VSCOLORTYPE son compatibles con el esquema en el atributo de tipo. Sin embargo, se recomienda que use sólo CT_RAW y CT_SYSCOLOR.  
  
 **Todos juntos**  
  
 Esto es un ejemplo sencillo de un archivo .xml de tema válido:  
  
```xml  
<Themes>  
  <Theme Name="Light" GUID="{de3dbbcd-f642-433c-8353-8f1df4370aba}">  
    <Category Name="MyCategory" GUID="{0A96238B-70CE-4479-9170-EECEAA3FCD58}">  
      <Color Name="MyActiveBorder">  
        <Background Type="CT_RAW" Source="FFCCCEDB" />  
      </Color>  
    </Category>  
  </Theme>  
</Themes>  
```  
  
## <a name="how-to-use-the-tool"></a>Cómo utilizar la herramienta  
 **Sintaxis**  
  
 VsixColorCompiler \< archivo XML> \< archivo PkgDef> \< argumentos opcionales>  
  
 **Argumentos**  
  
||||  
|-|-|-|  
|**Nombre del conmutador**|**Notas**|**Obligatorio u opcional**|  
|Sin nombre (archivo .xml)|Esto es el primer parámetro sin nombre y es la ruta de acceso al archivo XML para convertir.|Obligatorio|  
|Sin nombre (archivo .pkgdef)|Este es el segundo parámetro sin nombre y la ruta de acceso de salida para el archivo .pkgdef generado.<br /><br /> Valor predeterminado: \< nombre de archivo XML>.pkgdef|Optional|  
|/noLogo|Establecer este indicador detiene la información de producto y de copyright de la impresión.|Optional|  
|/?|Imprimir la información de ayuda.|Optional|  
|/help|Imprimir la información de ayuda.|Optional|  
  
 **Ejemplos**  
  
-   VsixColorCompiler D:\xml\colors.xml D:\pkgdef\colors.pkgdef  
  
-   / Nologo VsixColorCompiler D:\xml\colors.xml  
  
## <a name="notes"></a>Notas  
  
-   Esta herramienta requiere que esté instalado la última versión de tiempo de ejecución de VC ++.  
  
-   Se admiten sólo los archivos individuales. No se admite la conversión de forma masiva a través de las rutas de acceso de la carpeta.  
  
## <a name="sample-output"></a>Resultados de ejemplo  
 El archivo .pkgdef generado por la herramienta será similar a la siguiente claves:  
  
```  
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\Environment]  
"Data"=hex:3a,00,00,00,0b,00,00,00,01,00,00,00,c3,d9,4e,62,fd,bd,fa,41,96,c3,7c,82,4e,a3,2e,3d,01,00,00,00,0c,00,00,00,41,63,74,69,76,65,42,6f,72,64,65,72,01,cc,ce,db,ff,01,33,31,24,ff  
  
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\TreeView]  
"Data"=hex:38,00,00,00,0b,00,00,00,01,00,00,00,8e,f0,ec,92,13,8b,f4,4c,99,e9,ae,26,92,38,21,85,01,00,00,00,0a,00,00,00,42,61,63,6b,67,72,6f,75,6e,64,01,f5,f5,f5,ff,01,1e,1e,1e,ff  
```