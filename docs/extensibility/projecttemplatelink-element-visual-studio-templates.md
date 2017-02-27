---
title: "ProjectTemplateLink-Element (Visual Studio-Vorlagen) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#ProjectTemplateLink"
helpviewer_keywords: 
  - "<ProjectTemplateLink>-Element [Visual Studio-Vorlagen]"
  - "ProjectTemplateLink-Element [Visual Studio-Vorlagen]"
ms.assetid: b0449111-8b48-45a1-a031-ea24b765e969
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# ProjectTemplateLink-Element (Visual Studio-Vorlagen)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gibt den Pfad zur VSTEMPLATE\-Datei eines Projekts in einer Vorlage für mehrere Projekte an.  
  
## Syntax  
  
```  
<ProjectTemplateLink ProjectName="Name">     PathToTemplateFile </ProjectTemplateLink>  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden attribute\-Elemente sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`ProjectName`|Optionales Attribut.<br /><br /> Gibt in einer Vorlage für mehrere Projekte den Namen für jedes einzelne Projekt an.  Über das Dialogfeld **Neues Projekt** können einzelnen Projekten keine Namen zugewiesen werden.|  
|`CopyParameters`|Ermöglicht, dass alle Variablen in der Hauptgruppenvorlage in jede der verknüpften Vorlagen kopiert werden können.<br /><br /> Die Parameter in verknüpften Vorlagen enthalten ein Präfix `"$ext_*$"`.  Wenn beispielsweise in der Vorlage der übergeordneten Gruppe der Parameter `$projectname$` den Wert ExampleProject1 besitzt, ruft die verknüpfte Vorlage bei Ausführung einen Parameter `$ext_projectname$` ab, die eine Kopie des `$projectname$`\-Parameters aus der Vorlage der übergeordneten Gruppe ist.<br /><br /> Dadurch können verknüpfte Vorlagen einige häufig verwendete Parameter freigeben, die sonst möglicherweise nur in der Vorlage der übergeordneten Gruppe erstellt werden.<br /><br /> Dieses Attribut ist optional und erhält automatisch den Wert `false`, wenn es nicht enthalten ist.<br /><br /> Eingeführt in Visual Studio 2013 Update 2.  Informationen zum Verweisen auf die richtige Produktversion finden Sie unter [Referencing Assemblies Delivered in the Visual Studio 2013 SDK Update 2](http://msdn.microsoft.com/de-de/42b65c3e-e42b-4c39-98c8-bea285f25ffb).|  
  
### Untergeordnete Elemente  
 Keine  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Legt die Organisation und den Inhalt von Vorlagen für mehrere Projekte fest.|  
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|Gruppiert Projekte in Vorlagen für mehrere Projekte.|  
  
## Textwert  
 Ein Textwert ist erforderlich.  
  
 Dieser Text gibt den Pfad zur VSTEMPLATE\-Datei der Vorlage an.  
  
## Hinweise  
 Vorlagen mit mehreren Projekten fungieren als Container für mindestens zwei Projekte.  Das `ProjectTemplateLink`\-Element wird verwendet, um den Speicherort der VSTEMPLATE\-Datei für eines der Projekte in der Vorlage anzugeben.  Die VSTEMPLATE\-Datei einer Vorlage für mehrere Projekte enthält ein `ProjectTemplateLink`\-Element für jedes Projekt in der Vorlage.  Weitere Informationen zu Vorlagen für mehrere Projekte finden Sie unter [Gewusst wie: Erstellen von Vorlagen mit mehreren Projekten](../ide/how-to-create-multi-project-templates.md).  
  
## Beispiel  
 Dieses Beispiel zeigt eine einfache VSTEMPLATE\-Stammdatei für mehrere Projekte.  In diesem Beispiel enthält die Vorlage zwei Projekte: `My Windows Application` und `My Class Library`.  Durch das `ProjectName`\-Attribut im `ProjectTemplateLink`\-Element wird der Name festgelegt, der dem Projekt in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zugewiesen wird.  Wenn das `ProjectName`\-Attribut nicht vorhanden ist, wird der Name der VSTEMPLATE\-Datei als Projektname verwendet.  
  
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
            <ProjectTemplateLink ProjectName="My Class Library" CopyParameters="true">  
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