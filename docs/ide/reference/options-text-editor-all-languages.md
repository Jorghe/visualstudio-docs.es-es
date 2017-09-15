---
title: Opciones, Editor de texto, Todos los lenguajes | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.General
- VS.ToolsOptionsPages.Text_Editor.ResJSON.General
- vs.toolsoptionspages.text_editor.all_languages.scrollbars
helpviewer_keywords:
- Text Editor Options dialog box
- statement completion
- word wrap
- General dialog box
- line numbers
- virtual space
ms.assetid: 49ee7306-9d46-4170-850f-a1716171752d
caps.latest.revision: 20
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 00829d499ae9d5a52e94094eed15b1ae39894075
ms.contentlocale: es-es
ms.lasthandoff: 05/24/2017

---
# <a name="options-text-editor-all-languages"></a>Opciones, Editor de texto, Todos los lenguajes
Este cuadro de diálogo le permite cambiar el comportamiento predeterminado del Editor de código. Estas opciones también se aplican a otros editores basados en el Editor de código, como la vista de origen del diseñador HTML. Para abrir este cuadro de diálogo, seleccione **Opciones** del menú **Herramientas**. En la carpeta **Editor de texto**, expanda la subcarpeta **Todos los lenguajes** y, después, pulse **General**.  
  
> [!CAUTION]
>  Esta página establece las opciones predeterminadas de todos los lenguajes de desarrollo. Recuerde que restablecer una opción en este cuadro de diálogo restablecerá las opciones generales de todos los lenguajes para cualquier elección seleccionada aquí. Para cambiar las opciones del Editor de texto solo de un lenguaje, expanda la subcarpeta de ese lenguaje y seleccione sus páginas de opciones.  
  
 Se muestra una marca atenuada cuando se ha seleccionado una opción en las páginas de opciones generales para algunos lenguajes de programación, pero no para otros.  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para más información, vea [Personalizar el IDE de Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="statement-completion"></a>Finalización de instrucciones  
 Lista de miembros automática  
 Cuando está seleccionada, IntelliSense muestra las listas emergentes de miembros disponibles, propiedades, valores o métodos a medida que escribe en el editor. Pulse cualquier elemento de la lista emergente para insertarlo en el código. Al seleccionar esta opción se habilita la opción **Ocultar miembros avanzados**.  
  
 Ocultar miembros avanzados  
 Cuando está seleccionada, se acortan las listas emergentes de finalización de instrucciones mostrando solo los elementos que más se usan. Los demás elementos se filtran en la lista.  
  
 Información de parámetros  
 Cuando está seleccionada esta casilla, la sintaxis completa del procedimiento o la declaración actual se muestra en el punto de inserción del editor, con todos los parámetros disponibles. El siguiente parámetro que se puede asignar aparecerá en negrita.  
  
## <a name="settings"></a>Configuración  
 Habilitar espacio virtual  
 Cuando esta opción está seleccionada y la casilla **Ajuste de línea** se desactiva, puede hacer clic en cualquier parte más allá del final de una línea en el Editor de código y escribir. Esta característica puede usarse para colocar los comentarios en un lugar coherente junto al código.  
  
 Ajuste de línea  
 Cuando está seleccionada, cualquier parte de una línea que se extienda horizontalmente más allá del área visible del editor aparecerá automáticamente en la siguiente línea. Al activar esta opción se habilita la opción **Mostrar glifos visuales para ajuste de línea**.  
  
> [!NOTE]
>  La característica **Espacio virtual** se desactiva mientras **Ajuste de línea** está activada.  
  
 Mostrar glifos visuales para ajuste de línea  
 Cuando está seleccionada, se muestra un indicador de flecha de retorno en el que una línea larga se ajusta en una segunda línea.  
  
 ![Captura de pantalla de LineBreakSymbol](../../ide/reference/media/linebreak.gif "linebreak")  
  
 Desactive esta casilla si prefiere no mostrar estos indicadores.  
  
> [!NOTE]
>  Estas flechas de aviso no se agregan al código ni se imprimen. Sólo sirven como referencia.  
  
 Aplicar los comandos Cortar o Copiar a las líneas en blanco cuando no haya selección  
 Esta opción establece el comportamiento del editor cuando se coloca el punto de inserción en una línea en blanco, no se selecciona nada y, después, se usa el comando Copiar o Cortar.  
  
-   Cuando se selecciona esta opción, se copia o se corta la línea en blanco. Si después ejecuta Pegar, se inserta una línea en blanco nueva.  
  
-   Cuando esta opción está desactivada, el comando Cortar quita las líneas en blanco. En cambio, los datos del Portapapeles se conservan. Por lo tanto, si después usa el comando Pegar, se pega el contenido copiado en último lugar en el Portapapeles. Si no se ha copiado nada antes, no se pega nada.  
  
 Esta opción no tiene ningún efecto en el comando Copiar o Cortar cuando la línea no está en blanco. Si no se selecciona nada, se copia o se corta la línea completa. Si se pega después, se pega el texto de toda la línea y el carácter de fin de línea.  
  
> [!TIP]
>  Con el fin de poder mostrar indicadores para los espacios, tabuladores y fines de la línea, y distinguir así las líneas con sangría de las que están completamente en blanco, en el menú **Edición** seleccione **Opciones avanzadas** y pulse **Ver espacios en blanco**.  
  
## <a name="display"></a>Pantalla  
 Números de línea  
 Cuando está seleccionada, aparece un número de línea junto a cada línea de código.  
  
> [!NOTE]
>  Estos números de línea no se agregan al código ni se imprimen. Sólo sirven como referencia.  
  
 Habilitar navegación a direcciones URL con un solo clic  
 Si está seleccionada, el cursor del mouse pasa a ser una mano cuando se sitúe sobre una dirección URL en el editor. Puede hacer clic en la dirección URL para mostrar la página indicada en el explorador web.  
  
 Barra de navegación  
 Cuando está seleccionada, muestra la **Barra de navegación** en la parte superior del editor de código. Sus listas desplegables **Objetos** y **Miembros** le permiten elegir un objeto determinado en su código, seleccionar desde sus miembros e ir a la declaración del miembro seleccionado en el Editor de código.  
  
## <a name="see-also"></a>Vea también  
 [Opciones, editor de texto, todos los lenguajes, pestañas](../../ide/reference/options-text-editor-all-languages-tabs.md)   
 [General, Entorno, Opciones (Cuadro de diálogo)](../../ide/reference/general-environment-options-dialog-box.md)   
 [Usar IntelliSense](../../ide/using-intellisense.md)