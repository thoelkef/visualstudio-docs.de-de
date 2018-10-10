---
title: Folder-Element (Visual Studio-Projektvorlagen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Folder
helpviewer_keywords:
- Folder element [Visual Studio project templates]
ms.assetid: 558e3d41-0db5-4c44-82bb-6bb87892b093
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c26dd5652b2c167e8ae33be4250015ba32c34a96
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2018
ms.locfileid: "48878874"
---
# <a name="folder-element-visual-studio-project-templates"></a>Folder-Element (Visual Studio-Projektvorlagen)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Folder-Element (Visual Studio-Projektvorlagen)](https://docs.microsoft.com/visualstudio/extensibility/folder-element-visual-studio-project-templates).  
  
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
|`TargetFolderName`|Optionales Attribut.<br /><br /> Gibt den Namen, um den Ordner zu gewähren, wenn ein Projekt aus der Vorlage erstellt wird. Dieses Attribut ist nützlich für die Verwendung von parameterersetzungen erstellen Sie einen Ordnernamen ein, oder benennen einen Ordner mit einer internationalen Zeichenfolge ein, kann nicht direkt in die ZIP-Datei verwendet werden.|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|`Folder`|Gibt einen Ordner auf dem Projekt hinzugefügt. `Folder` Elemente können untergeordnete enthalten `Folder` Elemente.|  
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|Gibt eine Datei zum Projekt hinzufügen.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[Projekt](../extensibility/project-element-visual-studio-templates.md)|Optionales untergeordnetes Element des [TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md).|  
  
## <a name="remarks"></a>Hinweise  
 `Folder` ist ein optionales untergeordnetes Element des `Project`.  
  
 Sie können eine der folgenden Methoden verwenden, so organisieren Projektelemente in Ordnern in einer Vorlage:  
  
-   Schließen Sie die Ordner, in der ZIP-Vorlagendatei und dem Projekt in der VSTEMPLATE-Datei hinzufügen, indem Sie die Angabe des Pfads zur Datei in die `ProjectItem` Elemente ohne `Folder` Elemente. Dies ist die empfohlene Methode. Zum Beispiel:  
  
     `...`  
  
     `<ProjectItem>\Folder\item.cs</ProjectItem>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
-   Schließen Sie die Ordner, in der ZIP-Vorlagendatei, und fügen Sie sie dem Projekt in der VSTEMPLATE-Datei mit `Folder` Elemente. Zum Beispiel:  
  
     `...`  
  
     `<Folder name="Folder">`  
  
     `<ProjectItem>item.cs</ProjectItem>`  
  
     `</Folder>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
-   Schließen Sie Ordner nicht in die ZIP-Datei der Vorlage, aber fügen Sie Ordner mit der `TargetFileName` Attribut der `ProjectItem` Element. Zum Beispiel:  
  
     `...`  
  
     `<ProjectItem TargetFileName="\Folder\item.cs">item.cs</ProjectItem>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt die Metadaten für eine Projektvorlage für eine [!INCLUDE[csprcs](../includes/csprcs-md.md)] Windows-Anwendung.  
  
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

