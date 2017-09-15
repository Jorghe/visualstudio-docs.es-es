---
title: "Establecer una imagen de fondo en un diagrama | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e334a24c-8521-4072-b50f-e59158dde145
caps.latest.revision: 2
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 2
---
# Establecer una imagen de fondo en un diagrama
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En el SDK de visualización y modelado de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] puede establecer la imagen de fondo de un diseñador generado usando código personalizado.  
  
## Establecer la imagen de fondo  
  
#### Para establecer una imagen de fondo para un diseñador generado  
  
1.  Copie el archivo de imagen que quiere usar como fondo del diagrama en el directorio Dsl\\Resources para el proyecto actual.  
  
2.  En el **Explorador de soluciones**, haga clic con el botón secundario en la carpeta Dsl\\Resources, elija **Agregar** y, después, haga clic en **Elemento existente**.  
  
3.  En el cuadro de diálogo **Agregar elemento existente**, vaya a la carpeta Dsl\\Resources.  
  
4.  En la lista **Tipo de archivo**, haga clic en **Imagen**.  
  
5.  Haga clic en el archivo de imagen que copió en el directorio y haga clic en **Agregar**.  
  
6.  Haga clic con el botón secundario en Dsl y haga clic en **Propiedades** para abrir las propiedades del proyecto Dsl.  
  
7.  En la pestaña **Recursos**, haga clic en **Este proyecto no contiene ningún archivo de configuración predeterminado. Haga clic aquí para crear uno.**  
  
8.  Agregue el archivo de imagen al archivo de recursos arrastrando la imagen desde el **Explorador de soluciones** a la ventana de recursos.  
  
9. Abra el menú Archivo y haga clic en la opción para guardar las propiedades del proyecto.  
  
10. Compruebe que el archivo Dsl\\Properties\\Resources.resx existe y que tiene el archivo Resources.Designer.cs debajo de él.  
  
11. Si Resources.Designer.cs no está, haga clic en el archivo Resources.resx en el **Explorador de soluciones**.  
  
12. En la ventana **Propiedades**, establezca la propiedad `Custom Tool` en `ResXFileCodeGenerator`.  
  
13. En el **Explorador de soluciones**, haga clic con el botón secundario en el proyecto Dsl, elija **Agregar** y haga clic en **Nueva carpeta**.  
  
14. Asigne a la carpeta el nombre Custom.  
  
15. Haga clic con el botón secundario en la carpeta Custom, elija **Agregar** y haga clic en **Nuevo elemento**.  
  
16. En el cuadro de diálogo **Agregar nuevo elemento**, en la lista **Plantillas**, haga clic en **Archivo de código**.  
  
17. En el cuadro **Nombre**, escriba `BackgroundImage.cs` y haga clic en **Agregar**.  
  
18. Copie el código siguiente en el archivo BackgroundImage.cs y ajuste el espacio de nombres, el nombre de la clase de diagrama y el nombre del recurso de archivo de imagen.  
  
     Reemplace "MyDiagramClass" por el nombre de la clase parcial de diagrama definida en Dsl\\GeneratedCode\\Diagrams.cs.  También puede recuperar el espacio de nombres correcto del archivo Dsl\\GeneratedCode\\Diagrams.cs.  
  
    ```  
    using System;  
    using Microsoft.VisualStudio.Modeling.Diagrams;  
  
    // Fix the namespace:  
    namespace Fabrikam.MyLanguage  
    {  
      // Fix the Diagram Class name - get it from GeneratedCode\Diagram.cs  
  
      public partial class Language29Diagram  
      {  
        protected override void InitializeInstanceResources()  
        {  
          // Fix the Resources namespace and the Image resource name:  
          ImageField backgroundField = new ImageField("background",  
              Fabrikam.MyLanguage.Properties.Resources.MyPicture);  
  
          backgroundField.DefaultFocusable = false;  
          backgroundField.DefaultSelectable = false;  
          backgroundField.DefaultVisibility = true;  
          backgroundField.DefaultUnscaled = false;  
  
          shapeFields.Add(backgroundField);  
  
          backgroundField.AnchoringBehavior  
            .SetTopAnchor(AnchoringBehavior.Edge.Top, 0.01);  
          backgroundField.AnchoringBehavior  
            .SetLeftAnchor(AnchoringBehavior.Edge.Left, 0.01);  
          backgroundField.AnchoringBehavior  
            .SetRightAnchor(AnchoringBehavior.Edge.Right, 0.01);  
          backgroundField.AnchoringBehavior  
            .SetBottomAnchor(AnchoringBehavior.Edge.Bottom, 0.01);  
  
          base.InitializeInstanceResources();  
        }  
      }  
    }  
    ```  
  
     Para más información sobre cómo personalizar el modelo usando código de programa, vea [Navegar y actualizar un modelo en el código del programa](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
## Vea también  
 [Definir formas y conectores](../modeling/defining-shapes-and-connectors.md)   
 [Personalizar campos de imagen y texto](../modeling/customizing-text-and-image-fields.md)   
 [Navegar y actualizar un modelo en el código del programa](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Escribir código para personalizar un lenguaje específico de dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)