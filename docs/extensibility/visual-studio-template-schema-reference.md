---
title: Schemareferenz zu Visual Studio-Vorlagen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- VSTEMPLATE files
- Visual Studio templates, schema
- .vstemplate files
ms.assetid: 6f74a2d5-3811-43d6-8b10-eb5823ad8995
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 566a07af35181433b88d5c84ea461e2b7546fe4b
ms.sourcegitcommit: 56ae5032d99d948aae0548ae318ca2bae97ea962
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2018
ms.locfileid: "39586338"
---
# <a name="visual-studio-template-schema-reference"></a>Schemareferenz zu Visual Studio-Vorlage
Dieser Abschnitt enthält Informationen zu XML-Elemente in *VSTEMPLATE* -Dateien, die Dateien handelt, die Metadaten für Projektvorlagen, Elementvorlagen und Starter Kits gespeichert.

 Sie können *vstemplate.xsd* zum Überprüfen von benutzerdefinierten *VSTEMPLATE* Dateien. Diese Datei finden Sie unter *... \\ \<Visual Studio-Installationsordner > \Xml\Schemas\1033\vstemplate.xsd*.

|Element|Untergeordnete Elemente|Attribute|
|-------------|--------------------|----------------|
|[AppliesTo](../extensibility/appliesto-element-visual-studio-templates.md)|Keiner|Keiner|
|[Assembly (Vorlage)](../extensibility/assembly-element-visual-studio-templates.md)|--|--|
|[Assembly (Assistentenerweiterung)](../extensibility/assembly-element-visual-studio-template-wizard-extension.md)|--|--|
|[BuildProjectOnload](../extensibility/buildprojectonload-element-visual-studio-templates.md)|--|--|
|[CreateInPlace](../extensibility/createinplace-visual-studio-templates.md)|--|--|
|[CreateNewFolder](../extensibility/createnewfolder-element-visual-studio-templates.md)|--|--|
|[CustomDataSignature](../extensibility/customdatasignature-element-visual-studio-templates.md)|--|--|
|[CustomParameter](../extensibility/customparameter-element-visual-studio-templates.md)|--|name<br /><br /> Wert|
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|CustomParameter|--|
|[DefaultName](../extensibility/defaultname-element-visual-studio-templates.md)|--|--|
|[Beschreibung](../extensibility/description-element-visual-studio-templates.md)|--|Package<br /><br /> Id|
|[EnableEditOfLocationField](../extensibility/enableeditoflocationfield-element-visual-studio-templates.md)|--|--|
|[EnableLocationBrowseButton](../extensibility/enablelocationbrowsebutton-element-visual-studio-templates.md)|--|--|
|[Ordner](../extensibility/folder-element-visual-studio-project-templates.md)|ProjectItem<br /><br /> Ordner|name|
||[veraltet]|--|
|[FullClassName](../extensibility/fullclassname-element-visual-studio-template-wizard-extension.md)|--|--|
|[Ausgeblendet](../extensibility/hidden-element-visual-studio-templates.md)|--|--|
|[Symbol](../extensibility/icon-element-visual-studio-templates.md)|--|Package<br /><br /> Id|
|[LocationField](../extensibility/locationfield-element-visual-studio-project-templates.md)|--|--|
|[LocationFieldMRUPrefix](../extensibility/locationfieldmruprefix-element-visual-studio-templates.md)|--|--|
|[MaxFrameworkVersion](../extensibility/maxframeworkversion-element-visual-studio-templates.md)|--|--|
|[Name](../extensibility/name-element-visual-studio-templates.md)|--|Package<br /><br /> Id|
|[NumberOfParentCategoriesToRollUp](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)|--|--|
|[PreviewImage](../extensibility/previewimage-element-visual-studio-templates.md)|--|--|
|[Projekt](../extensibility/project-element-visual-studio-templates.md)|Ordner<br /><br /> ProjectItem|Datei<br /><br /> TargetFileName<br /><br /> ReplaceParameters|
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|ProjectTemplateLink<br /><br /> SolutionFolder|--|
|[ProjectItem (Elementvorlagen)](../extensibility/projectitem-element-visual-studio-item-templates.md)|--|SubType<br /><br /> CustomTool<br /><br /> ItemType<br /><br /> ReplaceParameters<br /><br /> TargetFileName|
|[ProjectItem (Projektvorlagen)](../extensibility/projectitem-element-visual-studio-project-templates.md)|--|TargetFileName<br /><br /> ReplaceParameters<br /><br /> OpenInEditor<br /><br /> OpenOrder<br /><br /> OpenInWebBrowser<br /><br /> OpenInHelpBrowser|
|[ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md)|--|--|
|[ProjectTemplateLink](../extensibility/projecttemplatelink-element-visual-studio-templates.md)|--|ProjektName|
|[ProjectType](../extensibility/projecttype-element-visual-studio-templates.md)|--|--|
|[PromptForSaveOnCreation](../extensibility/promptforsaveoncreation-element-visual-studio-templates.md)|--|--|
|[ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md)|--|--|
|[Verweis](../extensibility/reference-element-visual-studio-templates.md)|Assembly|--|
|[Verweise](../extensibility/references-element-visual-studio-templates.md)|Referenz|--|
|[RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md)|--|--|
|[RequiredPlatformVersion](../extensibility/requiredplatformversion-element-visual-studio-templates.md)|--|Version|
|[SDKReference](../extensibility/sdkreference-element-visual-studio-templates.md)|--|Package|
|[ShowByDefault](../extensibility/showbydefault-visual-studio-templates.md)|--|--|
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|ProjectTemplateLink<br /><br /> SolutionFolder|name|
|[SortOrder](../extensibility/sortorder-element-visual-studio-templates.md)|--|--|
|[SupportsCodeSeparation](../extensibility/supportscodeseparation-element-visual-studio-templates.md)|--|--|
|[SupportsLanguageDropDown](../extensibility/supportslanguagedropdown-element-visual-studio-templates.md)|--|--|
|[SupportsMasterPage](../extensibility/supportsmasterpage-element-visual-studio-templates.md)|--|--|
|[TargetPlatformName](../extensibility/targetplatformname-element-visual-studio-templates.md)|RequiredPlatformVersion|--|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|ProjectCollection<br /><br /> Projekt<br /><br /> Verweise<br /><br /> ProjectItem<br /><br /> CustomParameters|[BuildOnLoad](../extensibility/buildprojectonload-visual-studio-templates.md)|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|name<br /><br /> Beschreibung<br /><br /> Symbol<br /><br /> PreviewImage<br /><br /> ProjectType<br /><br /> ProjectSubType<br /><br /> TemplateID<br /><br /> TemplateGroupID<br /><br /> SortOrder<br /><br /> CreateNewFolder<br /><br /> DefaultName<br /><br /> ProvideDefaultName<br /><br /> PromptForSaveOnCreation<br /><br /> EnableLocationBrowseButton<br /><br /> EnableEditOfLocationField<br /><br /> Hidden<br /><br /> DisplayInParentCategories<br /><br /> LocationFieldMRUPrefix<br /><br /> NumberOfParentCategoriesToRollUp<br /><br /> CreateInPlace<br /><br /> BuildOnLoad<br /><br /> BuildProjectOnload<br /><br /> ShowByDefault<br /><br /> LocationField<br /><br /> SupportsMasterPage<br /><br /> SupportsCodeSeparation<br /><br /> SupportsLanguageDropDown<br /><br /> RequiredFrameworkVersion<br /><br /> FrameworkVersion<br /><br /> MaxFrameworkVersion<br /><br /> CustomDataSignature<br /><br /> TargetPlatformName|--|
|[TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md)|--|--|
|[TemplateID](../extensibility/templateid-element-visual-studio-templates.md)|--|--|
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|TemplateData<br /><br /> TemplateContent<br /><br /> WizardExtension<br /><br /> WizardData|Typ<br /><br /> Version|
|[WizardData](../extensibility/wizarddata-element-visual-studio-templates.md)|--|name|
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|Assembly<br /><br /> FullClassName|--|

## <a name="see-also"></a>Siehe auch

- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)