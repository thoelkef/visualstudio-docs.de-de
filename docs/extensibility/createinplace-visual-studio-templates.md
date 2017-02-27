---
title: "CreateInPlace (Visual Studio-Vorlagen) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#CreateInPlace"
helpviewer_keywords: 
  - "<CreateInPlace>-Element [Visual Studio-Vorlagen]"
  - "CreateInPlace-Element [Visual Studio-Vorlagen]"
ms.assetid: 420d46ea-2470-4da9-ad8e-95165588a920
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# CreateInPlace (Visual Studio-Vorlagen)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gibt an, ob das Projekt erstellt und die Parameterersetzung am angegebenen Speicherort ausgeführt werden soll, bzw. ob die Parameterersetzung in einem temporären Verzeichnis stattfinden und das Projekt anschließend am angegebenen Speicherort gespeichert werden soll.  
  
## Syntax  
  
```  
<CreateInPlace> true/false </CreateInPlace>  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
 Keine.  
  
### Untergeordnete Elemente  
 Keine.  
  
### Übergeordnete Elemente  
  
|Element|Description|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Kategorisiert die Vorlage und definiert, wie diese in den Dialogfeldern **Neues Projekt** oder **Neues Element hinzufügen** angezeigt wird.|  
  
## Textwert  
 Ein Textwert ist erforderlich.  
  
 Der Text muss entweder `true` oder `false` lauten.  Falls `true`, wird das Projekt erstellt, und die Parameterersetzung wird an dem Ort ausgeführt, der im Dialogfeld **Neues Projekt** festgelegt wurde.  Falls `false`, wird die Parameterersetzung in einem temporären Verzeichnis ausgeführt und das Projekt dann an den angegebenen Speicherort kopiert.  
  
## Hinweise  
 `CreateInPlace` ist ein optionales Element.  Der Standardwert ist `true`.  
  
## Beispiel  
 Im folgenden Beispiel werden die Metadaten für eine Vorlage in [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] veranschaulicht.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <CreateInPlace>false</CreateInPlace>  
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
 [Erstellen von benutzerdefinierten Projekt\- und Elementvorlagen](../ide/creating-project-and-item-templates.md)   
 [Schemareferenz zu Visual Studio\-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)