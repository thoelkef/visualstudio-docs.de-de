---
title: Visual Studio-Vorlagenschemareferenz | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- VSTEMPLATE files
- Visual Studio templates, schema
- .vstemplate files
ms.assetid: 6f74a2d5-3811-43d6-8b10-eb5823ad8995
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 49e41431938eed0078f6cbb241d3d62812899942
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697974"
---
# <a name="visual-studio-template-schema-reference"></a>Visual Studio-Vorlagenschemareferenz
Dieser Abschnitt enthält Informationen zu XML-Elementen in *.vstemplate-Dateien,* bei denen es sich um Dateien handelt, die Metadaten für Projektvorlagen, Elementvorlagen und StarterKits speichern.

 Sie können *vstemplate.xsd* verwenden, um benutzerdefinierte *.vstemplate-Dateien* zu überprüfen. Diese Datei ist unter *.. Visual \\Studio-Installationsordner>-Xml-Schemas-1033-vstemplate.xsd \<*.

|Element|Untergeordnete Elemente|Attribute|
|-------------|--------------------|----------------|
|[Appliesto](../extensibility/appliesto-element-visual-studio-templates.md)|Keine|Keine|
|[Assembly (Vorlage)](../extensibility/assembly-element-visual-studio-templates.md)|--|--|
|[Assembly (Assistentenerweiterung)](../extensibility/assembly-element-visual-studio-template-wizard-extension.md)|--|--|
|[BuildProjectOnload](../extensibility/buildprojectonload-element-visual-studio-templates.md)|--|--|
|[CreateInPlace](../extensibility/createinplace-visual-studio-templates.md)|--|--|
|[CreateNewFolder](../extensibility/createnewfolder-element-visual-studio-templates.md)|--|--|
|[CustomDataSignature](../extensibility/customdatasignature-element-visual-studio-templates.md)|--|--|
|[CustomParameter](../extensibility/customparameter-element-visual-studio-templates.md)|--|name<br /><br /> Wert|
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|CustomParameter|--|
|[DefaultName](../extensibility/defaultname-element-visual-studio-templates.md)|--|--|
|[Beschreibung](../extensibility/description-element-visual-studio-templates.md)|--|Paket<br /><br /> id|
|[EnableEditOfLocationField](../extensibility/enableeditoflocationfield-element-visual-studio-templates.md)|--|--|
|[EnableLocationBrowseButton](../extensibility/enablelocationbrowsebutton-element-visual-studio-templates.md)|--|--|
|[Ordner](../extensibility/folder-element-visual-studio-project-templates.md)|ProjectItem<br /><br /> Ordner|name|
||[veraltet]|--|
|[FullClassName](../extensibility/fullclassname-element-visual-studio-template-wizard-extension.md)|--|--|
|[Versteckte](../extensibility/hidden-element-visual-studio-templates.md)|--|--|
|[Symbol](../extensibility/icon-element-visual-studio-templates.md)|--|Paket<br /><br /> id|
|[LocationField](../extensibility/locationfield-element-visual-studio-project-templates.md)|--|--|
|[LocationFieldMRUPrefix](../extensibility/locationfieldmruprefix-element-visual-studio-templates.md)|--|--|
|[MaxFrameworkVersion](../extensibility/maxframeworkversion-element-visual-studio-templates.md)|--|--|
|[Name](../extensibility/name-element-visual-studio-templates.md)|--|Paket<br /><br /> id|
|[NumberOfParentCategoriesToRollUp](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)|--|--|
|[PreviewImage](../extensibility/previewimage-element-visual-studio-templates.md)|--|--|
|[Projekt](../extensibility/project-element-visual-studio-templates.md)|Ordner<br /><br /> ProjectItem|Datei<br /><br /> TargetFileName<br /><br /> ReplaceParameters|
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|ProjectTemplateLink<br /><br /> SolutionFolder|--|
|[ProjectItem (Elementvorlagen)](../extensibility/projectitem-element-visual-studio-item-templates.md)|--|SubType<br /><br /> CustomTool<br /><br /> ItemType<br /><br /> ReplaceParameters<br /><br /> TargetFileName|
|[ProjectItem (Projektvorlagen)](../extensibility/projectitem-element-visual-studio-project-templates.md)|--|TargetFileName<br /><br /> ReplaceParameters<br /><br /> OpenInEditor<br /><br /> OpenOrder<br /><br /> OpenInWebBrowser<br /><br /> OpenInHelpBrowser|
|[ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md)|--|--|
|[ProjectTemplateLink](../extensibility/projecttemplatelink-element-visual-studio-templates.md)|--|ProjectName|
|[ProjectType](../extensibility/projecttype-element-visual-studio-templates.md)|--|--|
|[PromptForSaveOnCreation](../extensibility/promptforsaveoncreation-element-visual-studio-templates.md)|--|--|
|[ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md)|--|--|
|[Referenz](../extensibility/reference-element-visual-studio-templates.md)|Assembly|--|
|[References](../extensibility/references-element-visual-studio-templates.md)|Referenz|--|
|[RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md)|--|--|
|[RequiredPlatformVersion](../extensibility/requiredplatformversion-element-visual-studio-templates.md)|--|Version|
|[SDKReferenz](../extensibility/sdkreference-element-visual-studio-templates.md)|--|Paket|
|[ShowByDefault](../extensibility/showbydefault-visual-studio-templates.md)|--|--|
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|ProjectTemplateLink<br /><br /> SolutionFolder|name|
|[SortOrder](../extensibility/sortorder-element-visual-studio-templates.md)|--|--|
|[SupportsCodeSeparation](../extensibility/supportscodeseparation-element-visual-studio-templates.md)|--|--|
|[SupportsLanguageDropDown](../extensibility/supportslanguagedropdown-element-visual-studio-templates.md)|--|--|
|[SupportsMasterPage](../extensibility/supportsmasterpage-element-visual-studio-templates.md)|--|--|
|[TargetPlatformName](../extensibility/targetplatformname-element-visual-studio-templates.md)|RequiredPlatformVersion|--|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|ProjectCollection<br /><br /> Project<br /><br /> References<br /><br /> ProjectItem<br /><br /> CustomParameters|[BuildOnLoad](../extensibility/buildonload-visual-studio-templates.md)|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Name<br /><br /> BESCHREIBUNG<br /><br /> Symbol<br /><br /> PreviewImage<br /><br /> ProjectType<br /><br /> ProjectSubType<br /><br /> TemplateID<br /><br /> TemplateGroupID<br /><br /> SortOrder<br /><br /> CreateNewFolder<br /><br /> DefaultName<br /><br /> ProvideDefaultName<br /><br /> PromptForSaveOnCreation<br /><br /> EnableLocationBrowseButton<br /><br /> EnableEditOfLocationField<br /><br /> Ausgeblendet<br /><br /> DisplayInParentCategories<br /><br /> LocationFieldMRUPrefix<br /><br /> NumberOfParentCategoriesToRollUp<br /><br /> CreateInPlace<br /><br /> BuildOnLoad<br /><br /> BuildProjectOnload<br /><br /> ShowByDefault<br /><br /> LocationField<br /><br /> SupportsMasterPage<br /><br /> SupportsCodeSeparation<br /><br /> SupportsLanguageDropDown<br /><br /> RequiredFrameworkVersion<br /><br /> FrameworkVersion<br /><br /> MaxFrameworkVersion<br /><br /> CustomDataSignature<br /><br /> TargetPlatformName|--|
|[TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md)|--|--|
|[TemplateID](../extensibility/templateid-element-visual-studio-templates.md)|--|--|
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|TemplateData<br /><br /> TemplateContent<br /><br /> WizardExtension<br /><br /> WizardData|type<br /><br /> Version|
|[WizardData](../extensibility/wizarddata-element-visual-studio-templates.md)|--|name|
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|Assembly<br /><br /> FullClassName|--|

## <a name="see-also"></a>Weitere Informationen

- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
