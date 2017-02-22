---
title: "LocationField-Element (Visual Studio-Projektvorlagen) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/vstemplate/2005#LocationField"
helpviewer_keywords: 
  - "LocationField-Element [Visual Studio-Projektvorlagen]"
ms.assetid: 6aaaa155-6ce0-4f7f-aa50-8d63d7a7c992
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# LocationField-Element (Visual Studio-Projektvorlagen)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gibt an, ob die **Speicherort** Textfeld in der **Neues Projekt** Dialogfeld aktiviert, deaktiviert oder ausgeblendet werden, für die Projektvorlage.  
  
 \<VSTemplate\>  
 \<TemplateData\>  
 \<LocationField\>  
  
## Syntax  
  
```  
<LocationField> Enabled/Disabled/Hidden </LocationField>  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden attribute\-Elemente sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
 Keine.  
  
### Untergeordnete Elemente  
 Keine  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Kategorisiert die Vorlage und definiert, wie es in einem angezeigt der **Neues Projekt**.|  
  
## Textwert  
 Ein Textwert ist erforderlich.  
  
 Gültige Werte sind:  
  
-   `Enabled`, der angibt, dass die **Speicherort** im Feld der **Neues Projekt** Dialogfeld aktiviert ist.  
  
-   `Disabled`, gibt an, dass die **Speicherort** im Feld der **Neues Projekt** im Dialogfeld deaktiviert ist.  
  
-   `Hidden`, der angibt, dass der **Speicherort** im Feld der **Neues Projekt** Dialogfeld ausgeblendet wird.  
  
## Hinweise  
 Der Standardwert ist `Enabled`.  
  
 Die **Speicherort** Textfeld in der **Neues Projekt** \(Dialogfeld\) kann Benutzer das Standardverzeichnis ändern, in dem neue Projekte gespeichert werden.  
  
 Die Angabe der den `Location` Element wird im Dialogfeld nur berücksichtigt, wenn die zugrunde liegende Projektsystem ihn unterstützt.  
  
## Beispiel  
 Im folgenden Beispiel werden die Metadaten für eine [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]\-Vorlage veranschaulicht.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <LocationField>Disabled</LocationField>  
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