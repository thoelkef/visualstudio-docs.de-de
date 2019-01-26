---
title: ProjectTemplateLink-Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectTemplateLink
helpviewer_keywords:
- <ProjectTemplateLink> element [Visual Studio Templates]
- ProjectTemplateLink element [Visual Studio Templates]
ms.assetid: b0449111-8b48-45a1-a031-ea24b765e969
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8ce474c0896d5f9a72c3c09253bef8ca1a5c4a4e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54947048"
---
# <a name="projecttemplatelink-element-visual-studio-templates"></a>ProjectTemplateLink-Element (Visual Studio-Vorlagen)
Gibt den Pfad zu der *VSTEMPLATE* -Datei eines Projekts in einer Vorlage mit mehreren Projekten.  
  
 \<VSTemplate>  
 \<TemplateContent>  
 \<ProjectCollection>  
 \<ProjectTemplateLink>  
- oder -   
\<VSTemplate>  
 \<TemplateContent>  
 \<ProjectCollection>  
 \<SolutionFolder>  
 \<ProjectTemplateLink>  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<ProjectTemplateLink ProjectName="Name">  
    PathToTemplateFile  
</ProjectTemplateLink>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden attribute-Elemente sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`ProjectName`|Optionales Attribut.<br /><br /> Gibt in einer Vorlage für mehrere Projekte den Namen für jedes einzelne Projekt an. Die **neues Projekt** Dialogfeld nicht möglich, einzelne Projekte Namen zuweisen.|  
|`CopyParameters`|Ermöglicht, dass alle Variablen in der Hauptgruppenvorlage in jede der verknüpften Vorlagen kopiert werden können.<br /><br /> Die Parameter in verknüpften Vorlagen enthalten ein Präfix `"$ext_*$"`. Für die in der Vorlage der übergeordneten Gruppe der Parameter z. B. `$projectname$` verfügt über einen Wert **ExampleProject1**, wenn die verknüpfte Vorlage die jeweilige ausgeführt werden, erhält einen Parameter `$ext_projectname$`, dies ist eine Kopie der `$projectname$`Parameter aus der Vorlage der übergeordneten Gruppe.<br /><br /> Dadurch können verknüpfte Vorlagen einige häufig verwendete Parameter freigeben, die sonst möglicherweise nur in der Vorlage der übergeordneten Gruppe erstellt werden.<br /><br /> Dieses Attribut ist optional und erhält automatisch den Wert `false`, wenn es nicht enthalten ist.<br /><br /> Eingeführt in Visual Studio 2013 Update 2. Um die richtige Produktversion verweisen zu können, finden Sie unter [verweisen auf Assemblys in Visual Studio 2013 SDK Update 2 übermittelten](https://msdn.microsoft.com/library/42b65c3e-e42b-4c39-98c8-bea285f25ffb).|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
 Keine  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Legt die Organisation und den Inhalt von Vorlagen für mehrere Projekte fest.|  
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|Gruppiert Projekte in Vorlagen für mehrere Projekte.|  
  
## <a name="text-value"></a>Textwert  
 Ein Textwert ist erforderlich.  
  
 Dieser Text gibt den Pfad zu der *VSTEMPLATE* -Datei der Vorlage.  
  
## <a name="remarks"></a>Hinweise  
 Vorlagen mit mehreren Projekten fungieren als Container für mindestens zwei Projekte. Die `ProjectTemplateLink` Element wird verwendet, um den Speicherort der an die *VSTEMPLATE* -Datei für eines der Projekte in der Vorlage. Die *VSTEMPLATE* Datei einer Vorlage mit mehreren Projekten enthält ein `ProjectTemplateLink` -Element für jedes Projekt in der Vorlage. Weitere Informationen zu Vorlagen mit mehreren Projekten, finden Sie unter [Vorgehensweise: Erstellen von Vorlagen mit mehreren Projekten](../ide/how-to-create-multi-project-templates.md).  
  
## <a name="example"></a>Beispiel  
 Dieses Beispiel zeigt eine einfache mit mehreren Projekten *VSTEMPLATE* Datei. In diesem Beispiel enthält die Vorlage zwei Projekte: `My Windows Application` und `My Class Library`. Durch das `ProjectName`-Attribut im `ProjectTemplateLink`-Element wird der Name festgelegt, der dem Projekt in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zugewiesen wird. Wenn die `ProjectName` Attribut nicht vorhanden ist, den Namen der *VSTEMPLATE* Datei als Projektname verwendet wird.  
  
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
 [Schemareferenz zu Visual Studio-Vorlage](../extensibility/visual-studio-template-schema-reference.md)   
 [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)   
 [Vorgehensweise: Erstellen von Vorlagen mit mehreren Projekten](../ide/how-to-create-multi-project-templates.md)