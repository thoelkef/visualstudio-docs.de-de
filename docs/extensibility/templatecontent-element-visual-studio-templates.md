---
title: TemplateContent-Element (Visual Studio-Vorlagen) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateContent
helpviewer_keywords:
- TemplateContent element [Visual Studio project templates]
ms.assetid: 90ae401c-b294-49ac-98da-e0d274f5bebb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 577ce71d3900947cde1de9a1e913124ab778a1ee
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699230"
---
# <a name="templatecontent-element-visual-studio-templates"></a>TemplateContent-Element (Visual Studio-Vorlagen)

Gibt den Inhalt der Vorlage an.

Elementhierarchie:

```xml
<VSTemplate>
  <TemplateContent>
```

## <a name="syntax"></a>Syntax

```xml
<TemplateContent>
    ...
</TemplateContent>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|[BuildOnLoad](../extensibility/buildonload-visual-studio-templates.md)|Gibt an, ob die Projektmappe erstellt werden soll, wenn ein Projekt aus der Vorlage erstellt wird.|

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Legt die Organisation und den Inhalt von Vorlagen für mehrere Projekte fest.|
|[Projekt](../extensibility/project-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Gibt Dateien oder Verzeichnisse an, die dem Projekt hinzugefügt werden sollen.|
|[References](../extensibility/references-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Gibt die Assemblyverweise an, die für eine Elementvorlage erforderlich sind.|
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|Optionales Element.<br /><br /> Gibt eine in der Vorlage enthaltene Datei an.|
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Gibt alle benutzerdefinierten Parameter an, die verwendet werden sollen, wenn ein Projekt oder Element aus der Vorlage erstellt wird.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Erforderliches Element<br /><br /> Enthält alle Metadaten für die Projektvorlage, Elementvorlage oder das Startkit.|

## <a name="remarks"></a>Bemerkungen
 `TemplateContent`ist ein erforderliches Element.

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

- [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)
- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
