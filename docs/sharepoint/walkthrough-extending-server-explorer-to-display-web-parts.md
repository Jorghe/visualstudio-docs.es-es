---
title: 'Walkthrough: Extending Server Explorer to Display Web Parts | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.prod: visual-studio-dev14
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint commands
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
ms.assetid: 5b1f104a-0eaf-4929-9f1f-d7afcfc8b707
caps.latest.revision: 54
author: kempb
ms.author: kempb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: 54e01f4db7fa98d808696b7ca8d85b1c4c038f02
ms.contentlocale: es-es
ms.lasthandoff: 08/30/2017

---
# <a name="walkthrough-extending-server-explorer-to-display-web-parts"></a>Walkthrough: Extending Server Explorer to Display Web Parts
  In Visual Studio, you can use the **SharePoint Connections** node of **Server Explorer** to view components on SharePoint sites. However, **Server Explorer** doesn't display some components by default. In this walkthrough, you'll extend **Server Explorer** so that it displays the Web Part gallery on each connected SharePoint site.  
  
 This walkthrough demonstrates the following tasks:  
  
-   Creating a Visual Studio extension that extends **Server Explorer** in the following ways:  
  
    -   The extension adds a **Web Part Gallery** node under each SharePoint site node in **Server Explorer**. This new node contains child nodes that represent each Web Part in the Web Part gallery on the site.  
  
    -   The extension defines a new type of node that represents a Web Part instance. This new node type is the basis for the child nodes under the new **Web Part Gallery** node. The new Web Part node type displays information in the **Properties** window about the Web Part that it represents. The node type also includes a custom shortcut menu item that you can use as a starting point for performing other tasks that relate to the Web Part.  
  
-   Creating two custom SharePoint commands that the the extension assembly calls. SharePoint commands are methods that can be called by extension assemblies to use APIs in the server object model for SharePoint. In this walkthrough, you create commands that retrieve Web Part information from the local SharePoint site on the development computer. For more information, see [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
-   Building a Visual Studio Extension (VSIX) package to deploy the extension.  
  
-   Debugging and testing the extension.  
  
> [!NOTE]  
>  For an alternate version of this walkthrough that uses the client object model for SharePoint instead of its server object model, see [Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md).  
  
## <a name="prerequisites"></a>Prerequisites  
 You need the following components on the development computer to complete this walkthrough:  
  
-   Supported editions of Windows, SharePoint and Visual Studio. For more information, see [Requirements for Developing SharePoint Solutions](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   The Visual Studio SDK. This walkthrough uses the **VSIX Project** template in the SDK to create a VSIX package to deploy the project item. For more information, see [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Knowledge of the following concepts is helpful, but not required, to complete the walkthrough:  
  
-   Using the server object model for SharePoint. For more information, see [Using the SharePoint Foundation Server-Side Object Model](http://go.microsoft.com/fwlink/?LinkId=177796).  
  
-   Web Parts in SharePoint solutions. For more information, see [Web Parts Overview](http://go.microsoft.com/fwlink/?LinkId=177803).  
  
## <a name="creating-the-projects"></a>Creating the Projects  
 To complete this walkthrough, you must create three projects:  
  
-   A VSIX project to create the VSIX package to deploy the extension.  
  
-   A class library project that implements the extension. This project must target the .NET Framework 4.5.  
  
-   A class library project that defines the custom SharePoint commands. This project must target the.NET Framework 3.5.  
  
 Start the walkthrough by creating the projects.  
  
#### <a name="to-create-the-vsix-project"></a>To create the VSIX project  
  
1.  Start [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  On the menu bar, choose **File**, **New**, **Project**.  
  
3.  In the  **New Project** dialog box, expand the **Visual C#** or **Visual Basic** nodes, and then choose the **Extensibility** node.  
  
    > [!NOTE]  
    >  The **Extensibility** node is available only if you install the Visual Studio SDK. For more information, see the prerequisites section earlier in this topic.  
  
4.  At the top of the dialog box, choose **.NET Framework 4.5** in the list of versions of the .NET Framework.  
  
5.  Choose the **VSIX Project** template, name the project **WebPartNode**, and then choose the **OK** button.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] adds the **WebPartNode** project to **Solution Explorer**.  
  
#### <a name="to-create-the-extension-project"></a>To create the extension project  
  
1.  In **Solution Explorer**, open the shortcut menu for the solution node, choose **Add**, and then choose **New Project**.  
  
    > [!NOTE]  
    >  In Visual Basic projects, the solution node appears in **Solution Explorer** only when the **Always show solution** check box is selected in the [NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/en-us/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).  
  
2.  In the **New Project** dialog box, expand the **Visual C#** node or **Visual Basic** node, and then the choose **Windows** node.  
  
3.  At the top of the dialog box, choose **.NET Framework 4.5** in the list of versions of the .NET Framework.  
  
4.  In the list of project templates, choose **Class Library**, name the project **WebPartNodeExtension**, and then choose the **OK** button.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] adds the **WebPartNodeExtension** project to the solution and opens the default Class1 code file.  
  
5.  Delete the Class1 code file from the project.  
  
#### <a name="to-create-the-sharepoint-commands-project"></a>To create the SharePoint commands project  
  
1.  In **Solution Explorer**, open the shortcut menu for the solution node, choose **Add**, and then choose **New Project**.  
  
    > [!NOTE]  
    >  In Visual Basic projects, the solution node appears in **Solution Explorer** only when the **Always show solution** check box is selected in the [NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/en-us/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).  
  
2.  In the  **New Project** dialog box, expand the **Visual C#** node or **Visual Basic** node, and then choose the **Windows** node.  
  
3.  At the top of the dialog box, choose **.NET Framework 3.5** in the list of versions of the .NET Framework.  
  
4.  
  
5.  In the list of project templates, choose **Class Library**, name the project **WebPartCommands**, and then choose the **OK** button.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] adds the **WebPartCommands** project to the solution and opens the default Class1 code file.  
  
6.  Delete the Class1 code file from the project.  
  
## <a name="configuring-the-projects"></a>Configuring the Projects  
 Before you write code to create the extension, you must add code files and assembly references, and configure the project settings.  
  
#### <a name="to-configure-the-webpartnodeextension-project"></a>To configure the WebPartNodeExtension project  
  
1.  In the WebPartNodeExtension project, add four code files that have the following names:  
  
    -   SiteNodeExtension  
  
    -   WebPartNodeTypeProvider  
  
    -   WebPartNodeInfo  
  
    -   WebPartCommandIds  
  
2.  Open the shortcut menu for the **WebPartNodeExtension** project, and then choose **Add Reference**.  
  
3.  In the **Reference Manager - WebPartNodeExtension** dialog box, choose the **Framework** tab, and then select the check box for each of the following assemblies:  
  
    -   System.ComponentModel.Composition  
  
    -   System.Windows.Forms  
  
4.  Choose the **Extensions** tab, select the check box for the Microsoft.VisualStudio.SharePoint assembly, and then choose the **OK** button.  
  
5.  In **Solution Explorer**, open the shortcut menu for the **WebPartNodeExtension** project node, and then choose **Properties**.  
  
     The **Project Designer** opens.  
  
6.  Choose the **Application** tab.  
  
7.  In the **Default namespace** box (C#) or **Root namespace** box ([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]), enter **ServerExplorer.SharePointConnections.WebPartNode**.  
  
#### <a name="to-configure-the-webpartcommands-project"></a>To configure the WebPartCommands project  
  
1.  In the WebPartCommands project, add a code file that's named WebPartCommands.  
  
2.  In **Solution Explorer**, open the shortcut menu for the **WebPartCommands** project node, choose **Add**, and then choose **Existing Item**.  
  
3.  In the **Add Existing Item** dialog box, browse to the folder that contains the code files for the WebPartNodeExtension project, and then choose the WebPartNodeInfo and WebPartCommandIds code files.  
  
4.  Choose the arrow next to the **Add** button, and then choose **Add As Link** in the menu that appears.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] adds the code files to the WebPartCommands project as links. As a result, the code files are located in the WebPartNodeExtension project, but the code in the files are also compiled in the WebPartCommands project.  
  
5.  Open the shortcut menu for the **WebPartCommands** project again, and choose **Add Reference**.  
  
6.  In the **Reference Manager - WebPartCommands** dialog box, choose the **Extensions** tab, select the check box for each of the following assemblies, and then choose the **OK** button:  
  
    -   Microsoft.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
7.  In **Solution Explorer**, open the shortcut menu for the **WebPartCommands** project again, and then choose **Properties**.  
  
     The **Project Designer** opens.  
  
8.  Choose the **Application** tab.  
  
9. In the **Default namespace** box (C#) or **Root namespace** box ([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]), enter **ServerExplorer.SharePointConnections.WebPartNode**.  
  
## <a name="creating-icons-for-the-new-nodes"></a>Creating Icons for the New Nodes  
 Create two icons for the **Server Explorer** extension: an icon for the new **Web Part Gallery** node, and another icon for each child Web Part node under the **Web Part Gallery** node. Later in this walkthrough, you will write code that associates these icons with the nodes.  
  
#### <a name="to-create-icons-for-the-nodes"></a>To create icons for the nodes  
  
1.  In **Solution Explorer**, open the shortcut menu for the **WebPartNodeExtension** project, and then choose **Properties**.  
  
2.  The **Project Designer** opens.  
  
3.  Choose the **Resources** tab, and then choose the **This project does not contain a default resources file. Click here to create one** link.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] creates a resource file and opens it in the designer.  
  
4.  At the top of the designer, choose the arrow next to the **Add Resource** menu command, and then choose **Add New Icon** in the menu that appears.  
  
5.  In the **Add New Resource** dialog box, name the new icon **WebPartsNode**, and then choose the **Add** button.  
  
     The new icon opens in the **Image Editor**.  
  
6.  Edit the 16x16 version of the icon so that it has a design that you can easily recognize.  
  
7.  Open the shortcut menu for the 32x32 version of the icon, and then choose **Delete Image Type**.  
  
8.  Repeat steps 5 through 8 to add a second icon to the project resources, and name this icon **WebPart**.  
  
9. In **Solution Explorer**, under the **Resources** folder for the **WebPartNodeExtension** project, open the shortcut menu for **WebPartsNode.ico**.  
  
10. In the **Properties** window, choose the arrow next to **Build Action**, and then choose **Embedded Resource** on the menu that appears.  
  
11. Repeat the last two steps for **WebPart.ico**.  
  
## <a name="adding-the-web-part-gallery-node-to-server-explorer"></a>Adding the Web Part Gallery Node to Server Explorer  
 Create a class that adds the new **Web Part Gallery** node to each SharePoint site node. To add the new node, the class implements the <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> interface. Implement this interface whenever you want to extend the behavior of an existing node in **Server Explorer**, such as adding a child node to a node.  
  
#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>To add the Web Part Gallery node to Server Explorer  
  
1.  In the WebPartNodeExtension project, open the SiteNodeExtension code file, and then paste the following code into it.  
  
    > [!NOTE]  
    >  After you add this code, the project will have some compile errors, but they'll go away when you add code in later steps.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/sitenodeextension.cs#1)]  [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/sitenodeextension.vb#1)]  
  
## <a name="defining-a-node-type-that-represents-a-web-part"></a>Defining a Node Type that Represents a Web Part  
 Create a class that defines a new type of node that represents a Web Part. Visual Studio uses this new node type to display child nodes under the **Web Part Gallery** node. Each child node represents a single Web Part on the SharePoint site.  
  
 To define the new node type, the class implements the <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> interface. Implement this interface whenever you want to define a new type of node in **Server Explorer**.  
  
#### <a name="to-define-the-web-part-node-type"></a>To define the Web Part node type  
  
1.  In the WebPartNodeExtension project, open the WebPartNodeTypeProvder code file, and then paste the following code into it.  
  
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb#2)]  [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodetypeprovider.cs#2)]  
  
## <a name="defining-the-web-part-data-class"></a>Defining the Web Part Data Class  
 Define a class that contains data about a single Web Part on the SharePoint site. Later in this walkthrough, you will create a custom SharePoint command that retrieves data about each Web Part on the site and then assigns the data to instances of this class.  
  
#### <a name="to-define-the-web-part-data-class"></a>To define the Web Part data class  
  
1.  In the WebPartNodeExtension project, open the WebPartNodeInfo code file, and then paste the following code into it.  
  
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodeinfo.vb#3)]  [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodeinfo.cs#3)]  
  
## <a name="defining-the-ids-for-the-sharepoint-command"></a>Defining the IDs for the SharePoint Command  
 Define several strings that identify the custom SharePoint commands. You will implement these commands later in this walkthrough.  
  
#### <a name="to-define-the-command-ids"></a>To define the command IDs  
  
1.  In the WebPartNodeExtension project, open the WebPartCommandIds code file, and then paste the following code into it.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartcommandids.cs#4)]  [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartcommandids.vb#4)]  
  
## <a name="creating-the-custom-sharepoint-commands"></a>Creating the Custom SharePoint Commands  
 Create custom commands that call into the server object model for SharePoint to retrieve data about the Web Parts on the SharePoint site. Each command is a method that has the <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> applied to it.  
  
#### <a name="to-define-the-sharepoint-commands"></a>To define the SharePoint commands  
  
1.  In the WebPartCommands project, open the WebPartCommands code file, and then paste the following code into it.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/CSharp/WebPartNode/WebPartCommands/WebPartCommands.cs#6)]  [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartcommands/webpartcommands.vb#6)]  
  
## <a name="checkpoint"></a>Checkpoint  
 At this point in the walkthrough, all the code for the **Web Part Gallery** node and the SharePoint commands are now in the projects. Build the solution to make sure that both projects compile without errors.  
  
#### <a name="to-build-the-solution"></a>To build the solution  
  
1.  On the menu bar, choose **Build**, **Build Solution**.  
  
    > [!WARNING]  
    >  At this point, the WebPartNode project may have a build error because the VSIX manifest file doesn't have a value for Author. This error will go away when you add a value in later steps.  
  
## <a name="creating-a-vsix-package-to-deploy-the-extension"></a>Creating a VSIX Package to Deploy the Extension  
 To deploy the extension, use the VSIX project in your solution to create a VSIX package. First, configure the VSIX package by modifying the source.extension.vsixmanifest file in the VSIX project. Then, create the VSIX package by building the solution.  
  
#### <a name="to-configure-the-vsix-package"></a>To configure the VSIX package  
  
1.  In **Solution Explorer**, under the WebPartNode project, open the **source.extension.vsixmanifest** file in the manifest editor.  
  
     The source.extension.vsixmanifest file is the basis for the extension.vsixmanifest file that all VSIX packages require. For more information about this file, see [VSIX Extension Schema 1.0 Reference](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  In the **Product Name** box, enter **Web Part Gallery Node for Server Explorer**.  
  
3.  In the **Author** box, enter **Contoso**.  
  
4.  In the **Description** box, enter **Adds a custom Web Part Gallery node to the SharePoint Connections node in Server Explorer. This extension uses a custom SharePoint command to call into the server object model.**  
  
5.  Choose the **Assets** tab of the editor, and then choose the **New** button.  
  
     The **Add New Asset** dialog box appears.  
  
6.  In the **Type** list, choose **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  This value corresponds to the `MefComponent` element in the extension.vsixmanifest file. This element specifies the name of an extension assembly in the VSIX package. For more information, see [NIB: MEFComponent Element (VSX Schema)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
7.  In the  **Source** list, choose **A project in current solution**.  
  
8.  In the **Project** list, choose **WebPartNodeExtension** and then choose the **OK** button.  
  
9. In the manifest editor, choose the **New** button again.  
  
     The **Add New Asset** dialog box appears.  
  
10. In the **Type** box, enter **SharePoint.Commands.v4**.  
  
    > [!NOTE]  
    >  This element specifies a custom extension that you want to include in the Visual Studio extension. For more information, see [Asset Element (VSX Schema)](http://msdn.microsoft.com/en-us/9fcfc098-edc7-484b-9d4c-acd17829d737).  
  
11. In the **Source** list, choose the **A project in current solution** list item.  
  
12. In the **Project** list, choose **WebPartCommands**, and then choose the **OK** button.  
  
13. On the menu bar, choose **Build**, **Build Solution**, and then make sure that the solution compiles without errors.  
  
14. Make sure that the build output folder for the WebPartNode project now contains the WebPartNode.vsix file.  
  
     By default, the build output folder is the ..\bin\Debug folder under the folder that contains your project file.  
  
## <a name="testing-the-extension"></a>Testing the Extension  
 You're now ready to test the new **Web Part Gallery** node in **Server Explorer**. First, start debugging the extension in an experimental instance of Visual Studio. Then, use the new **Web Parts** node in the experimental instance of [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
#### <a name="to-start-debugging-the-extension"></a>To start debugging the extension  
  
1.  Restart [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] with administrative credentials, and then open the WebPartNode solution.  
  
2.  In the WebPartNodeExtension project, open the SiteNodeExtension code file, and then add a breakpoint to the first line of code in the `NodeChildrenRequested` and `CreateWebPartNodes` methods.  
  
3.  Choose the F5 key to start debugging.  
  
     Visual Studio installs the extension to %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web Part Gallery Node Extension for Server Explorer\1.0 and starts an experimental instance of Visual Studio. You will test the project item in this instance of Visual Studio.  
  
#### <a name="to-test-the-extension"></a>To test the extension  
  
1.  In the experimental instance of [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], on the menu bar, choose **View**, **Server Explorer**.  
  
2.  Perform the following steps if the SharePoint site that you want to use for testing doesn't appear under the **SharePoint Connections** node in **Server Explorer**:  
  
    1.  In **Server Explorer**, open the shortcut menu for **SharePoint Connections**, and then choose **Add Connection**.  
  
    2.  In the **Add SharePoint Connection** dialog box, enter the URL for the SharePoint site to which you want to connect, and then choose the **OK** button.  
  
         To specify the SharePoint site on your development computer, enter **http://localhost**.  
  
3.  Expand the site connection node (which displays the URL of your site), and then expand a child site node (for example, **Team Site**).  
  
4.  Verify that the code in the other instance of [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] stops on the breakpoint that you set earlier in the `NodeChildrenRequested` method, and then choose F5 to continue to debug the project.  
  
5.  In the experimental instance of Visual Studio, verify that a new node named **Web Part Gallery** appears under the top-level site node, and then expand the **Web Part Gallery** node.  
  
6.  Verify that the code in the other instance of Visual Studio stops on the breakpoint that you set earlier in the `CreateWebPartNodes` method, and then choose the F5 key to continue to debug the project.  
  
7.  In the experimental instance of Visual Studio, verify that all Web Parts on the connected site appear under the **Web Part Gallery** node in **Server Explorer**.  
  
8.  In **Server Explorer**, open the shortcut menu for one of the Web Parts, and then choose **Properties**.  
  
9. In the instance of [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] that you're debugging, verify that details about the Web Part appear in the **Properties** window.  
  
## <a name="uninstalling-the-extension-from-visual-studio"></a>Uninstalling the Extension from Visual Studio  
 After you finish testing the extension, uninstall the extension from Visual Studio.  
  
#### <a name="to-uninstall-the-extension"></a>To uninstall the extension  
  
1.  In the experimental instance of [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], on the menu bar, choose **Tools**, **Extensions and Updates**.  
  
     The **Extensions and Updates** dialog box opens.  
  
2.  In the list of extensions, choose **Web Part Gallery Node Extension for Server Explorer**, and then choose the **Uninstall** button.  
  
3.  In the dialog box that appears, choose the **Yes** button to confirm that you want to uninstall the extension, and then choose the **Restart Now** button to complete the uninstallation.  
  
4.  Close both instances of Visual Studio (the experimental instance and the instance of Visual Studio in which the WebPartNode solution is open).  
  
## <a name="see-also"></a>See Also  
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)   
 [Image Editor for Icons](/cpp/windows/image-editor-for-icons)   
 [Creating an Icon or Other Image &#40;Image Editor for Icons&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)  
  
  