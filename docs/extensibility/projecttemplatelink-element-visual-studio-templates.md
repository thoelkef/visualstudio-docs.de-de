---
title: ProjectTemplateLink-Element (Visual Studio-Vorlagen) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/vstemplate/2005#ProjectTemplateLink
helpviewer_keywords:
- <ProjectTemplateLink> element [Visual Studio Templates]
- ProjectTemplateLink element [Visual Studio Templates]
ms.assetid: b0449111-8b48-45a1-a031-ea24b765e969
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9e614b2ec8ef404ef21e665ac5ae26dd73253f55
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="projecttemplatelink-element-visual-studio-templates"></a>ProjectTemplateLink-Element (Visual Studio-Vorlagen)
Gibt den Pfad zur VSTEMPLATE-Datei eines Projekts in einer Vorlage für mehrere Projekte an.  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<ProjectCollection >  
 \<ProjectTemplateLink >  
- oder -   
\<VSTemplate >  
 \<TemplateContent >  
 \<ProjectCollection >  
 \<SolutionFolder >  
 \<ProjectTemplateLink >  
  
## <a name="syntax"></a>Syntax  
  
```  
<ProjectTemplateLink ProjectName="Name">  
    PathToTemplateFile  
</ProjectTemplateLink>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden attribute-Elemente sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`ProjectName`|Optionales Attribut.<br /><br /> Gibt in einer Vorlage für mehrere Projekte den Namen für jedes einzelne Projekt an. Die **neues Projekt** Dialogfeld nicht einzelne Projekte Namen zuweisen.|  
|`CopyParameters`|Ermöglicht, dass alle Variablen in der Hauptgruppenvorlage in jede der verknüpften Vorlagen kopiert werden können.<br /><br /> Die Parameter in verknüpften Vorlagen enthalten ein Präfix `"$ext_*$"`. Angenommen, wenn in der Vorlage der übergeordneten Gruppe der Parameter `$projectname$` verfügt über einen Wert **ExampleProject1**, wenn die verknüpfte Vorlage er die jeweilige ausgeführt werden, erhält einen Parameter `$ext_projectname$`, dies ist eine Kopie der `$projectname$`Parameter aus der Vorlage der übergeordneten Gruppe.<br /><br /> Dadurch können verknüpfte Vorlagen einige häufig verwendete Parameter freigeben, die sonst möglicherweise nur in der Vorlage der übergeordneten Gruppe erstellt werden.<br /><br /> Dieses Attribut ist optional und erhält automatisch den Wert `false`, wenn es nicht enthalten ist.<br /><br /> Eingeführt in Visual Studio 2013 Update 2. Um die richtige Produktversion verweisen zu können, finden Sie unter [verweisen auf Assemblys in Visual Studio 2013 SDK Update 2 übermittelten](http://msdn.microsoft.com/en-us/42b65c3e-e42b-4c39-98c8-bea285f25ffb).|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
 Keine  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Legt die Organisation und den Inhalt von Vorlagen für mehrere Projekte fest.|  
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|Gruppiert Projekte in Vorlagen für mehrere Projekte.|  
  
## <a name="text-value"></a>Textwert  
 Ein Textwert ist erforderlich.  
  
 Dieser Text gibt den Pfad zur VSTEMPLATE-Datei der Vorlage an.  
  
## <a name="remarks"></a>Hinweise  
 Vorlagen mit mehreren Projekten fungieren als Container für mindestens zwei Projekte. Das `ProjectTemplateLink`-Element wird verwendet, um den Speicherort der VSTEMPLATE-Datei für eines der Projekte in der Vorlage anzugeben. Die VSTEMPLATE-Datei einer Vorlage für mehrere Projekte enthält ein `ProjectTemplateLink`-Element für jedes Projekt in der Vorlage. Weitere Informationen zu Vorlagen mit mehreren Projekten finden Sie unter [Vorgehensweise: Erstellen von Vorlagen mit mehreren Projekten](../ide/how-to-create-multi-project-templates.md).  
  
## <a name="example"></a>Beispiel  
 Dieses Beispiel zeigt eine einfache VSTEMPLATE-Stammdatei für mehrere Projekte. In diesem Beispiel enthält die Vorlage zwei Projekte: `My Windows Application` und `My Class Library`. Durch das `ProjectName`-Attribut im `ProjectTemplateLink`-Element wird der Name festgelegt, der dem Projekt in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zugewiesen wird. Wenn das `ProjectName`-Attribut nicht vorhanden ist, wird der Name der VSTEMPLATE-Datei als Projektname verwendet.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)   
 [Gewusst wie: Erstellen von Vorlagen mit mehreren Projekten](../ide/how-to-create-multi-project-templates.md)