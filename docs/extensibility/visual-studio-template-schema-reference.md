---
title: "Referencia de esquema de plantillas de Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ".vstemplate (archivos)"
  - "plantillas de Visual Studio, esquema"
  - "VSTEMPLATE (archivos)"
ms.assetid: 6f74a2d5-3811-43d6-8b10-eb5823ad8995
caps.latest.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 25
---
# Referencia de esquema de plantillas de Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta sección contiene información sobre los elementos XML comprendidos en los archivos .vstemplate, que son los archivos donde se guardan los metadatos de las plantillas de proyecto y de elementos, así como de los Starter Kits.  
  
 Puede utilizar vstemplate.xsd para validar los archivos .vstemplate personalizados.  Este archivo está disponible en. \\*Visual Studio installation folder*\\Xml\\Schemas\\1033\\vstemplate.xsd.  
  
|Elemento|Elementos secundarios|Atributos|  
|--------------|---------------------------|---------------|  
|[AppliesTo](../extensibility/appliesto-element-visual-studio-templates.md)|Ninguno|Ninguno|  
|[Assembly \(plantilla\)](../extensibility/assembly-element-visual-studio-templates.md)|\-\-|\-\-|  
|[Assembly \(extensión de asistente\)](../extensibility/assembly-element-visual-studio-template-wizard-extension.md)|\-\-|\-\-|  
|[BuildProjectOnload](../extensibility/buildprojectonload-element-visual-studio-templates.md)|\-\-|\-\-|  
|[CreateInPlace](../extensibility/createinplace-visual-studio-templates.md)|\-\-|\-\-|  
|[CreateNewFolder](../extensibility/createnewfolder-element-visual-studio-templates.md)|\-\-|\-\-|  
|[CustomDataSignature](../extensibility/customdatasignature-element-visual-studio-templates.md)|\-\-|\-\-|  
|[CustomParameter](../extensibility/customparameter-element-visual-studio-templates.md)|\-\-|Name<br /><br /> Valor|  
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|CustomParameter|\-\-|  
|[DefaultName](../extensibility/defaultname-element-visual-studio-templates.md)|\-\-|\-\-|  
|[Descripción](../extensibility/description-element-visual-studio-templates.md)|\-\-|Package<br /><br /> ID|  
|[EnableEditOfLocationField](../extensibility/enableeditoflocationfield-element-visual-studio-templates.md)|\-\-|\-\-|  
|[EnableLocationBrowseButton](../extensibility/enablelocationbrowsebutton-element-visual-studio-templates.md)|\-\-|\-\-|  
|[Carpeta](../extensibility/folder-element-visual-studio-project-templates.md)|ProjectItem<br /><br /> Carpeta|Name|  
||\[obsoleto\]|\-\-|  
|[FullClassName](../extensibility/fullclassname-element-visual-studio-template-wizard-extension.md)|\-\-|\-\-|  
|[Hidden](../extensibility/hidden-element-visual-studio-templates.md)|\-\-|\-\-|  
|[Icon](../extensibility/icon-element-visual-studio-templates.md)|\-\-|Package<br /><br /> ID|  
|[LocationField](../extensibility/locationfield-element-visual-studio-project-templates.md)|\-\-|\-\-|  
|[LocationFieldMRUPrefix](../extensibility/locationfieldmruprefix-element-visual-studio-templates.md)|\-\-|\-\-|  
|[MaxFrameworkVersion](../extensibility/maxframeworkversion-element-visual-studio-templates.md)|\-\-|\-\-|  
|[Name](../extensibility/name-element-visual-studio-templates.md)|\-\-|Package<br /><br /> ID|  
|[NumberOfParentCategoriesToRollUp](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)|\-\-|\-\-|  
|[PreviewImage](../extensibility/previewimage-element-visual-studio-templates.md)|\-\-|\-\-|  
|[Proyecto](../extensibility/project-element-visual-studio-templates.md)|Carpeta<br /><br /> ProjectItem|Archivo<br /><br /> TargetFileName<br /><br /> ReplaceParameters|  
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|ProjectTemplateLink<br /><br /> SolutionFolder|\-\-|  
|[ProjectItem \(plantillas de elementos\)](../extensibility/projectitem-element-visual-studio-item-templates.md)|\-\-|Subtipo<br /><br /> CustomTool<br /><br /> ItemType<br /><br /> ReplaceParameters<br /><br /> TargetFileName|  
|[ProjectItem \(plantillas de proyecto\)](../extensibility/projectitem-element-visual-studio-project-templates.md)|\-\-|TargetFileName<br /><br /> ReplaceParameters<br /><br /> OpenInEditor<br /><br /> OpenOrder<br /><br /> OpenInWebBrowser<br /><br /> OpenInHelpBrowser|  
|[ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md)|\-\-|\-\-|  
|[ProjectTemplateLink](../extensibility/projecttemplatelink-element-visual-studio-templates.md)|\-\-|ProjectName|  
|[ProjectType](../extensibility/projecttype-element-visual-studio-templates.md)|\-\-|\-\-|  
|[PromptForSaveOnCreation](../extensibility/promptforsaveoncreation-element-visual-studio-templates.md)|\-\-|\-\-|  
|[ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md)|\-\-|\-\-|  
|[Reference](../extensibility/reference-element-visual-studio-templates.md)|Ensamblado|\-\-|  
|[Referencias](../extensibility/references-element-visual-studio-templates.md)|Reference|\-\-|  
|[RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md)|\-\-|\-\-|  
|[RequiredPlatformVersion](../extensibility/requiredplatformversion-element-visual-studio-templates.md)|\-\-|Versión|  
|[SDKReference](72c8b352-0b7a-42b3-ba5d-2a2d1e90c3)|\-\-|Package|  
|[ShowByDefault](../extensibility/showbydefault-visual-studio-templates.md)|\-\-|\-\-|  
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|ProjectTemplateLink<br /><br /> SolutionFolder|Name|  
|[SortOrder](../extensibility/sortorder-element-visual-studio-templates.md)|\-\-|\-\-|  
|[SupportsCodeSeparation](../extensibility/supportscodeseparation-element-visual-studio-templates.md)|\-\-|\-\-|  
|[SupportsLanguageDropDown](../extensibility/supportslanguagedropdown-element-visual-studio-templates.md)|\-\-|\-\-|  
|[SupportsMasterPage](../extensibility/supportsmasterpage-element-visual-studio-templates.md)|\-\-|\-\-|  
|[TargetPlatformName](../extensibility/targetplatformname-element-visual-studio-templates.md)|RequiredPlatformVersion|\-\-|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|ProjectCollection<br /><br /> Proyecto<br /><br /> Referencias<br /><br /> ProjectItem<br /><br /> CustomParameters|[BuildOnLoad](../extensibility/buildprojectonload-visual-studio-templates.md)|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Name<br /><br /> Descripción<br /><br /> Icon<br /><br /> PreviewImage<br /><br /> ProjectType<br /><br /> ProjectSubType<br /><br /> TemplateID<br /><br /> TemplateGroupID<br /><br /> SortOrder<br /><br /> CreateNewFolder<br /><br /> DefaultName<br /><br /> ProvideDefaultName<br /><br /> PromptForSaveOnCreation<br /><br /> EnableLocationBrowseButton<br /><br /> EnableEditOfLocationField<br /><br /> Hidden<br /><br /> DisplayInParentCategories<br /><br /> LocationFieldMRUPrefix<br /><br /> NumberOfParentCategoriesToRollUp<br /><br /> CreateInPlace<br /><br /> BuildOnLoad<br /><br /> BuildProjectOnload<br /><br /> ShowByDefault<br /><br /> LocationField<br /><br /> SupportsMasterPage<br /><br /> SupportsCodeSeparation<br /><br /> SupportsLanguageDropDown<br /><br /> RequiredFrameworkVersion<br /><br /> FrameworkVersion<br /><br /> MaxFrameworkVersion<br /><br /> CustomDataSignature<br /><br /> TargetPlatformName|\-\-|  
|[TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md)|\-\-|\-\-|  
|[TemplateID](../extensibility/templateid-element-visual-studio-templates.md)|\-\-|\-\-|  
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|TemplateData<br /><br /> TemplateContent<br /><br /> WizardExtension<br /><br /> WizardData|Tipo<br /><br /> Versión|  
|[WizardData](../extensibility/wizarddata-element-visual-studio-templates.md)|\-\-|Name|  
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|Ensamblado<br /><br /> FullClassName|\-\-|  
  
## Vea también  
 [Crear plantillas de proyecto y de elemento personalizadas](../ide/creating-project-and-item-templates.md)   
 [Cómo: Crear Starter Kits](../ide/how-to-create-starter-kits.md)