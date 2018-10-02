---
title: Diseñar advertencias | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.codeanalysis.designrules
helpviewer_keywords:
- design warnings
- managed code analysis warnings, design warnings
- warnings, design
ms.assetid: 34e65a18-560c-423f-814f-519089e318cf
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6f7ba768d27334052c16f13b114d990156bb4a59
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47582958"
---
# <a name="design-warnings"></a>Diseñar advertencias
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [advertencias de diseño](https://docs.microsoft.com/visualstudio/code-quality/design-warnings).  
  
Advertencias compatibles con el cumplimiento para las instrucciones de diseño de .NET Framework de diseño.  
  
## <a name="in-this-section"></a>En esta sección  
  
|Regla|Descripción|  
|----------|-----------------|  
|[CA1000: No declarar miembros estáticos en tipos genéricos](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)|Cuando se llama a un miembro estático de un tipo genérico, se debe especificar el argumento de tipo correspondiente a ese tipo. Cuando se llama a un miembro de instancia genérico que no admite la interferencia, se debe especificar el argumento de tipo para el miembro. En estos dos casos, la sintaxis para especificar el argumento de tipo es diferente y resulta fácil confundirse.|  
|[CA1001: Los tipos que poseen campos descartables deben ser descartables](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Una clase declara e implementa un campo de instancia es de tipo System.IDisposable y la clase no implementa IDisposable. Una clase que declara un campo IDisposable posee indirectamente un recurso no administrado y debería implementar la interfaz IDisposable.|  
|[CA1002: No exponer listas genéricas](../code-quality/ca1002-do-not-expose-generic-lists.md)|System.Collections.Generic.List < (de \<(T >) >) es una colección genérica diseñada para el rendimiento, no para la herencia. Por consiguiente, List no contiene ningún miembro virtual. En su lugar, se debe exponer las colecciones genéricas diseñadas para herencia.|  
|[CA1003: Utilizar instancias genéricas de controlador de eventos](../code-quality/ca1003-use-generic-event-handler-instances.md)|Un tipo contiene un delegado que devuelve void cuya firma contiene dos parámetros (el primero un objeto y el segundo un tipo asignable a EventArgs) y los destinos de ensamblado que contiene [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)].|  
|[CA1004: Los métodos genéricos deben proporcionar un parámetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)|La inferencia es el modo en que se determina el argumento de tipo de un método genérico partiendo del tipo de argumento pasado al método, en lugar de especificar directamente el argumento de tipo. Para habilitar la inferencia, la firma de parámetro de un método genérico debe incluir un parámetro del mismo tipo que el parámetro type del método. En este caso, no es necesario especificar el argumento de tipo. Al utilizar la inferencia para todos los parámetros de tipo, la sintaxis para llamar a métodos de instancia genéricos y es idéntica; Esto simplifica el uso de métodos genéricos.|  
|[CA1005: Evite parámetros excesivos en tipos genéricos](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)|Cuantos más parámetros de tipo contenga un tipo genérico, más difícil resulta saber y recordar qué representa cada uno de ellos. Suele ser evidente con un parámetro de tipo, como en la lista\<T > y en algunos casos con dos parámetros de tipo, como en Dictionary\<TKey, TValue >. Sin embargo, si hay más de dos parámetros de tipo, la dificultad se vuelve demasiado grande para la mayoría de los usuarios.|  
|[CA1006: No anidar tipos genéricos en firmas de miembro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)|Un argumento de tipo anidado es un argumento de tipo que también es un tipo genérico. Para llamar a un miembro cuya firma contenga un argumento de tipo anidado, el usuario debe crear instancias de un tipo genérico y pasar este tipo al constructor de un segundo tipo genérico. El procedimiento y la sintaxis necesarios para ello son complejos, por lo que es preferible evitarlo.|  
|[CA1007: Utilizar valores genéricos cuando sea posible](../code-quality/ca1007-use-generics-where-appropriate.md)|Un método visible externamente contiene un parámetro de referencia de tipo System.Object. El uso de un método genérico permite pasar al método todos los tipos, sujeto a las restricciones que puedan ser de aplicación, sin convertirlos antes al tipo del parámetro de referencia.|  
|[CA1008: Las enumeraciones deben tener un valor igual a cero](../code-quality/ca1008-enums-should-have-zero-value.md)|El valor predeterminado de una enumeración no inicializada, igual que otros tipos de valor, es cero. Una enumeración de atributos de y sin marcadores debería definir a un miembro con el valor de cero para que el valor predeterminado es un valor válido de la enumeración. Si una enumeración a la que se le haya aplicado el atributo FlagsAttribute define un miembro con valor cero, su nombre debe ser "None" para indicar que no se han establecido valores en la enumeración.|  
|[CA1009: Declare los controladores de evento correctamente](../code-quality/ca1009-declare-event-handlers-correctly.md)|Los métodos de control de eventos toman dos parámetros. El primero es de tipo System.Object y se denomina "sender". Éste es el objeto que provocó el evento. El segundo parámetro es de tipo System.EventArgs y se denomina "e". Estos son los datos están asociados a este evento. Los métodos de control de eventos no deben devolver un valor; en el lenguaje de programación C#, esto se indica mediante el tipo de valor devuelto void.|  
|[CA1010: Las colecciones deben implementar la interfaz genérica](../code-quality/ca1010-collections-should-implement-generic-interface.md)|Para ampliar la utilidad de una colección, implemente una de las interfaces de colección genéricas. Entonces podrá utilizar la colección para rellenar tipos de colecciones genéricas.|  
|[CA1011: Considere pasar los tipos base como parámetros](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)|Cuando en una declaración de método se especifica un tipo base como parámetro, cualquier tipo derivado del tipo base puede pasarse al método como el argumento correspondiente. Si la funcionalidad adicional proporcionada por el tipo de parámetro derivado no resulta necesaria, el uso del tipo base permite que el método se utilice más ampliamente.|  
|[CA1012: Los tipos abstractos no deberían tener constructores](../code-quality/ca1012-abstract-types-should-not-have-constructors.md)|Los tipos derivados pueden llamar solo a los constructores de tipos abstractos. Puesto que los constructores públicos crean instancias de un tipo y no se pueden crear instancias de un tipo abstracto, no es correcto diseñar un tipo abstracto con un constructor público.|  
|[CA1013: El operador de sobrecarga es igual que la suma y resta de sobrecarga](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)|Un tipo público o protegido implementa los operadores de suma o resta sin implementar el operador de igualdad.|  
|[CA1014: Marque los ensamblados con CLSCompliantAttribute](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md)|La Common Language Specification (CLS) define las restricciones de nomenclatura, los tipos de datos y las reglas a las que los ensamblados deben ajustarse si se van a utilizar los lenguajes de programación. Un buen diseño determina que todos los ensamblados indican explícitamente la conformidad con CLS mediante el uso de CLSCompliantAttribute. Si este atributo no está presente en un ensamblado, el ensamblado no es conforme.|  
|[CA1016: Marcar los ensamblados con AssemblyVersionAttribute](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|.NET Framework usa el número de versión para identificar de forma única un ensamblado y enlazar a tipos en ensamblados con nombre seguro. El número de versión se utiliza junto con la versión y la directiva del fabricante. De forma predeterminada, las aplicaciones sólo se ejecutan con la versión de ensamblado con la que se compilaron.|  
|[CA1017: Marque los ensamblados con ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)|ComVisibleAttribute determina cómo obtienen acceso los clientes COM al código administrado. Los procedimientos de diseño recomendados dictan que los ensamblados indican explícitamente la visibilidad COM. La visibilidad COM se puede establecer para un ensamblado completo y, a continuación, se puede invalidar para los tipos individuales y los miembros de tipo. Si este atributo no está presente, el contenido del ensamblado es visible para los clientes COM.|  
|[CA1018: Marcar atributos con AttributeUsageAttribute](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)|Cuando defina un atributo personalizado, márquelo utilizando AttributeUsageAttribute para indicar dónde se puede aplicar en el código fuente. El significado de un atributo y el uso que se le va a dar determinará sus ubicaciones válidas en código.|  
|[CA1019: Definir descriptores de acceso para los argumentos de atributo](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)|Los atributos pueden definir argumentos obligatorios que deben especificarse al aplicar el atributo a un destino. Éstos también se denominan argumentos posicionales porque se proporcionan para atribuir constructores como parámetros posicionales. Para cada argumento obligatorio, el atributo debe proporcionar también una propiedad de sólo lectura correspondiente de modo que el valor del argumento se pueda recuperar en tiempo de ejecución. Los atributos también pueden definir argumentos opcionales, que también se denominan argumentos con nombre. Estos argumentos se proporcionan para atribuir constructores por nombre y deben tener una propiedad de lectura/escritura correspondiente.|  
|[CA1020: Evitar espacios de nombres con pocos tipos](../code-quality/ca1020-avoid-namespaces-with-few-types.md)|Asegúrese de que cada uno de los espacios de nombres tiene una organización lógica y que tiene un motivo válido para colocar los tipos en un espacio de nombres apenas lleno.|  
|[CA1021: Evitar parámetros out](../code-quality/ca1021-avoid-out-parameters.md)|Para pasar tipos por referencia (utilizando los parámetros out o ref) es necesario tener experiencia con punteros, saber la diferencia entre los tipos de referencia y los tipos de valor, y controlar métodos con varios valores devueltos. Además, no se suele saber qué diferencia hay entre los parámetros out y ref.|  
|[CA1023: Los indizadores no deben ser multidimensionales](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)|Los indizadores (es decir, las propiedades indizadas) deben utilizar un índice único. Los indizadores multidimensionales pueden reducir de forma significativa la utilidad de la biblioteca.|  
|[CA1024: Utilizar las propiedades donde corresponda](../code-quality/ca1024-use-properties-where-appropriate.md)|Un método público o protegido tiene un nombre que comienza por "Get", no toma ningún parámetro y devuelve un valor que no es una matriz. El método podría ser un buen candidato para convertirse en propiedad.|  
|[CA1025: Reemplaza argumentos repetitivos con una matriz de parámetros](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)|Utilice una matriz de parámetros en lugar de argumentos repetidos si no conoce el número exacto de argumentos y si los argumentos de variable son del mismo tipo o pueden pasarse como si fueran del mismo tipo.|  
|[CA1026: No debería utilizar parámetros predeterminados](../code-quality/ca1026-default-parameters-should-not-be-used.md)|Los métodos que utilizan parámetros predeterminados están permitidos en CLS; sin embargo, CLS permite que los compiladores omitan los valores asignados a estos parámetros. Para seguir utilizando el comportamiento que desea en los lenguajes de programación, los métodos que utilizan parámetros predeterminados deberían reemplazarse con sobrecargas de métodos que proporcionen los parámetros predeterminados.|  
|[CA1027: Marcar enumeraciones con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)|Una enumeración es un tipo de valor que define un conjunto de constantes con nombre relacionadas. Aplique FlagsAttribute a una enumeración cuando se pueda combinar con sentido sus constantes con nombre.|  
|[CA1028: El almacenamiento de la enumeración debe ser de tipo Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)|Una enumeración es un tipo de valor que define un conjunto de constantes con nombre relacionadas. De manera predeterminada, el tipo de datos System.Int32 se utiliza para almacenar el valor constante. Aunque puede cambiar este tipo subyacente, no es necesario o recomendado para la mayoría de los escenarios.|  
|[CA1030: Utilizar eventos cuando sea apropiado](../code-quality/ca1030-use-events-where-appropriate.md)|Esta regla detecta métodos que tienen nombres que normalmente se utilizarían para eventos. Si se llama a un método en respuesta a un cambio de estado claramente definido, un controlador de eventos debe invocar al método. Los objetos que llaman al método deben provocar eventos en lugar de llamar directamente al método.|  
|[CA1031: No capturar los tipos de excepción general](../code-quality/ca1031-do-not-catch-general-exception-types.md)|No se deben capturar excepciones generales. Detectar una excepción más específica, o vuelva a producir la excepción general como la última instrucción del bloque catch.|  
|[CA1032: Implementar constructores de excepción estándar](../code-quality/ca1032-implement-standard-exception-constructors.md)|El error al proporcionar el conjunto completo de constructores puede dificultar el control correcto de las excepciones.|  
|[CA1033: Los tipos secundarios deberían poder llamar a los métodos de interfaz](../code-quality/ca1033-interface-methods-should-be-callable-by-child-types.md)|Un tipo no sellado visible externamente proporciona un método explícito de implementación de una interfaz pública pero no proporciona un método visible externamente alternativo con el mismo nombre.|  
|[CA1034: Los tipos anidados no deben ser visibles](../code-quality/ca1034-nested-types-should-not-be-visible.md)|Los tipos anidados son tipos declarados en el ámbito de otro tipo. Los tipos anidados son útiles para encapsular los detalles de la implementación privada del tipo contenido. Los tipos anidados, utilizados para este propósito, no deben ser visibles externamente.|  
|[CA1035: Las implementaciones de ICollection tienen miembros fuertemente tipados](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)|Esta regla requiere que las implementaciones de ICollection proporcionen miembros fuertemente tipados para que los usuarios no necesiten convertir los argumentos en el tipo Object cuando utilicen la funcionalidad proporcionada por la interfaz. Esta regla supone que el tipo que implementa ICollection lo hace para administrar una colección de instancias de un tipo que es más fuerte que Object.|  
|[CA1036: Invalidar métodos en tipos comparables](../code-quality/ca1036-override-methods-on-comparable-types.md)|Un tipo público o protegido implementa la interfaz System.IComparable. No invalida Object.Equals ni sobrecarga al operador específico del lenguaje para la igualdad, desigualdad, menor que o mayor que.|  
|[CA1038: Los enumeradores deben estar fuertemente tipados](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)|Esta regla requiere que las implementaciones de IEnumerator también proporcionen una versión fuertemente tipada de la propiedad Current para que los usuarios no tengan que convertir el valor devuelto en un tipo inflexible cuando utilicen la funcionalidad proporcionada por la interfaz.|  
|[CA1039: Las listas están fuertemente tipadas](../code-quality/ca1039-lists-are-strongly-typed.md)|Esta regla requiere que las implementaciones de IList proporcionen miembros fuertemente tipados para que los usuarios no necesiten convertir los argumentos en el tipo System.Object cuando utilicen la funcionalidad proporcionada por la interfaz.|  
|[CA1040: Evitar interfaces vacías](../code-quality/ca1040-avoid-empty-interfaces.md)|Las interfaces definen miembros que proporcionan un comportamiento o acuerdo de uso. Cualquier tipo puede adoptar la funcionalidad descrita por la interfaz sin tener en cuenta dónde aparece el tipo en la jerarquía de herencia. Un tipo implementa una interfaz proporcionando las implementaciones para los miembros de la interfaz. Una interfaz vacía no define ningún miembro; por consiguiente, no define ningún contrato que se pueda implementar.|  
|[CA1041: Proporcionar un mensaje ObsoleteAttribute](../code-quality/ca1041-provide-obsoleteattribute-message.md)|Un tipo o miembro se marca con un atributo System.ObsoleteAttribute para el que no se ha especificado su propiedad ObsoleteAttribute.Message. Cuando se compila un tipo o miembro que está marcado con ObsoleteAttribute, se muestra la propiedad Message del atributo, lo que da al usuario información sobre el tipo o miembro obsoleto.|  
|[CA1043: Utilizar argumento integral o de cadena para los indizadores](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)|Los indizadores (es decir, las propiedades indizadas) deben utilizar tipos enteros o de cadena para el índice. Estos tipos se utilizan normalmente para indizar las estructuras de datos y aumentan la utilidad de la biblioteca. El uso del tipo Object debería limitarse a los casos en los que el tipo entero o de cadena no se puede especificar en tiempo de diseño.|  
|[CA1044: Las propiedades no deben ser de solo escritura](../code-quality/ca1044-properties-should-not-be-write-only.md)|Aunque es aceptable y a menudo necesario tener una propiedad de solo lectura, las directrices de diseño prohíben el uso de propiedades de solo escritura. Esto es porque si se deja que un usuario configure un valor, y a continuación se impide que el usuario vea ese valor, no proporciona ninguna seguridad. Además, sin acceso de lectura, no se puede ver el estado de los objetos compartidos, lo que limita su utilidad.|  
|[CA1045: No pasar tipos por referencia](../code-quality/ca1045-do-not-pass-types-by-reference.md)|Para pasar tipos por referencia (utilizando los parámetros out o ref) es necesario tener experiencia con punteros, saber la diferencia entre los tipos de referencia y los tipos de valor, y controlar métodos con varios valores devueltos. Los arquitectos de bibliotecas cuyos diseños están destinados a los usuarios en general no deben esperar que los usuarios dominen el uso de los parámetros out o ref.|  
|[CA1046: No sobrecargar el operador de igualdad en los tipos de referencia](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)|Para los tipos de referencia, la implementación predeterminada del operador de igualdad casi siempre es correcta. De manera predeterminada, dos referencias son iguales sólo si señalan al mismo objeto.|  
|[CA1047: No declarar miembros protegidos en tipos sealed](../code-quality/ca1047-do-not-declare-protected-members-in-sealed-types.md)|Los tipos declaran miembros protegidos para que los tipos heredados puedan obtener acceso o reemplazar el miembro. Por definición, no se puede heredar de tipos sealed, lo que significa que no se puede llamar a los métodos protegidos en tipos sealed.|  
|[CA1048: No declarar miembros virtuales en tipos sealed](../code-quality/ca1048-do-not-declare-virtual-members-in-sealed-types.md)|Los tipos declaran los métodos como virtuales para que los tipos heredados puedan reemplazar la implementación del método virtual. Por definición, no se puede heredar de un tipo sealed. Esto hace que un método virtual en un tipo sealed no tenga sentido.|  
|[CA1049: Los tipos que poseen recursos nativos deben ser descartables](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|Los tipos que se asignan a recursos no administrados deberían implementar IDisposable para permitir que los llamadores liberen estos recursos a petición y reduzcan el período de duración de los objetos que contienen los recursos.|  
|[CA1050: Declare tipos en espacios de nombres](../code-quality/ca1050-declare-types-in-namespaces.md)|Los tipos se declaran dentro de los espacios de nombres para evitar conflictos de nombre y como una forma de organizar los tipos relacionados en una jerarquía de objetos.|  
|[CA1051: No declarar campos de instancia visibles](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)|El uso principal de un campo debe ser como un detalle de implementación. Los campos deben ser privados o internos y deben exponerse utilizando propiedades.|  
|[CA1052: Los tipos titulares estáticos deben ser sealed](../code-quality/ca1052-static-holder-types-should-be-sealed.md)|Un tipo público o protegido contiene a sólo miembros estáticos y no se declara mediante el uso de modificador NotInheritable (Visual Basic) o sealed (C#). Un tipo que no está diseñado para heredarse debería marcarse con el modificador sealed para impedir su uso como tipo base.|  
|[CA1053: Los tipos titulares estáticos no deben tener constructores](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)|Un tipo público o público anidado declara sólo miembros estáticos y tiene un constructor predeterminado público o protegido. El constructor no es necesario puesto que al llamar a los miembros estáticos no se requiere una instancia del tipo. La sobrecarga de la cadena debería llamar a la sobrecarga del identificador URI utilizando el argumento string por motivos de seguridad y protección.|  
|[CA1054: Los parámetros de URI no deben ser cadenas](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)|Si un método toma una representación de cadena de un identificador URI, debe proporcionarse la sobrecarga correspondiente que toma una instancia de la clase URI, que proporciona estos servicios de forma segura.|  
|[CA1055: Los valores devueltos URI no deben ser cadenas](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)|Esta regla supone que el método devuelve un URI. Las representaciones de cadena de identificadores URI tienen tendencia a analizar y codificar errores, por lo que pueden crear puntos vulnerables en la seguridad. La clase System.Uri proporciona estos servicios de una manera segura.|  
|[CA1056: Las propiedades URI no deben ser cadenas](../code-quality/ca1056-uri-properties-should-not-be-strings.md)|Esta regla supone que la propiedad representa un URI. Las representaciones de cadena de identificadores URI tienen tendencia a analizar y codificar errores, por lo que pueden crear puntos vulnerables en la seguridad. La clase System.Uri proporciona estos servicios de una manera segura.|  
|[CA1057: Las sobrecargas URI de cadena llaman a sobrecargas System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)|Un tipo declara sobrecargas de método que solamente se distinguen por la sustitución de un parámetro de cadena por un parámetro System.Uri. La sobrecarga que toma el parámetro de cadena no llama a la sobrecarga que toma el parámetro URI.|  
|[CA1058: Los tipos no deben ampliar ciertos tipos base](../code-quality/ca1058-types-should-not-extend-certain-base-types.md)|Un tipo visible externamente extiende algunos tipos base. Utilice una de las alternativas.|  
|[CA1059: Los miembros no deben exponer algunos tipos concretos](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)|Un tipo concreto es un tipo que tiene una implementación completa y, por consiguiente, se pueden crear instancias de él. Para permitir un uso extendido del miembro, reemplace el tipo concreto por la interfaz sugerida.|  
|[CA1060: Mueva P/Invokes a la clase NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|Los métodos de invocación de plataforma, como aquellos marcados con el <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> o métodos definidos utilizando la palabra clave Declare en [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], tener acceso a código no administrado. Estos métodos deben ser de la clase NativeMethods, UnsafeNativeMethods o SafeNativeMethods.|  
|[CA1061: No oculte métodos de clases base](../code-quality/ca1061-do-not-hide-base-class-methods.md)|Un método de un tipo base está oculto por un método del mismo nombre en un tipo derivado cuando la firma del parámetro del método derivado solo se diferencia por tipos derivados de manera más débil que los tipos correspondientes de la firma del parámetro del método base.|  
|[CA1062: Validar argumentos de métodos públicos](../code-quality/ca1062-validate-arguments-of-public-methods.md)|Todos los argumentos de referencia pasados a métodos visibles externamente se deben comprobar para ver si son null.|  
|[CA1063: Implemente IDisposable correctamente](../code-quality/ca1063-implement-idisposable-correctly.md)|Todos los tipos IDisposable deben implementar el modelo de Dispose correctamente.|  
|[CA1064: Las excepciones deben ser públicas](../code-quality/ca1064-exceptions-should-be-public.md)|Una excepción interna solo se ve dentro de su propio ámbito interno. Cuando la excepción esté fuera del ámbito interno, sólo se podrá usar la excepción base para detectarla. Si la excepción interna se hereda de <xref:System.Exception?displayProperty=fullName>, <xref:System.SystemException?displayProperty=fullName>, o <xref:System.ApplicationException?displayProperty=fullName>, el código externo no tendrá información suficiente para saber qué hacer con la excepción.|  
|[CA1065: No producir excepciones en ubicaciones inesperadas](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|Un método que no se espera que produzca excepciones inicia una excepción.|  
|[CA2210: Los ensamblados deben tener nombres seguros válidos](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md)|El nombre seguro protege los clientes de cargar inconscientemente un ensamblado con el que se ha alterado. Los ensamblados sin nombres seguros sólo deben implementarse en escenarios muy limitados. Si se comparten o se distribuyen ensamblados que no están correctamente firmados, el ensamblado puede manipularse, el Common Language Runtime podría no cargar el ensamblado o el usuario podría deshabilitar la comprobación del equipo.|


