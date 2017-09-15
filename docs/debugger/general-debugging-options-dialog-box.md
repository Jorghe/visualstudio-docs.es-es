---
title: General, Debugging, Options Dialog Box | Microsoft Docs
ms.custom: 
ms.date: 05/23/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.options.General
- VS.ToolsOptionsPages.Debugger.General
- VS.ToolsOptionsPages.Debugger.ENC
- vs.debug.options.ENC
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Options dialog box, debugging
ms.assetid: b33aee0b-43c3-4c26-8ed4-bc673f491503
caps.latest.revision: 46
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 9e6c28d42bec272c6fd6107b4baf0109ff29197e
ms.openlocfilehash: 643d1892815822b6616d379d07909731c6100ba4
ms.contentlocale: es-es
ms.lasthandoff: 08/22/2017

---
# <a name="general-debugging-options-dialog-box"></a>General, Debugging, Options Dialog Box
The **Tools > Options > Debugging > General** page lets you set the following options:  
  
**Ask before deleting all breakpoints**  
Requires confirmation before completing the **Delete All Breakpoints** command.  
  
**Break all processes when one process breaks**  
Simultaneously breaks all processes to which the debugger is attached, when a break occurs.  
  
**Break when exceptions cross AppDomain or managed/native boundaries**  
In managed or mixed-mode debugging, the common language runtime can catch exceptions that cross application domain boundaries or managed/native boundaries when the following conditions are true:  
  
1\) When native code calls managed code by using COM Interop and the managed code throws an exception. See [Introduction to COM Interop](/dotnet/articles/visual-basic/programming-guide/com-interop/introduction-to-com-interop).  
  
2\) When managed code running in application domain 1 calls managed code in application domain 2, and the code in application domain 2 throws an exception. See [Programming with Application Domains](/dotnet/articles/framework/app-domains/index).  

3\) When code calls a function by using reflection, and the function throws an exception. See [Reflection](/dotnet/framework/reflection-and-codedom/reflection).  
  
In condition 2 and 3, the exception is sometimes caught by managed code in `mscorlib` instead of the common language runtime. This option does not affect breaking on exceptions caught by `mscorlib`.  
  
**Enable address-level debugging**  
 Enables advanced features for debugging at the address level (the **Disassembly** window, the **Registers** window, and address breakpoints).  
  
- **Show disassembly if source is not available**  
    Automatically shows the **Disassembly** window when you try to debug code for which source is unavailable.  
  
**Enable breakpoint filters**  
Enables you to set filters on breakpoints so that they will affect only specific processes, threads, or computers.  
 
**Use the new Exception Helper**  
Enables the Exception Helper (Visual Studio 2017) that replaces the exception assistant.
  
> [!NOTE]
> For managed code, this option was previously called **Enable the exception assistant** . 
  
**Enable Just My Code**  
The debugger displays and steps into user code ("My Code") only, ignoring system code and other code that is optimized or that does not have debugging symbols.

- **Warn if no user code on launch (Managed only)**  
    When debugging starts with Just My Code enabled, this option warns you if there is no user code ("My Code"). 

**Enable .NET Framework source stepping**  
Allows the debugger to step into .NET Framework source. Enabling this option automatically disables Just My Code .NET Framework symbols will be downloaded to a cache location. You can change the cache location in the **Options** dialog box, **Debugging** category, **Symbols** page.  
  
**Step over properties and operators (Managed only)**  
Prevents the debugger from stepping into properties and operators in managed code.  
  
**Enable property evaluation and other implicit function calls**  
Turns on automatic evaluation of properties and implicit function calls in variables windows and the **QuickWatch** dialog box.  
  
- **Call string conversion function on objects in variables windows (C# and JavaScript only)**  
    Executes an implicit string conversion call when evaluating objects in variables windows. Therefore, that result is displayed as a string instead of the type name. Only applies while debugging in C# code. This setting may be overridden by the DebuggerDisplay attribute (see [Using the DebuggerDisplay Attribute](../debugger/using-the-debuggerdisplay-attribute.md)).  
  
**Enable source server support**  
Tells the Visual Studio debugger to get source files from source servers that implement the SrcSrv (`srcsrv.dll`) protocol. Team Foundation Server and the Debugging Tools for Windows are two source servers that implement the protocol. For more information about SrcSrv setup, see the [SrcSrv](hhttps://msdn.microsoft.com/en-us/library/windows/hardware/ff558791(v=vs.85).aspx) documentation. In addition, see [Specify Symbol (.pdb) and Source Files](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
> [!IMPORTANT]
>  Because reading .pdb files can execute arbitrary code in the files, make sure that you trust the server.  
  
- **Print source server diagnostic messages to the Output window**  
    When source server support is enabled, this setting turns on diagnostic display.  
  
- **Allow source server for partial trust assemblies (Managed only)**  
    When source server support is enabled, this setting overrides the default behavior of not retrieving sources for partial trust assemblies.  

- **Enable source link support**  
    Tells the Visual Studio debugger to download source files for .pdb files that contain Source Link information. For more information about Source Link, see the [Source Link Specification](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/source_link.md).

    > [!IMPORTANT]
    >  Because Source Link will download files using http or https, make sure you trust the .pdb file.  
  
**Highlight entire line for breakpoints and current statement (C++ only)**  
When the debugger highlights a breakpoint or current statement, it highlights the entire line.  
  
**Require source files to exactly match the original version**  
Tells the debugger to verify that a source file matches the version of the source code used to build the executable you are debugging. If the version does not match, you'll be prompted to find a matching source. If a matching source is not found, the source code will not be displayed during debugging. 
  
**Redirect all Output window text to the Immediate window**  
Sends all debugger messages that would ordinarily appear in the **Output** window to the **Immediate** window instead.  
  
**Show raw structure of objects in variables windows**  
Turns off all object structure view customizations. For more information about view customizations, see [Create custom views of .managed objects](../debugger/create-custom-views-of-dot-managed-objects.md).  
  
**Suppress JIT optimization on module load (Managed only)**  
Disables the JIT optimization of managed code when a module is loaded and JIT is compiled while the debugger is attached. Disabling optimization may make it easier to debug some problems, although at the expense of performance. If you are using Just My Code, suppressing JIT optimization can cause non-user code to appear as user code ("My Code").

**Enable JavaScript debugging for ASP.NET (Chrome and IE)** Enables the script debugger for ASP.NET apps. On first use in Chrome, you may need to sign into the browser on first use to enable Chrome extensions that you have installed. Disable this option to revert to legacy behavior.    

**Load dll exports**  
Loads dll export tables. Symbol information from dll export tables can be useful if you are working with Windows messages, Windows procedures (WindowProcs), COM objects, or marshaling, or any dll for which you do not have symbols. Reading dll export information involves some overhead. Therefore, this capability is turned off by default.  
  
To see what symbols are available in the export table of a dll, use `dumpbin /exports`. Symbols are available for any 32-bit system dll. By reading the `dumpbin /exports` output, you can see the exact function name, including non-alphanumeric characters. This is useful for setting a breakpoint on a function. Function names from dll export tables might appear truncated elsewhere in the debugger. The calls are listed in the calling order, with the current function (the most deeply nested) at the top. For more information, see [dumpbin /exports](/cpp/build/reference/dash-exports).  
  
**Show parallel stacks diagram bottom-up**  
Controls the direction in which stacks are displayed in the **Parallel Stacks** window.  
  
**Ignore GPU memory access exceptions if the data written didn't change the value**  
Ignores race conditions that were detected during debugging if the data didn't change. For more information, see [Debugging GPU Code](../debugger/debugging-gpu-code.md).  
  
**Use Managed Compatibility Mode**  
Replaces the default debugging engine with a legacy version to enable these scenarios:  
  
- You are using a .NET Framework language other than C#, VB, or F# that provides its own Expression Evaluator (this includes C++/CLI).  
  
- You want to enable Edit and Continue for C++ projects while mixed mode debugging.  
  
Note that choosing Managed Compatibility mode disables some features that are implemented only in the default debugging engine. 

**Use the legacy C# and VB expression evaluators**  
The debugger will use the Visual Studio 2013 C#/VB expression evaluators instead of the Visual Studio 2015 Roslyn-based expression evaluators.    
  
**Warn when using custom debugger visualizers against potentially unsafe processes (Managed only)**  
Visual Studio warns you when you are using a custom debugger visualizer that is running code in the debuggee process, because it could be running unsafe code.  
  
**Enable Windows debug heap allocator (Native only)**  
Enables the windows debug heap to improve heap diagnostics. Enabling this option will impact debugging performance.  
  
**Enable UI Debugging Tools for XAML**  
The Live Visual Tree and the Live Property Explore windows will appear when you start debugging (F5) a supported project type. For more information, see [Inspect XAML properties while debugging](../debugger/inspect-xaml-properties-while-debugging.md).  
  
- **Preview selected elements in Live Visual Tree**  
    The XAML element whose context is selected is also selected in the **Live Visual Tree** window.  
  
- **Show runtime tools in application**  
    Shows the **Live Visual Tree** commands in a toolbar on the main window of the XAML application that is being debugged. This option was introduced in Visual Studio 2015 Update 2. 

- **Enable XAML Edit and Continue** Allows you to use Edit and Continue feature for XAML code. 
  
**Enable Diagnostic Tools while debugging**  
The **Diagnostic Tools** window appears while you are debugging.
  
**Show elapsed time PerfTip while debugging**  
The code window displays the elapsed time of a given method call when you are debugging.  
  
**Enable Edit and Continue**  
You can use the Edit and Continue functionality while debugging .  
  
- **Enable Native Edit and Continue**  
    You can use the Edit and Continue functionality while debugging native C++ code. For more information, see [Edit and Continue (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).  
  
- **Apply changes on continue (Native only)**  
    Visual Studio automatically compiles and applies any outstanding code changes you have made when continuing the process from a break state. If not selected, you can choose to apply changes using the "Apply Code Changes" item under the Debug menu.  
  
- **Warn about stale code (Native only)**  
    Get warnings about stale code.    

**Show run to click button in editor while debugging** When this option is selected, the [Run to Click](debugger-feature-tour.md#run-to-a-point-in-your-code-quickly-using-the-mouse) button will be shown while debugging.

## <a name="options-supported-in-older-versions-of-visual-studio"></a>Options supported in older versions of Visual Studio

If you are using an older version of Visual Studio, some additional options might be present.

**Enable the exception assistant**  
For managed code, enabled the exception assistant. In Visual Studio 2017, the Exception Helper replaced the exception assistant.

**Unwind the call stack on unhandled exceptions**  
Causes the **Call Stack** window to roll back the call stack to the point before the unhandled exception occurred. 

**Warn if no symbols on launch (native only)**  
Displays a warning dialog box when you try to debug a program for which the debugger has no symbol information. 

**Warn if script debugging is disabled on launch**  
Displays a warning dialog box when the debugger is launched with script debugging disabled.

**Use Native Compatibility Mode**  
When this option is selected, the debugger uses the Visual Studio 2010 native debugger instead of the new native debugger.  
  
You should use this option when you are debugging .NET C++ code, because the new debugging engine does not support evaluating .NET C++ expressions. However, enabling Native Compatibility Mode disables many features that depend on the current debugger implementation to operate. For example, the legacy engine lacks many visualizers for built-in types like `std::string` in Visual Studio 2015 projects.   Please use Visual Studio 2013 projects for the optimal debugging experience in these cases.
  
## <a name="see-also"></a>See Also  
 [Debugging in Visual Studio](../debugger/index.md) [Debugger Feature Tour](../debugger/debugger-feature-tour.md)