---
title: ProjectType-Element (Visual Studio-Vorlagen) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/vstemplate/2005#ProjectType
helpviewer_keywords: ProjectType element [Visual Studio project templates]
ms.assetid: ccf9d83f-c7f3-49c7-a31f-e1f22bec004c
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fb177139491236cf518aba4e7f2effd213c1a469
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="projecttype-element-visual-studio-templates"></a>ProjectType-Element (Visual Studio-Vorlagen)
Kategorisiert die Projektvorlage, sodass es unter der angegebenen Gruppe angezeigt wird der **neues Projekt** oder **neues Element hinzufügen** (Dialogfeld).  
  
> [!WARNING]
>  Ab Visual Studio 2012 werden Projektvorlagen für C++ unterstützt. In Visual Studio 2010 und früheren Versionen werden sie für C++ nicht unterstützt.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<ProjectType >  
  
## <a name="syntax"></a>Syntax  
  
```  
<ProjectType> CSharp/VisualBasic/VC/Web </ProjectType>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden attribute-Elemente sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
 Keine.  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
 Keine  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Kategorisiert die Vorlage und definiert, wie diese in den Dialogfeldern **Neues Projekt** oder **Neues Element hinzufügen** angezeigt wird.|  
  
## <a name="text-value"></a>Textwert  
 Ein Textwert ist erforderlich.  
  
 Durch diesen Wert wird der Projekttyp angegeben, der von der Vorlage erstellt wird. Er muss einen der folgenden Werte aufweisen:  
  
-   `CSharp`: Gibt an, dass von der Vorlage ein [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]-Projekt oder -Element erstellt wird.  
  
-   `VisualBasic`: Gibt an, dass von der Vorlage ein [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]-Projekt oder -Element erstellt wird.  
  
-   `Web`: Gibt an, dass von der Vorlage ein Webprojekt oder -element erstellt wird. Wenn die `ProjectType` Element dieser Wert enthält, die Sprache des Projekts oder Element gemäß der [ProjectSubType-Element (Visual Studio-Vorlagen)](../extensibility/projectsubtype-element-visual-studio-templates.md).  
  
## <a name="remarks"></a>Hinweise  
 `ProjectType` ist ein erforderliches untergeordnetes Element von `TemplateData`.  
  
 Der Wert des der `ProjectType` Element gibt an, in dem die Vorlage befindet, in der **neues Projekt** oder **neues Element hinzufügen** (Dialogfeld). Z. B. eine Vorlage mit einer `ProjectType` Wert `CSharp` wird unter der **Visual C#-** Knoten in der **neues Projekt** (Dialogfeld).  
  
 Ein Vorlagenuntertyp kann mithilfe der [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) Element.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel werden die Metadaten für eine Projektvorlage einer [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]-Anwendung veranschaulicht.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyStarterKit.csproj">  
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
 [ProjectSubType-Element (Visual Studio-Vorlagen)](../extensibility/projectsubtype-element-visual-studio-templates.md)