---
title: "SolutionFolder-Element (Visual Studio-Vorlagen) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#SolutionFolder"
helpviewer_keywords: 
  - "<SolutionFolder>-Element [Visual Studio-Vorlagen]"
  - "SolutionFolder-Element [Visual Studio-Vorlagen]"
ms.assetid: 963f0398-fb50-4d8e-879d-d48f8b7c6d80
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# SolutionFolder-Element (Visual Studio-Vorlagen)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gruppiert Projekte in Vorlagen für mehrere Projekte.  
  
## Syntax  
  
```  
<SolutionFolder Name="DirectoryName">  
    ...  
</SolutionFolder>  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden attribute\-Elemente sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`Name`|Erforderliches Attribut.<br /><br /> Der Name des Projektmappenordners.|  
  
### Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[ProjectTemplateLink](../extensibility/projecttemplatelink-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Gibt den Pfad zur VSTEMPLATE\-Datei eines Projekts in einer Vorlage für mehrere Projekte an.|  
|`SolutionFolder`|Optionales Element.<br /><br /> Gruppiert Projekte in Vorlagen für mehrere Projekte.|  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Legt die Organisation und den Inhalt von Vorlagen für mehrere Projekte fest.|  
|`SolutionFolder`|Gruppiert Projekte in Vorlagen für mehrere Projekte.|  
  
## Hinweise  
 Vorlagen mit mehreren Projekten fungieren als Container für mindestens zwei Projekte.  Das `SolutionFolder`\-Element wird verwendet, um die Projekte in der Vorlage in Gruppen zu organisieren.  Die von `SolutionFolder`\-Elementen angegebenen Ordner werden als Projektmappenordner im Projekt in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] erstellt.  Weitere Informationen zu Vorlagen mit mehreren Projekten finden Sie unter [Gewusst wie: Erstellen von Vorlagen mit mehreren Projekten](../ide/how-to-create-multi-project-templates.md).  
  
## Beispiel  
 Dieses Beispiel verwendet das `SolutionFolder`\-Element, um die Vorlage mit mehreren Projekten in zwei Gruppen zu unterteilen, `Math Classes` und `Graphics Classes`.  Die Vorlage enthält vier Projekte, von denen sich je zwei in jedem Projektmappenordner befinden.  
  
```  
<VSTemplate Version="3.0.0" Type="ProjectGroup"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>Multi-Project Template Sample</Name>  
        <Description>An example of a multi-project template</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>VisualBasic</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectCollection>  
            <SolutionFolder Name="Math Classes">  
                <ProjectTemplateLink ProjectName="MathClassLib1">  
                    MathClassLib1\MyTemplate.vstemplate  
                </ProjectTemplateLink>  
                <ProjectTemplateLink ProjectName="MathClassLib2">  
                    MathClassLib2\MyTemplate.vstemplate  
                </ProjectTemplateLink>  
            </SolutionFolder>  
            <SolutionFolder Name="Graphics Classes">  
                <ProjectTemplateLink ProjectName="GraphicsClassLib1">  
                    GraphicsClassLib1\MyTemplate.vstemplate  
                </ProjectTemplateLink>  
                <ProjectTemplateLink ProjectName="GraphicsClassLib2">  
                    GraphicsClassLib2\MyTemplate.vstemplate  
                </ProjectTemplateLink>  
            </SolutionFolder>  
        </ProjectCollection>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## Siehe auch  
 [Schemareferenz zu Visual Studio\-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [Erstellen von benutzerdefinierten Projekt\- und Elementvorlagen](../ide/creating-project-and-item-templates.md)   
 [Gewusst wie: Erstellen von Vorlagen mit mehreren Projekten](../ide/how-to-create-multi-project-templates.md)