---
title: VSTemplate-Element (Visual Studio-Vorlagen) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#VSTemplate
helpviewer_keywords:
- VSTemplate element [Visual Studio project templates]
ms.assetid: f8ac561b-3b0b-4246-9ec9-118d2447e9a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 651e8b6dbbe11c450b105f3185e7e987bb30da9b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697869"
---
# <a name="vstemplate-element-visual-studio-templates"></a>VSTemplate-Element (Visual Studio-Vorlagen)
Enthält alle Metadaten zur Projektvorlage, Elementvorlage oder zum Startkit.

## <a name="syntax"></a>Syntax

```csharp
<VSTemplate Type="TemplateType" Version="x.x.x">
    <TemplateData>    </TemplateData>
    <TemplateContent>    </TemplateContent>
    ...
</VSTemplate>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

| attribute | BESCHREIBUNG |
|-----------| - |
| `Type` | Identifiziert die Vorlage als Projektvorlage oder Elementvorlage. Dieses Attribut kann den `Project` `Item`Wert oder haben. |
| `Version` | Gibt eine Versionsnummer für die Vorlage an. Vorlagen in [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] und `Version` haben den `3.0.0`Attributwert von . |

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Erforderliches Element<br /><br /> Gibt Daten an, die die Vorlage kategorisieren, und definiert, wie sie im Dialogfeld **Neues Projekt** oder Neues **Element** hinzufügen angezeigt wird.|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Erforderliches Element<br /><br /> Gibt den Inhalt der Vorlage an.|
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|Optionales Element.|
|[WizardData](../extensibility/wizarddata-element-visual-studio-templates.md)|Optionales Element.|

### <a name="parent-elements"></a>Übergeordnete Elemente
 Keine.

## <a name="remarks"></a>Bemerkungen
 Das `VSTemplate` Element ist das Stammelement von *.vstemplate-Dateien.*

## <a name="example"></a>Beispiel
 Im folgenden Beispiel werden die Metadaten für eine Projektvorlage einer [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]-Anwendung veranschaulicht.

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyStarterKit.csproj">
            <ProjectItem>Form1.cs</ProjectItem>
            <ProjectItem>Form1.Designer.cs</ProjectItem>
            <ProjectItem>Program.cs</ProjectItem>
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>
            <ProjectItem>Properties\Resources.resx</ProjectItem>
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>
            <ProjectItem>Properties\Settings.settings</ProjectItem>
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Weitere Informationen
- [Visual Studio-Vorlagenschemareferenz](../extensibility/visual-studio-template-schema-reference.md)
- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
