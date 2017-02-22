---
title: "ProjectType-Element (Visual Studio-Vorlagen) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/vstemplate/2005#ProjectType"
helpviewer_keywords: 
  - "ProjectType-Element [Visual Studio-Projektvorlagen]"
ms.assetid: ccf9d83f-c7f3-49c7-a31f-e1f22bec004c
caps.latest.revision: 19
caps.handback.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
---
# ProjectType-Element (Visual Studio-Vorlagen)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Kategorisiert die Projektvorlage, sodass sie in den Dialogfeldern **Neues Projekt** oder **Neues Element hinzufügen** unter der angegebenen Gruppe angezeigt wird.  
  
> [!WARNING]
>  Ab Visual Studio 2012 werden Projektvorlagen für C\+\+ unterstützt.  In Visual Studio 2010 und früheren Versionen werden sie für C\+\+ nicht unterstützt.  
  
## Syntax  
  
```  
<ProjectType> CSharp/VisualBasic/VC/Web </ProjectType>  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden attribute\-Elemente sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
 Keine.  
  
### Untergeordnete Elemente  
 Keine.  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Kategorisiert die Vorlage und definiert, wie diese in den Dialogfeldern **Neues Projekt** oder **Neues Element hinzufügen** angezeigt wird.|  
  
## Textwert  
 Ein Textwert ist erforderlich.  
  
 Durch diesen Wert wird der Projekttyp angegeben, der von der Vorlage erstellt wird. Er muss einen der folgenden Werte aufweisen:  
  
-   `CSharp`: Gibt an, dass von der Vorlage ein [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]\-Projekt oder \-Element erstellt wird.  
  
-   `VisualBasic`: Gibt an, dass von der Vorlage ein [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\-Projekt oder \-Element erstellt wird.  
  
-   `Web`: Gibt an, dass von der Vorlage ein Webprojekt oder \-element erstellt wird.  Wenn das `ProjectType`\-Element diesen Wert enthält, wird die Sprache des Projekts oder Elements im [ProjectSubType\-Element \(Visual Studio\-Vorlagen\)](../extensibility/projectsubtype-element-visual-studio-templates.md) definiert.  
  
## Hinweise  
 `ProjectType` ist ein erforderliches untergeordnetes Element von `TemplateData`.  
  
 Durch den Wert des `ProjectType`\-Elements wird angegeben, wo sich die Vorlage im Dialogfeld **Neues Projekt** oder **Neues Element hinzufügen** befindet.  Eine Vorlage mit dem `ProjectType`\-Wert `CSharp` wird beispielsweise im Dialogfeld **Neues Projekt** unter dem Knoten **Visual C\#** angezeigt.  
  
 Ein Vorlagenuntertyp kann mithilfe des [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md)\-Elements festgelegt verwendet.  
  
## Beispiel  
 Im folgenden Beispiel werden die Metadaten für eine Projektvorlage einer [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]\-Anwendung veranschaulicht.  
  
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
  
## Siehe auch  
 [Schemareferenz zu Visual Studio\-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [Erstellen von benutzerdefinierten Projekt\- und Elementvorlagen](../ide/creating-project-and-item-templates.md)   
 [ProjectSubType\-Element \(Visual Studio\-Vorlagen\)](../extensibility/projectsubtype-element-visual-studio-templates.md)