---
title: WizardExtension-Element (Visual Studio-Vorlagen) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#WizardExtension
helpviewer_keywords:
- WizardExtension element [Visual Studio Templates]
- <WizardExtension> element [Visual Studio Templates]
ms.assetid: d54b01c1-50f5-4b65-828c-686e2321cc8c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fd81b32861114d654aa794b992826589406b1df9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740375"
---
# <a name="wizardextension-element-visual-studio-templates"></a>WizardExtension-Element (Visual Studio-Vorlagen)
Enthält die Registrierungselemente zum Anpassen des Vorlagen-Assistenten.

 \<VSTemplate> ... \<WizardExtension>

## <a name="syntax"></a>Syntax

```
<WizardExtension>
    <Assembly>... </Assembly>
    <FullClassName>... </FullClassName>
</WizardExtension>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden attribute-Elemente sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute
 Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[Versammlung](../extensibility/assembly-element-visual-studio-template-wizard-extension.md)|Erforderliches Element<br /><br /> Gibt den Namen oder den starken Namen einer Assembly an, die im globalen Assemblycache angezeigt wird. Es muss mindestens `Assembly` ein Element `WizardExtension` in einem Element vorhanden sein.|
|[FullClassName](../extensibility/fullclassname-element-visual-studio-template-wizard-extension.md)|Erforderliches Element<br /><br /> Der vollqualifizierte Name der Klasse, `IWizard` die die Schnittstelle implementiert. Es muss mindestens `FullClassName` ein Element `WizardExtension` in einem Element vorhanden sein.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Enthält alle Metadaten für die Projektvorlage, Elementvorlage oder das Startkit.|

## <a name="remarks"></a>Bemerkungen
 `WizardExtension` ist ein optionales untergeordnetes Element von `VSTemplate`.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel werden die Metadaten für [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] die Standardprojektvorlage für eine Windows-Anwendung veranschaulicht.

```
<VSTemplate Version="3.0.0" Type="Item"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyTemplate</Name>
        <Description>Template using IWizard extension</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyTemplate.csproj">
            <ProjectItem>Form1.cs<ProjectItem>
            <ProjectItem>Form1.Designer.cs</ProjectItem>
            <ProjectItem>Program.cs</ProjectItem>
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>
            <ProjectItem>Properties\Resources.resx</ProjectItem>
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>
            <ProjectItem>Properties\Settings.settings</ProjectItem>
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>
        </Project>
    </TemplateContent>
    <WizardExtension>
        <Assembly>MyWizard, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom=null</Assembly>
        <FullClassName>MyWizard.CustomWizard</FullClassName>
    </WizardExtension>
</VSTemplate>
```

## <a name="see-also"></a>Weitere Informationen
- [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)
- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
- [Gewusst wie: Verwenden von Assistenten mit Projektvorlagen](../extensibility/how-to-use-wizards-with-project-templates.md)
