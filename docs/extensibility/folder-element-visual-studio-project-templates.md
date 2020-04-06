---
title: Ordnerelement (Visual Studio-Projektvorlagen) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Folder
helpviewer_keywords:
- Folder element [Visual Studio project templates]
ms.assetid: 558e3d41-0db5-4c44-82bb-6bb87892b093
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cb256b8be0dd9ce68f193750bf3ff5a383d5f073
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711467"
---
# <a name="folder-element-visual-studio-project-templates"></a>Ordnerelement (Visual Studio-Projektvorlagen)
Gibt einen Ordner an, der dem Projekt hinzugefügt wird.

 \<VSTemplate \<> TemplateContent \< \<> Project> Folder>

## <a name="syntax"></a>Syntax

```
<Folder Name="Project Folder">
    <Folder> ... </Folder>
    <ProjectItem> ... </ProjectItem>
</Folder>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden attribute-Elemente sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|`Name`|Erforderliches Attribut.<br /><br /> Der Name des Projektordners.|
|`TargetFolderName`|Optionales Attribut.<br /><br /> Gibt den Namen an, der dem Ordner geben soll, wenn ein Projekt aus der Vorlage erstellt wird. Dieses Attribut ist nützlich, um die Parameterersetzung zum Erstellen eines Ordnernamens oder zum Benennen eines Ordners mit einer internationalen Zeichenfolge zu verwenden, die nicht direkt in der *ZIP-Datei* verwendet werden kann.|

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|`Folder`|Gibt einen Ordner an, der dem Projekt hinzugefügt werden soll. `Folder`Elemente können `Folder` untergeordnete Elemente enthalten.|
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|Gibt eine Datei an, die dem Projekt hinzugefügt werden soll.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[Projekt](../extensibility/project-element-visual-studio-templates.md)|Optionales untergeordnetes Element von [TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md).|

## <a name="remarks"></a>Bemerkungen
 `Folder`ist ein optionales untergeordnetes Element von `Project`.

 Sie können eine der folgenden Methoden verwenden, um Projektelemente in Ordnern in einer Vorlage zu organisieren:

- Fügen Sie die Ordner in die *.zip-Datei* der Vorlage ein, und fügen Sie sie `ProjectItem` dem Projekt `Folder` in der *.vstemplate-Datei* hinzu, indem Sie den Pfad zur Datei in den Elementen ohne Elemente angeben. Dies ist die empfohlene Methode. Beispiel:

     `...`

     `<ProjectItem>\Folder\item.cs</ProjectItem>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

- Fügen Sie die Ordner in die *Zip-Datei* der Vorlage ein, `Folder` und fügen Sie sie dem Projekt in der *.vstemplate-Datei* mit Elementen hinzu. Beispiel:

     `...`

     `<Folder name="Folder">`

     `<ProjectItem>item.cs</ProjectItem>`

     `</Folder>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

- Schließen Sie keine Ordner in die *ZIP-Datei* `TargetFileName` der Vorlage `ProjectItem` ein, fügen Sie jedoch Ordner mit dem Attribut des Elements hinzu. Beispiel:

     `...`

     `<ProjectItem TargetFileName="\Folder\item.cs">item.cs</ProjectItem>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

## <a name="example"></a>Beispiel
 Im folgenden Beispiel werden die Metadaten für [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] eine Projektvorlage für eine Windows-Anwendung veranschaulicht.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyTemplate.csproj">
            <ProjectItem>Form1.cs<ProjectItem>
            <ProjectItem>Form1.Designer.cs</ProjectItem>
            <ProjectItem>Program.cs</ProjectItem>
            <Folder Name="Properties">
                <ProjectItem>AssemblyInfo.cs</ProjectItem>
                <ProjectItem>Resources.resx</ProjectItem>
                <ProjectItem>Resources.Designer.cs</ProjectItem>
                <ProjectItem>Settings.settings</ProjectItem>
                <ProjectItem>Settings.Designer.cs</ProjectItem>
            </Folder>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Weitere Informationen
- [Visual Studio-Vorlagenschemareferenz](../extensibility/visual-studio-template-schema-reference.md)
- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
- [ProjectItem-Element (Visual Studio-Elementvorlagen)](../extensibility/projectitem-element-visual-studio-item-templates.md)
