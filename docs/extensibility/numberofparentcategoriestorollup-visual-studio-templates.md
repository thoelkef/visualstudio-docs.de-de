---
title: NumberOfParentCategoriesToRollUp-Element (Vorlagen)
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#NumberOfParentCategoriesToRollUp
helpviewer_keywords:
- NumberOfParentCategoriesToRollUp element [Visual Studio Templates]
- <NumberOfParentCategoriesToRollUp> element [Visual Studio Templates]
ms.assetid: 6f9d36f5-ae23-4a92-8132-b11799e2c21a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b903b9d0bdab2c17dd2e489de01badad82c15473
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702361"
---
# <a name="numberofparentcategoriestorollup-element-visual-studio-templates"></a>NumberOfParentCategoriesToRollUp-Element (Visual Studio-Vorlagen)
Gibt die Anzahl der übergeordneten Kategorien an, die die Vorlage im Dialogfeld **Neues Projekt** anzeigen.

 \<VSTemplate \<> TemplateData> \<NumberOfParentCategoriesToRollup>

## <a name="syntax"></a>Syntax

```xml
<NumberOfParentCategoriesToRollUp>
1
</NumberOfParentCategoriesToRollUp>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute
 Keine.

### <a name="child-elements"></a>Untergeordnete Elemente
 Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Kategorisiert die Vorlage und definiert, wie diese in den Dialogfeldern **Neues Projekt** oder **Neues Element hinzufügen** angezeigt wird.|

## <a name="text-value"></a>Textwert
 Ein `integer` Wert ist erforderlich.

 Dieser Wert gibt die Anzahl der übergeordneten Kategorien an, die die Vorlage im Dialogfeld **Neues Projekt** anzeigen.

## <a name="remarks"></a>Bemerkungen
 `NumberOfParentCategoriesToRollUp` ist ein optionales Element.

## <a name="example"></a>Beispiel
 In diesem Beispiel werden [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] die Metadaten für eine Windows-Anwendung veranschaulicht. Wenn eine Vorlage mit diesen Metadaten zwei Ordnerebenen unterhalb des Knotens der obersten Ebene [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] platziert wird, wird die Vorlage im Dialogfeld **"Neues Projekt"** im Knoten der obersten Ebene angezeigt. Wenn `NumberOfParentCategoriesToRollUp` der nicht festgelegt ist, wird die Vorlage nur in dem Knoten angezeigt, in dem sie sich physisch befindet.

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <NumberOfParentCategoriesToRollUp>2</NumberOfParentCategoriesToRollUp>
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
