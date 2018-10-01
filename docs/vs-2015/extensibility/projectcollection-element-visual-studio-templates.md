---
title: ProjectCollection-Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
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
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectCollection
helpviewer_keywords:
- <ProjectCollection> element [Visual Studio Templates]
- ProjectCollection element [Visual Studio Templates]
ms.assetid: deb27180-2035-49ed-b835-c47bb3cd2f8f
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b6ca66c8cf18c891d7f9a771495af14eb4cc9921
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47523772"
---
# <a name="projectcollection-element-visual-studio-templates"></a>ProjectCollection-Element (Visual Studio-Vorlagen)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [ProjectCollection-Element (Visual Studio-Vorlagen)](https://docs.microsoft.com/visualstudio/extensibility/projectcollection-element-visual-studio-templates).  
  
Legt die Organisation und den Inhalt von Vorlagen für mehrere Projekte fest.  
  
 \<VSTemplate>  
 \<TemplateContent >  
 \<ProjectCollection >  
  
## <a name="syntax"></a>Syntax  
  
```  
<ProjectCollection>  
    <ProjectTemplateLink> ... </ProjectTemplateLink>  
    <SolutionFolder> ... </SolutionFolder>  
</ProjectCollection>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden attribute-Elemente sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
 Keine  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[ProjectTemplateLink](../extensibility/projecttemplatelink-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Gibt ein Projekt in einer Vorlage mit mehreren Projekten.|  
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Gruppiert Projekte in Vorlagen für mehrere Projekte.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Gibt den Inhalt der Vorlage.|  
  
## <a name="remarks"></a>Hinweise  
 Vorlagen mit mehreren Projekten fungieren als Container für mindestens zwei Projekte. Die `ProjectCollection` Element wird verwendet, um die Projekte enthalten in der Vorlage anzugeben. Weitere Informationen zu Vorlagen mit mehreren Projekten, finden Sie unter [Vorgehensweise: Erstellen von Vorlagen mit mehreren Projekten](../ide/how-to-create-multi-project-templates.md).  
  
## <a name="example"></a>Beispiel  
 Dieses Beispiel zeigt eine einfache VSTEMPLATE-Stammdatei für mehrere Projekte. In diesem Beispiel enthält die Vorlage zwei Projekte: `My Windows Application` und `My Class Library`. Durch das `ProjectName`-Attribut im `ProjectTemplateLink`-Element wird der Name festgelegt, der dem Projekt in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zugewiesen wird. Wenn das `ProjectName`-Attribut nicht vorhanden ist, wird der Name der VSTEMPLATE-Datei als Projektname verwendet.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)   
 [Gewusst wie: Erstellen von Vorlagen mit mehreren Projekten](../ide/how-to-create-multi-project-templates.md)

