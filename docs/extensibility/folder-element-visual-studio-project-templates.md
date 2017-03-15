---
title: "Folder-Element (Visual Studio-Projektvorlagen) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#Folder"
helpviewer_keywords: 
  - "Folder-Element [Visual Studio-Projektvorlagen]"
ms.assetid: 558e3d41-0db5-4c44-82bb-6bb87892b093
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Folder-Element (Visual Studio-Projektvorlagen)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gibt einen Ordner an, der dem Projekt hinzugefügt wird.  
  
## Syntax  
  
```  
<Folder Name="Project Folder">  
    <Folder> ... </Folder>  
    <ProjectItem> ... </ProjectItem>  
</Folder>  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und übergeordnete Elemente beschrieben.  
  
### Attribute  
  
|Attribut|Description|  
|--------------|-----------------|  
|`Name`|Erforderliches Attribut.<br /><br /> Der Name des Projektordners.|  
|`TargetFolderName`|Optionales Attribut.<br /><br /> Gibt den Namen des Ordners bei der Projekterstellung von der Vorlage an.  Dieses Attribut ist nützlich bei der Verwendung der Parameterersetzung beim Erstellen eines Ordnernamens oder beim Benennen eines Ordners mit einer internationalen Zeichenfolge, die in der ZIP\-Datei nicht direkt verwendet werden kann.|  
  
### Untergeordnete Elemente  
  
|Element|Description|  
|-------------|-----------------|  
|`Folder`|Gibt einen Ordner an, der dem Projekt hinzugefügt werden soll.  Ein `Folder`\-Element kann untergeordnete `Folder`\-Elemente enthalten.|  
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|Gibt eine Datei an, die dem Projekt hinzugefügt werden soll.|  
  
### Übergeordnete Elemente  
  
|Element|Description|  
|-------------|-----------------|  
|[Project](../extensibility/project-element-visual-studio-templates.md)|Optionales untergeordnetes Element von [TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md).|  
  
## Hinweise  
 `Folder` ist ein optionales untergeordnetes Element von `Project`.  
  
 Die folgenden Möglichkeiten stehen zur Auswahl, um Projektelemente in Ordnern in einer Vorlage zu organisieren:  
  
-   Schließen Sie die Ordner in die ZIP\-Datei der Vorlage ein, und fügen Sie sie dem Projekt in der VSTEMPLATE\-Datei hinzu, indem Sie den Pfad zur Datei in den `ProjectItem`\-Elementen angeben, ohne `Folder`\-Elemente festzulegen.  Dies ist die empfohlene Methode.  Beispiel:  
  
     `...`  
  
     `<ProjectItem>\Folder\item.cs</ProjectItem>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
-   Schließen Sie die Ordner in die ZIP\-Datei der Vorlage ein, und fügen Sie sie dem Projekt in der VSTEMPLATE\-Datei mit `Folder`\-Elementen hinzu.  Beispiel:  
  
     `...`  
  
     `<Folder name="Folder">`  
  
     `<ProjectItem>item.cs</ProjectItem>`  
  
     `</Folder>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
-   Schließen Sie keine Ordner in die ZIP\-Datei der Vorlage ein. Stattdessen fügen Sie Ordner über das `TargetFileName`\-Attribut des `ProjectItem`\-Elements hinzu.  Beispiel:  
  
     `...`  
  
     `<ProjectItem TargetFileName="\Folder\item.cs">item.cs</ProjectItem>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
## Beispiel  
 Im folgenden Beispiel werden die Metadaten für eine Projektvorlage einer Windows\-Anwendung in [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] veranschaulicht.  
  
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
  
## Siehe auch  
 [Schemareferenz zu Visual Studio\-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [Erstellen von benutzerdefinierten Projekt\- und Elementvorlagen](../ide/creating-project-and-item-templates.md)   
 [ProjectItem\-Element \(Visual Studio\-Elementvorlagen\)](../extensibility/projectitem-element-visual-studio-item-templates.md)