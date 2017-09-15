---
title: Registering a Tool Window | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tool windows, registering managed
- tool windows, registering
ms.assetid: 8c8c4a24-3da4-497b-9db2-0ddd7cfbfdd2
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 2d0177c027a76e7441543952cf917e4fbfa2a317
ms.contentlocale: es-es
ms.lasthandoff: 08/28/2017

---
# <a name="registering-a-tool-window"></a>Registering a Tool Window
You can register your tool windows using <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> and  <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute>  
  
## <a name="example"></a>Example  
  
```csharp  
  
      [ProvideToolWindow(typeof(PersistedWindowPane), Style = MsVsShell.VsDockStyle.Tabbed, Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")] [ProvideToolWindow(typeof(DynamicWindowPane), PositionX=250, PositionY=250, Width=160, Height=180, Transient=true)] [ProvideToolWindowVisibility(typeof(DynamicWindowPane), /*UICONTEXT_SolutionExists*/"f1536ef8-92ec-443c-9ed7-fdadf150da82")]  
[ProvideMenuResource(1000, 1)]  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("01069CDD-95CE-4620-AC21-DDFF6C57F012")]  
public class PackageToolWindow : Package  
{  
```  
  
 In the code above, the <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> registers the PersistedWindowPane and DynamicWindowPane tool windows with Visual Studio. The persisted tool window is docked and tabbed with **Solution Explorer**, and the dynamic window is given a default starting position and size. The dynamic window is made transient, which indicates that it is not created on startup. This writes a DontForceCreate value in the ToolWindows key in the system registry. For more information, see [Tool Window Display Configuration](../extensibility/tool-window-display-configuration.md).