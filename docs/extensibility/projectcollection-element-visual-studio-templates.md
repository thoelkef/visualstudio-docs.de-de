---
title: "ProjectCollection-Element (Visual Studio-Vorlagen) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#ProjectCollection"
helpviewer_keywords: 
  - "<ProjectCollection>-Element [Visual Studio-Vorlagen]"
  - "ProjectCollection-Element [Visual Studio-Vorlagen]"
ms.assetid: deb27180-2035-49ed-b835-c47bb3cd2f8f
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# ProjectCollection-Element (Visual Studio-Vorlagen)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Legt die Organisation und den Inhalt von Vorlagen mit mehreren Projekten fest.  
  
## Syntax  
  
```  
<ProjectCollection>  
    <ProjectTemplateLink> ... </ProjectTemplateLink>  
    <SolutionFolder> ... </SolutionFolder>  
</ProjectCollection>  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und übergeordnete Elemente beschrieben.  
  
### Attribute  
 Keine.  
  
### Untergeordnete Elemente  
  
|Element|Description|  
|-------------|-----------------|  
|[ProjectTemplateLink](../extensibility/projecttemplatelink-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Gibt ein Projekt in einer Vorlage mit mehreren Projekten an.|  
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Gruppiert Projekte in Vorlagen mit mehreren Projekten.|  
  
### Übergeordnete Elemente  
  
|Element|Description|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Gibt den Inhalt der Vorlage an.|  
  
## Hinweise  
 Vorlagen mit mehreren Projekten fungieren als Container für mindestens zwei Projekte.  Das `ProjectCollection`\-Element wird verwendet, um die Projekte für die Vorlage anzugeben.  Weitere Informationen zu Vorlagen mit mehreren Projekten finden Sie unter [Gewusst wie: Erstellen von Vorlagen mit mehreren Projekten](../ide/how-to-create-multi-project-templates.md).  
  
## Beispiel  
 In diesem Beispiel wird eine einfache VSTEMPLATE\-Stammdatei mit mehreren Projekten veranschaulicht.  In diesem Beispiel enthält die Vorlage zwei Projekte: `My Windows Application` und `My Class Library`.  Durch das `ProjectName`\-Attribut im `ProjectTemplateLink`\-Element wird der Name festgelegt, der dem Projekt in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zugewiesen wird.  Wenn das `ProjectName`\-Attribut nicht vorhanden ist, wird der Name der VSTEMPLATE\-Datei als Projektname verwendet.  
  
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
            <ProjectTemplateLink ProjectName="My Windows Application">  
                WindowsApp\MyTemplate.vstemplate  
            </ProjectTemplateLink>  
            <ProjectTemplateLink ProjectName="My Class Library">  
                ClassLib\MyTemplate.vstemplate  
            </ProjectTemplateLink>  
        </ProjectCollection>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## Siehe auch  
 [Schemareferenz zu Visual Studio\-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [Erstellen von benutzerdefinierten Projekt\- und Elementvorlagen](../ide/creating-project-and-item-templates.md)   
 [Gewusst wie: Erstellen von Vorlagen mit mehreren Projekten](../ide/how-to-create-multi-project-templates.md)