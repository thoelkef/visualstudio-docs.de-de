---
title: SolutionFolder-Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SolutionFolder
helpviewer_keywords:
- <SolutionFolder> element [Visual Studio Templates]
- SolutionFolder element [Visual Studio Templates]
ms.assetid: 963f0398-fb50-4d8e-879d-d48f8b7c6d80
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c5e47729d55b9c248b81c5867175fed75e8b93a8
ms.sourcegitcommit: 35bebf794f528d73d82602e096fd97d7b8f82c25
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/18/2018
ms.locfileid: "53561589"
---
# <a name="solutionfolder-element-visual-studio-templates"></a>SolutionFolder-Element (Visual Studio-Vorlagen)
Gruppiert Projekte in Vorlagen für mehrere Projekte.  
  
 \<VSTemplate>  
 \<TemplateContent >  
 \<ProjectCollection >  
 \<SolutionFolder >  
  
## <a name="syntax"></a>Syntax  
  
```  
<SolutionFolder Name="DirectoryName">  
    ...  
</SolutionFolder>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden attribute-Elemente sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Name`|Erforderliches Attribut.<br /><br /> Der Name des Projektmappenordners.|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[ProjectTemplateLink](../extensibility/projecttemplatelink-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Gibt den Pfad zur VSTEMPLATE-Datei eines Projekts in einer Vorlage für mehrere Projekte an.|  
|`SolutionFolder`|Optionales Element.<br /><br /> Gruppiert Projekte in Vorlagen für mehrere Projekte.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Legt die Organisation und den Inhalt von Vorlagen für mehrere Projekte fest.|  
|`SolutionFolder`|Gruppiert Projekte in Vorlagen für mehrere Projekte.|  
  
## <a name="remarks"></a>Hinweise  
 Vorlagen mit mehreren Projekten fungieren als Container für mindestens zwei Projekte. Das `SolutionFolder`-Element wird verwendet, um die Projekte in der Vorlage in Gruppen zu organisieren. Die von `SolutionFolder`-Elementen angegebenen Ordner werden als Projektmappenordner im Projekt in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] erstellt. Weitere Informationen zu Vorlagen mit mehreren Projekten, finden Sie unter [Vorgehensweise: Erstellen von Vorlagen mit mehreren Projekten](../ide/how-to-create-multi-project-templates.md).  
  
## <a name="example"></a>Beispiel  
 Dieses Beispiel verwendet das `SolutionFolder`-Element, um die Vorlage mit mehreren Projekten in zwei Gruppen zu unterteilen, `Math Classes` und `Graphics Classes`. Die Vorlage enthält vier Projekte, von denen sich je zwei in jedem Projektmappenordner befinden.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)   
 [Vorgehensweise: Erstellen von Vorlagen mit mehreren Projekten](../ide/how-to-create-multi-project-templates.md)