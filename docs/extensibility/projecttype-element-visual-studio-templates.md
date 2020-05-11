---
title: ProjectType-Element (Visual Studio-Vorlagen) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectType
helpviewer_keywords:
- ProjectType element [Visual Studio project templates]
ms.assetid: ccf9d83f-c7f3-49c7-a31f-e1f22bec004c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d794bd5e81e77a892b5a3be38ff73ab805582dd7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701808"
---
# <a name="projecttype-element-visual-studio-templates"></a>ProjectType-Element (Visual Studio-Vorlagen)
Kategorisiert die Projektvorlage so, dass sie unter der angegebenen Gruppe im Dialogfeld **Neues Projekt** oder Neues **Element hinzufügen** angezeigt wird.

> [!WARNING]
> Ab Visual Studio 2012 werden Projektvorlagen für C++ unterstützt. In Visual Studio 2010 und früheren Versionen werden sie für C++ nicht unterstützt.

 \<VSTemplate \<> TemplateData> \<ProjectType>

## <a name="syntax"></a>Syntax

```xml
<ProjectType> CSharp/VisualBasic/VC/Web </ProjectType>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Kategorisiert die Vorlage und definiert, wie diese in den Dialogfeldern **Neues Projekt** oder **Neues Element hinzufügen** angezeigt wird.|

## <a name="text-value"></a>Textwert
 Ein Textwert ist erforderlich.

 Durch diesen Wert wird der Projekttyp angegeben, der von der Vorlage erstellt wird. Er muss einen der folgenden Werte aufweisen:

- `CSharp`: Gibt an, dass von der Vorlage ein [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]-Projekt oder -Element erstellt wird.

- `VisualBasic`: Gibt an, dass von der Vorlage ein [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]-Projekt oder -Element erstellt wird.

- `Web`: Gibt an, dass die Vorlage ein Webprojekt oder -element erstellt. Wenn `ProjectType` das Element diesen Wert enthält, wird die Sprache des Projekts oder Elements im [ProjectSubType-Element (Visual Studio-Vorlagen)](../extensibility/projectsubtype-element-visual-studio-templates.md)definiert.

## <a name="remarks"></a>Bemerkungen
 `ProjectType` ist ein erforderliches untergeordnetes Element von `TemplateData`.

 Der Wert `ProjectType` des Elements gibt an, wo sich die Vorlage im Dialogfeld **Neues Projekt** oder Neues **Element hinzufügen** befindet. Beispielsweise wird eine Vorlage `ProjectType` mit `CSharp` dem Wert "Visual C" im Dialogfeld **Neues Projekt** unter dem Knoten **"Visual C"** angezeigt.

 Ein Vorlagenuntertyp kann mithilfe des [ProjectSubType-Elements](../extensibility/projectsubtype-element-visual-studio-templates.md) angegeben werden.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel werden die Metadaten für eine Projektvorlage einer [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]-Anwendung veranschaulicht.

```
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
- [ProjectSubType-Element (Visual Studio-Vorlagen)](../extensibility/projectsubtype-element-visual-studio-templates.md)
