---
title: Folder-Element (Visual Studio-Projektvorlagen) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Folder
helpviewer_keywords:
- Folder element [Visual Studio project templates]
ms.assetid: 558e3d41-0db5-4c44-82bb-6bb87892b093
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c2ecf9c2973a5fb09cf1a217bd700882dce41626
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="folder-element-visual-studio-project-templates"></a>Folder-Element (Visual Studio-Projektvorlagen)
Gibt einen Ordner, der dem Projekt hinzugefügt werden.  
  
 \<VSTemplate>  
 \<TemplateContent >  
 \<Project>  
 \<Ordner >  
  
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
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Name`|Erforderliches Attribut.<br /><br /> Der Name des Projektordners.|  
|`TargetFolderName`|Optionales Attribut.<br /><br /> Gibt den Namen für den Ordner, wenn ein Projekt aus der Vorlage erstellt wurde. Dieses Attribut ist nützlich für die Verwendung von parameterersetzung So erstellen einen Ordnernamen ein, oder benennen einen Ordner mit einer internationalen Zeichenfolge, die nicht direkt in der ZIP-Datei verwendet werden kann.|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|`Folder`|Gibt einen Ordner auf dem Projekt hinzugefügt. `Folder` Elemente können untergeordnete enthalten `Folder` Elemente.|  
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|Gibt eine Datei zum Projekt hinzugefügt.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[Projekt](../extensibility/project-element-visual-studio-templates.md)|Optionales untergeordnetes Element von [TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md).|  
  
## <a name="remarks"></a>Hinweise  
 `Folder` ist ein optionales untergeordnetes Element des `Project`.  
  
 Sie können eine der folgenden Methoden, um Projektelemente in Ordnern in einer Vorlage zu organisieren:  
  
-   Schließen Sie die Ordner in die ZIP-Datei der Vorlage, und das Projekt in der VSTEMPLATE-Datei hinzufügen, indem angeben des Pfads zur Datei in die `ProjectItem` Elementen, die keine `Folder` Elemente. Dies ist die empfohlene Methode. Zum Beispiel:  
  
     `...`  
  
     `<ProjectItem>\Folder\item.cs</ProjectItem>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
-   Schließen Sie die Ordner in die ZIP-Datei der Vorlage, und fügen sie das Projekt in der VSTEMPLATE-Datei mit hinzu `Folder` Elemente. Zum Beispiel:  
  
     `...`  
  
     `<Folder name="Folder">`  
  
     `<ProjectItem>item.cs</ProjectItem>`  
  
     `</Folder>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
-   Schließen Sie Ordner nicht in der ZIP-Vorlagendatei, aber Hinzufügen von Ordnern, die mit der `TargetFileName` Attribut von der `ProjectItem` Element. Zum Beispiel:  
  
     `...`  
  
     `<ProjectItem TargetFileName="\Folder\item.cs">item.cs</ProjectItem>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Metadaten für eine Projektvorlage für eine [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Windows-Anwendung.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)   
 [ProjectItem-Element (Visual Studio-Projektelementvorlagen)](../extensibility/projectitem-element-visual-studio-item-templates.md)