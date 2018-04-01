---
title: ProjectSubType-Element (Visual Studio-Vorlagen) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectSubType
helpviewer_keywords:
- ProjectSubType element [Visual Studio Templates]
- <ProjectSubType> element [Visual Studio Templates]
ms.assetid: f6895cd4-3e95-4f0e-aa9e-8c7750f46ed4
caps.latest.revision: 13
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 11effbe7e1fc6c7380ba8dbc8da3f2fe14614b5b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="projectsubtype-element-visual-studio-templates"></a>ProjectSubType-Element (Visual Studio-Vorlagen)
Klassifiziert die Vorlage in einer Unterkategorie des Werts der `ProjectType` Element.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<ProjectSubType >  
  
## <a name="syntax"></a>Syntax  
  
```  
<ProjectSubType> SubType </ProjectSubType>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden attribute-Elemente sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
 Keine  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
 Keine  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Kategorisiert die Vorlage und definiert, wie diese in den Dialogfeldern **Neues Projekt** oder **Neues Element hinzufügen** angezeigt wird.|  
  
## <a name="text-value"></a>Textwert  
 Ein Textwert ist erforderlich.  
  
 Dieser Wert gibt die Unterkategorie der Vorlage.  
  
## <a name="remarks"></a>Hinweise  
 `ProjectSubType` ist ein optionales untergeordnetes Element von `TemplateData`.  
  
 Die `ProjectSubType` -Element stellt eine Unterkategorie aus, um die [ProjectType](../extensibility/projecttype-element-visual-studio-templates.md) Element. Dieser Wert kann Folgendes enthalten:  
  
-   `SmartDevice-NETCFv1`: Gibt an, dass die Projektvorlage abzielt die [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] Version 1.0.  
  
-   `SmartDevice-NETCFv2`: Gibt an, dass die Vorlage Ziele der [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] Version 2.0.  
  
 Wenn eine Vorlage enthält einen `ProjectType` Element mit einem Wert von `Web`, die `ProjectSubType` Element gibt die Programmiersprache der Vorlage. Dieses Element kann die folgenden Werte aufweisen:  
  
-   `CSharp`: Gibt an, dass die Projektvorlage erstellt eine [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Webprojekt oder-Element.  
  
-   `VisualBasic`: Gibt an, dass die Projektvorlage erstellt eine [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Webprojekt oder-Element.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt die Metadaten für eine Projektvorlage für eine [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Gerät Anwendung Ziele der [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] Version 2.0.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic device template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <ProjectSubType>SmartDevice-NETCFv2</ProjectSubType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyTemplate.csproj">  
            <ProjectItem>Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>  
            <ProjectItem>Properties\Resources.resx</ProjectItem>  
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>  
            <ProjectItem>Properties\Settings.settings</ProjectItem>  
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)   
 [ProjectType-Element (Visual Studio-Vorlagen)](../extensibility/projecttype-element-visual-studio-templates.md)