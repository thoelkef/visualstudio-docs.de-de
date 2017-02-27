---
title: "Description-Element (Visual Studio-Vorlagen) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Description-Element [Visual Studio-Projektvorlagen]"
ms.assetid: 6e12be73-081f-4c7d-898f-027c307a9fe1
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# Description-Element (Visual Studio-Vorlagen)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gibt die Beschreibung der Vorlage an, so wie sie im Dialogfeld **Neues Projekt** oder **Neues Element hinzufügen** angezeigt wird.  
  
## Syntax  
  
```  
<Description>  
    Template Description  
</Description>  
```  
  
```  
<Description Package="{PackageID}" ID="ResourceID" />  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
  
|Attribut|Description|  
|--------------|-----------------|  
|`Package`|Optionales Attribut für komplexere Benutzerszenarien.<br /><br /> Eine GUID, durch die die ID des Visual Studio\-Pakets angegeben wird.|  
|`ID`|Optionales Attribut für komplexere Benutzerszenarien.<br /><br /> Gibt die ID der Visual Studio\-Ressource an.|  
  
### Untergeordnete Elemente  
 Keine.  
  
### Übergeordnete Elemente  
  
|Element|Description|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Kategorisiert die Vorlage und definiert, wie diese in den Dialogfeldern **Neues Projekt** oder **Neues Element hinzufügen** angezeigt wird.|  
  
## Textwert  
 Ein Textwert ist erforderlich, es sei denn, das `Package`\-Attribut und das `ID`\-Attribut werden verwendet.  
  
 Der Text enthält eine Beschreibung der Vorlage.  
  
## Hinweise  
 `Description` ist ein erforderliches untergeordnetes Element des `TemplateData`\-Elements.  
  
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