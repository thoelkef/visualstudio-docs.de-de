---
title: FullClassName-Element (Erweiterung des VS-Vorlagen-Assistenten)
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#FullClassName
helpviewer_keywords:
- FullClassName element [Visual Studio project template]
ms.assetid: 651e1010-d529-4856-85ff-c77ceca5d2ed
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3e533fdf5b5497b17949581801721136b18bc2d1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711419"
---
# <a name="fullclassname-element-visual-studio-template-wizard-extension"></a>FullClassName-Element (Visual Studio-Vorlagen-Assistentenerweiterung)
Der vollqualifizierte Name der Klasse, `IWizard` die die Schnittstelle implementiert.

 \<VSTemplate \<> WizardExtension> ... \<FullClassName>

## <a name="syntax"></a>Syntax

```xml
<FullClassName>ClassName</FullClassName>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden attribute-Elemente sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute
 Keine.

### <a name="child-elements"></a>Untergeordnete Elemente
 Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|Enthält die Registrierungselemente zum Anpassen des Vorlagen-Assistenten.|

## <a name="text-value"></a>Textwert
 Ein Textwert ist erforderlich.

 Dieser Text gibt die Klasse `IWizard` an, die die Schnittstelle implementiert. Die angegebene Klasse muss in der Assembly vorhanden sein, die vom [Assemblyelement](../extensibility/assembly-element-visual-studio-template-wizard-extension.md) angegeben wird.

## <a name="remarks"></a>Bemerkungen
 `FullClassName` ist ein erforderliches untergeordnetes Element von `WizardExtension`.

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
- [Visual Studio-Vorlagenschemareferenz](../extensibility/visual-studio-template-schema-reference.md)
- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
- [Gewusst wie: Verwenden von Assistenten mit Projektvorlagen](../extensibility/how-to-use-wizards-with-project-templates.md)
