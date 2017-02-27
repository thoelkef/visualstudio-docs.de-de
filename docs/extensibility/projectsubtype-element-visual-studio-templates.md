---
title: "ProjectSubType-Element (Visual Studio-Vorlagen) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#ProjectSubType"
helpviewer_keywords: 
  - "<ProjectSubType>-Element [Visual Studio-Vorlagen]"
  - "ProjectSubType-Element [Visual Studio-Vorlagen]"
ms.assetid: f6895cd4-3e95-4f0e-aa9e-8c7750f46ed4
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# ProjectSubType-Element (Visual Studio-Vorlagen)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Klassifiziert die Vorlage in eine Unterkategorie des Werts, der im `ProjectType`\-Element angegeben wurde.  
  
## Syntax  
  
```  
<ProjectSubType> SubType </ProjectSubType>  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und übergeordnete Elemente beschrieben.  
  
### Attribute  
 Keine.  
  
### Untergeordnete Elemente  
 Keine.  
  
### Übergeordnete Elemente  
  
|Element|Description|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Kategorisiert die Vorlage und definiert, wie diese in den Dialogfeldern **Neues Projekt** oder **Neues Element hinzufügen** angezeigt wird.|  
  
## Textwert  
 Ein Textwert ist erforderlich.  
  
 Dieser Wert gibt die Unterkategorie der Vorlage an.  
  
## Hinweise  
 `ProjectSubType` ist ein optionales untergeordnetes Element von `TemplateData`.  
  
 Das `ProjectSubType`\-Element stellt eine Unterkategorie für das [ProjectType](../extensibility/projecttype-element-visual-studio-templates.md)\-Element bereit.  Dieser Wert kann folgende Werte aufweisen:  
  
-   `SmartDevice-NETCFv1`: Gibt an, dass die Vorlage für [!INCLUDE[Compact](../extensibility/includes/compact_md.md)], Version 1.0, entwickelt wurde.  
  
-   `SmartDevice-NETCFv2`: Gibt an, dass die Vorlage für [!INCLUDE[Compact](../extensibility/includes/compact_md.md)], Version 2.0, entwickelt wurde.  
  
 Wenn die Vorlage ein `ProjectType`\-Element mit dem Wert `Web` enthält, gibt das `ProjectSubType`\-Element die Programmiersprache der Vorlage an.  Dieses Element kann die folgenden Werte aufweisen:  
  
-   `CSharp`: Gibt an, dass von der Vorlage ein [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]\-Webprojekt oder \-Webelement erstellt wird.  
  
-   `VisualBasic`: Gibt an, dass von der Vorlage ein [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\-Webprojekt oder \-Webelement erstellt wird.  
  
## Beispiel  
 Im folgenden Beispiel werden die Metadaten für eine Projektvorlage einer Geräteanwendung in [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] veranschaulicht, die für [!INCLUDE[Compact](../extensibility/includes/compact_md.md)], Version 2.0, entwickelt wurde.  
  
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
  
## Siehe auch  
 [Schemareferenz zu Visual Studio\-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [Erstellen von benutzerdefinierten Projekt\- und Elementvorlagen](../ide/creating-project-and-item-templates.md)   
 [ProjectType\-Element \(Visual Studio\-Vorlagen\)](../extensibility/projecttype-element-visual-studio-templates.md)