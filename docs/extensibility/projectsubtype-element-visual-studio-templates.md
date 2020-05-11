---
title: ProjectSubType-Element (Visual Studio-Vorlagen) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectSubType
helpviewer_keywords:
- ProjectSubType element [Visual Studio Templates]
- <ProjectSubType> element [Visual Studio Templates]
ms.assetid: f6895cd4-3e95-4f0e-aa9e-8c7750f46ed4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 27396ad1bcc4e181b2b8cecd6ca863db2412630d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701834"
---
# <a name="projectsubtype-element-visual-studio-templates"></a>ProjectSubType-Element (Visual Studio-Vorlagen)
Klassifiziert die Vorlage in eine Unterkategorie des `ProjectType` im Element angegebenen Werts.

 \<VSTemplate \<> TemplateData> \<ProjectSubType>

## <a name="syntax"></a>Syntax

```xml
<ProjectSubType> SubType </ProjectSubType>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Erforderliches Element<br /><br /> Kategorisiert die Vorlage und definiert, wie diese in den Dialogfeldern **Neues Projekt** oder **Neues Element hinzufügen** angezeigt wird.|

## <a name="text-value"></a>Textwert
 Ein Textwert ist erforderlich.

 Dieser Wert gibt die Unterkategorie der Vorlage an.

## <a name="remarks"></a>Bemerkungen
 `ProjectSubType` ist ein optionales untergeordnetes Element von `TemplateData`.

 Das `ProjectSubType` Element stellt eine Unterkategorie für das [ProjectType-Element](../extensibility/projecttype-element-visual-studio-templates.md) bereit. Dieser Wert kann Folgendes umfassen:

- `SmartDevice-NETCFv1`: Gibt an, dass [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] die Vorlage auf die Version 1.0 abzielt.

- `SmartDevice-NETCFv2`: Gibt an, dass [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] die Vorlage auf die Version 2.0 abzielt.

  Wenn eine Vorlage `ProjectType` ein Element `Web`mit `ProjectSubType` dem Wert von enthält, gibt das Element die Programmiersprache der Vorlage an. Dieses Element kann die folgenden Werte haben:

- `CSharp`: Gibt an, dass [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] die Vorlage ein Webprojekt oder -element erstellt.

- `VisualBasic`: Gibt an, dass [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] die Vorlage ein Webprojekt oder -element erstellt.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt die Metadaten [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] für eine [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] Projektvorlage für eine Geräteanwendung, die auf die Version 2.0 abzielt.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic device template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <ProjectSubType>SmartDevice-NETCFv2</ProjectSubType>
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
</VSTemplate>
```

## <a name="see-also"></a>Weitere Informationen
- [Visual Studio-Vorlagenschemareferenz](../extensibility/visual-studio-template-schema-reference.md)
- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
- [ProjectType-Element (Visual Studio-Vorlagen)](../extensibility/projecttype-element-visual-studio-templates.md)
