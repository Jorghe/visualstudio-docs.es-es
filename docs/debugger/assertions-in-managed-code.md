---
title: "Aserciones en el c&#243;digo administrado | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "aserciones, código administrado"
  - "aserciones, efectos secundarios"
  - "Debug.Assert (método)"
  - "Debug.Listeners (propiedad)"
  - "depurar [Visual Studio], aserciones en el código administrado"
  - "depurar código administrado, aserciones"
  - "Trace.Assert (método)"
  - "Trace.Listeners (propiedad)"
ms.assetid: 70ab2522-6486-4076-a1a9-e0f11cd0f3a1
caps.latest.revision: 29
caps.handback.revision: 29
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Aserciones en el c&#243;digo administrado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Una aserción, o instrucción `Assert`, prueba una condición especificada como un argumento de dicha instrucción `Assert`.  Si la condición se evalúa como true, no se produce ninguna acción.  Si la condición se evalúa como false, se produce un error en la aserción.  Si se ejecuta con una compilación de depuración, el programa entra en modo de interrupción.  
  
##  <a name="BKMK_In_this_topic"></a> En este tema  
 [Aserciones en el espacio de nombres System.Diagnostics](#BKMK_Asserts_in_the_System_Diagnostics_Namespace)  
  
 [Debug.Assert (Método)](#BKMK_The_Debug_Assert_method)  
  
 [Efectos secundarios de Debug.Assert](#BKMK_Side_effects_of_Debug_Assert)  
  
 [Requisitos de Trace y Debug](#BKMK_Trace_and_Debug_Requirements)  
  
 [Argumentos de Assert](#BKMK_Assert_arguments)  
  
 [Personalizar el comportamiento de Assert](#BKMK_Customizing_Assert_behavior)  
  
 [Establecer aserciones en archivos de configuración](#BKMK_Setting_assertions_in_configuration_files)  
  
##  <a name="BKMK_Asserts_in_the_System_Diagnostics_Namespace"></a> Aserciones en el espacio de nombres System.Diagnostics  
 En Visual Basic y Visual C\#, puede utilizar el método `Assert` de <xref:System.Diagnostics.Debug> o <xref:System.Diagnostics.Trace>, que están en el espacio de nombres <xref:System.Diagnostics>.  Los métodos de la clase <xref:System.Diagnostics.Debug> no se incluyen en una versión de lanzamiento de su programa, de modo que no aumentan el tamaño ni reducen la velocidad de su código de versión.  
  
 C\+\+ no admite los métodos de la clase <xref:System.Diagnostics.Debug>.  Se puede conseguir el mismo efecto mediante la clase <xref:System.Diagnostics.Trace> con compilación condicional, por ejemplo `#ifdef DEBUG`...  `#endif`.  
  
 [En este tema](#BKMK_In_this_topic)  
  
##  <a name="BKMK_The_Debug_Assert_method"></a> Debug.Assert \(Método\)  
 Utilice el método <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> libremente para probar condiciones que deberían ser true si el código es correcto.  Por ejemplo, suponga que ha escrito una función de división de enteros.  Según las reglas matemáticas, el divisor nunca puede ser cero.  Puede probarlo mediante una aserción:  
  
```vb  
Function IntegerDivide(ByVal dividend As Integer, ByVal divisor As Integer) As Integer  
    Debug.Assert(divisor <> 0)  
    Return CInt(dividend / divisor)  
End Function  
```  
  
```c#  
int IntegerDivide ( int dividend , int divisor )  
    { Debug.Assert ( divisor != 0 );  
        return ( dividend / divisor ); }  
```  
  
 Cuando se ejecuta este código en el depurador, se evalúa la instrucción de aserción, pero en la versión de lanzamiento no se realiza la comparación, de modo que no se produce sobrecarga adicional.  
  
 A continuación se muestra otro ejemplo.  Se utiliza una clase que implementa una cuenta corriente, de la siguiente manera:  
  
```vb  
Dim amount, balance As Double  
balance = savingsAccount.balance  
Debug.Assert(amount <= balance)  
SavingsAccount.Withdraw(amount)  
```  
  
```c#  
float balance = savingsAccount.Balance;  
Debug.Assert ( amount <= balance );  
savingsAccount.Withdraw ( amount );  
```  
  
 Antes de retirar dinero de la cuenta, desea asegurarse de que hay saldo suficiente para cubrir la cantidad que se dispone a retirar.  Puede escribir una aserción para comprobar el saldo:  
  
```vb  
Dim amount, balance As Double  
balance = savingsAccount.balance  
Trace.Assert(amount <= balance)  
SavingsAccount.Withdraw(amount)  
```  
  
```c#  
float balance = savingsAccount.Balance;  
Trace.Assert ( amount <= balance );  
savingsAccount.Withdraw ( amount );  
```  
  
 Tenga en cuenta que las llamadas al método <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> desaparecen cuando se crea una versión de lanzamiento del código.  Esto significa que la llamada que comprueba el saldo desaparecerá en la versión de lanzamiento.  Para resolver este problema, debe reemplazar <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> por <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>, que no desaparece en la versión de lanzamiento:  
  
 A diferencia de las llamadas a <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>, las llamadas a <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> agregan sobrecarga a la versión de lanzamiento.  
  
 [En este tema](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Side_effects_of_Debug_Assert"></a> Efectos secundarios de Debug.Assert  
 Cuando utilice <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>, asegúrese de que el código incluido en `Assert` no cambia el resultado del programa si se quita `Assert`.  De lo contrario, podría producir accidentalmente un error que solo aparezca en la versión de lanzamiento del programa.  Preste especial atención a las aserciones que contengan llamadas a funciones o procedimientos, como en el ejemplo siguiente:  
  
```vb  
' unsafe code  
Debug.Assert (meas(i) <> 0 )  
```  
  
```c#  
// unsafe code  
Debug.Assert (meas(i) != 0 );  
```  
  
 Este uso de <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> parece seguro a primera vista, pero suponga que cada vez que se llama a la función meas se actualiza un contador.  Cuando se compila la versión de lanzamiento, esta llamada a meas se elimina, de manera que no se actualiza el contador.  Este es un ejemplo de una función con efectos secundarios.  Cuando se elimina una llamada a una función que tiene efectos secundarios podría producirse un error que solo aparece en la versión de lanzamiento.  Para evitar tales problemas, no incluya llamadas a funciones en una instrucción <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>.  En su lugar, utilice una variable temporal:  
  
```vb  
temp = meas( i )  
Debug.Assert (temp <> 0)  
```  
  
```c#  
temp = meas( i );  
Debug.Assert ( temp != 0 );  
```  
  
 Aunque se utilice <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>, conviene no colocar llamadas a funciones dentro de una instrucción `Assert`.  Dichas llamadas deben ser seguras, puesto que las instrucciones <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> no se eliminan en la versión de lanzamiento.  No obstante, si se acostumbra a no usar dichas construcciones, la probabilidad de cometer un error al utilizar <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> será menor.  
  
 [En este tema](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Trace_and_Debug_Requirements"></a> Requisitos de Trace y Debug  
 Si crea el proyecto mediante los asistentes de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], el símbolo TRACE se define de forma predeterminada en las configuraciones de Release y Debug.  El símbolo DEBUG se define de forma predeterminada solo en la versión de depuración.  
  
 De lo contrario, para que funcionen los métodos <xref:System.Diagnostics.Trace>, el programa debe tener uno de los siguientes símbolos en la parte superior del archivo de código fuente:  
  
-   `#Const TRACE = True` en Visual Basic  
  
-   `#define TRACE` en Visual C\# y C\+\+  
  
 O bien, el programa se debe compilar con la opción TRACE:  
  
-   `/d:TRACE=True` en Visual Basic  
  
-   `/d:TRACE` en Visual C\# y C\+\+  
  
 Si necesita utilizar los métodos Debug en una versión de lanzamiento de C\# o Visual Basic, debe definir el símbolo DEBUG en la configuración de lanzamiento.  
  
 C\+\+ no admite los métodos de la clase <xref:System.Diagnostics.Debug>.  Se puede conseguir el mismo efecto mediante la clase <xref:System.Diagnostics.Trace> con compilación condicional, por ejemplo `#ifdef DEBUG`...  `#endif`.  Estos símbolos se pueden definir en el cuadro de diálogo **Páginas de propiedades de \<proyecto\>**.  Para obtener más información, vea [Cambiar la configuración del proyecto para una configuración de depuración de Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md) o [Cambiar la configuración del proyecto para una configuración de depuración de C o C\+\+](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
##  <a name="BKMK_Assert_arguments"></a> Argumentos de Assert  
 <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> y <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> pueden utilizar hasta tres argumentos.  El primer argumento, de uso obligatorio, es la condición que se desea comprobar.  Si llama a <xref:System.Diagnostics.Trace.Assert%28System.Boolean%29?displayProperty=fullName> o <xref:System.Diagnostics.Debug.Assert%28System.Boolean%29?displayProperty=fullName> con un único argumento, el método `Assert` comprueba la condición y, si el resultado es false, envía el contenido de la pila de llamadas a la **Ventana de salida**.  En el ejemplo siguiente se muestran <xref:System.Diagnostics.Trace.Assert%28System.Boolean%29?displayProperty=fullName> y <xref:System.Diagnostics.Debug.Assert%28System.Boolean%29?displayProperty=fullName>.  
  
```vb  
Debug.Assert(stacksize > 0)  
Trace.Assert(stacksize > 0)  
```  
  
```c#  
Debug.Assert ( stacksize > 0 );  
Trace.Assert ( stacksize > 0 );   
```  
  
 El segundo y tercer argumento, si existen, deben ser cadenas.  Si llama a <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> o <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> con dos o tres argumentos, el primer argumento es una condición.  El método comprueba la condición y, si el resultado es false, genera la segunda y tercera cadena.  En el ejemplo siguiente se muestran <xref:System.Diagnostics.Debug.Assert%28System.Boolean%2CSystem.String%29?displayProperty=fullName> y <xref:System.Diagnostics.Trace.Assert%28System.Boolean%2CSystem.String%29?displayProperty=fullName> utilizados con dos argumentos:  
  
```vb  
Debug.Assert(stacksize > 0, "Out of stack space")  
Trace.Assert(stacksize > 0, "Out of stack space")  
```  
  
```c#  
Debug.Assert ( stacksize > 0, "Out of stack space" );  
Trace.Assert ( stacksize > 0, "Out of stack space" );  
```  
  
 En el ejemplo siguiente se muestran <xref:System.Diagnostics.Debug.Assert%2A> y <xref:System.Diagnostics.Trace.Assert%2A>.  
  
```vb  
Debug.Assert(stacksize > 0, "Out of stack space. Bytes left:" , Format(size, "G"))  
Trace.Assert(stacksize > 0, "Out of stack space. Bytes left:" , Format(size, "G"))  
Trace.Assert(stacksize > 0, "Out of stack space. Bytes left:", "inctemp failed on third call" )  
```  
  
```c#  
Debug.Assert ( stacksize > 100, "Out of stack space" , "Failed in inctemp" );  
Trace.Assert ( stacksize > 0, "Out of stack space", "Failed in inctemp" );   
```  
  
 [En este tema](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Customizing_Assert_behavior"></a> Personalizar el comportamiento de Assert  
 Si se ejecuta la aplicación en modo de interfaz de usuario, el método `Assert` muestra el cuadro de diálogo **Error de aserción** cuando se produce un error en la condición.  La propiedad <xref:System.Diagnostics.Debug.Listeners%2A> o <xref:System.Diagnostics.Trace.Listeners%2A> controla las acciones que tienen lugar cuando se produce un error en una aserción.  
  
 Puede personalizar el comportamiento del resultado agregando un objeto <xref:System.Diagnostics.TraceListener> a la colección `Listeners`, quitar un objeto <xref:System.Diagnostics.TraceListener> de la colección `Listeners` o reemplazar el método <xref:System.Diagnostics.TraceListener.Fail%2A?displayProperty=fullName> de un objeto `TraceListener` existente para que se comporte de forma diferente.  
  
 Por ejemplo, podría invalidar el método <xref:System.Diagnostics.TraceListener.Fail%2A?displayProperty=fullName> para escribir en un registro de eventos, en lugar de mostrar el cuadro de diálogo **Error de aserción**.  
  
 Para personalizar el resultado de esta forma, el programa debe contener un agente de escucha, heredar de <xref:System.Diagnostics.TraceListener> e invalidar su método <xref:System.Diagnostics.TraceListener.Fail%2A?displayProperty=fullName>.  
  
 Para obtener más información, vea [Trace Listeners](../Topic/Trace%20Listeners.md).  
  
 [En este tema](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Setting_assertions_in_configuration_files"></a> Establecer aserciones en archivos de configuración  
 Se pueden establecer aserciones en el archivo de configuración del programa al igual que en el código.  Para obtener más información, vea <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> o <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>.  
  
## Vea también  
 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>   
 <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>   
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Tracing and Instrumenting Applications](../Topic/Tracing%20and%20Instrumenting%20Applications.md)   
 [How to: Compile Conditionally with Trace and Debug](../Topic/How%20to:%20Compile%20Conditionally%20with%20Trace%20and%20Debug.md)   
 [Tipos de proyectos de C\#, F\# y Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Depurar código administrado](../debugger/debugging-managed-code.md)