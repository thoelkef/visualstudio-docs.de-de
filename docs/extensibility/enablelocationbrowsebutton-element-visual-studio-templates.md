---
title: "EnableLocationBrowseButton-Element (Visual Studio-Vorlagen) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/vstemplate/2005#EnableLocationBrowseButton"
helpviewer_keywords: 
  - "EnableLocationBrowseButton [Visual Studio-Projektvorlagen]"
ms.assetid: a12d10d8-af49-482a-af77-e084fd07a47d
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# EnableLocationBrowseButton-Element (Visual Studio-Vorlagen)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gibt an, ob die Schaltfläche **Durchsuchen** im Dialogfeld **Neues Projekt** verfügbar ist, sodass Benutzer das Standardverzeichnis problemlos ändern können, in dem ein neues Projekt gespeichert wird.  
  
## Syntax  
  
```  
<EnableLocationBrowseButton> true/false </EnableLocationBrowseButton>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Kategorisiert die Vorlage und definiert, wie diese in den Dialogfeldern **Neues Projekt** oder **Neues Element hinzufügen** angezeigt wird.|  
  
## Textwert  
 Ein Textwert ist erforderlich.  
  
 Der Text muss entweder `true` oder `false` lauten. Dadurch wird angegeben, ob die Schaltfläche **Durchsuchen** im Dialogfeld **Neues Projekt** angezeigt wird oder nicht.  
  
## Hinweise  
 `EnableLocationBrowseButton` ist ein optionales Element.  Der Standardwert ist `true`. Das heißt, die Schaltfläche **Durchsuchen** wird im Dialogfeld **Neues Projekt** angezeigt.  
  
 Im Dialogfeld **Neues Projekt** wird durch das Textfeld **Speicherort** das Verzeichnis angegeben, in dem neue Projekte gespeichert werden.  Über die Schaltfläche **Durchsuchen** können Sie dieses Verzeichnis ändern, indem Sie das Dialogfeld **Projektspeicherort** anzeigen, in dem Sie leicht zu einem anderen Computerverzeichnis navigieren und dieses dann als Verzeichnis für neue Projekte auswählen können.  
  
## Beispiel  
 Im folgenden Beispiel werden die Metadaten für eine Windows\-Anwendung in [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] veranschaulicht.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <EnableLocationBrowseButton>false</EnableLocationBrowseButton>  
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