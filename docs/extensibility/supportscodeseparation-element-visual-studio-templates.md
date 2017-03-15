---
title: "SupportsCodeSeparation-Element (Visual Studio-Vorlagen) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#SupportsCodeSeparation"
helpviewer_keywords: 
  - "<SupportsCodeSeparation>-Element [Visual Studio-Vorlagen]"
  - "SupportsCodeSeparation-Element [Visual Studio-Vorlagen]"
ms.assetid: 8112aac8-a269-40e5-b92b-9b9a6ff5a542
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# SupportsCodeSeparation-Element (Visual Studio-Vorlagen)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gibt an, ob das Kontrollkästchen **Code in eigener Datei platzieren** im Dialogfeld **Neues Element hinzufügen** aktiviert ist.  
  
## Syntax  
  
```  
<SupportsCodeSeparation> true/false </SupportsCodeSeparation>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Kategorisiert die Vorlage und definiert, wie diese in den Dialogfeldern **Neues Projekt** oder **Neues Element** angezeigt wird.|  
  
## Textwert  
 Ein Textwert ist erforderlich.  
  
 Der Text muss `true` oder `false` lauten. Dadurch wird angegeben, ob das Kontrollkästchen **Code in eigener Datei platzieren** im Dialogfeld **Neues Element hinzufügen** aktiviert ist oder nicht.  
  
## Hinweise  
 `SupportsCodeSeparation` ist ein optionales Element.  Der Standardwert ist `false`.  
  
 Das `SupportsCodeSeparation`\-Element ist nur für Webelementvorlagen verfügbar.  
  
 Die Codetrennung oder das Code\-Behind\-Seitenmodell ermöglichen es Ihnen, Markup\- und Programmiercode auf zwei verschiedene Dateien zu verteilen.  Dieses Modell wird von [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] und anderen .NET\-Sprachen verwendet.  
  
## Beispiel  
 Im folgenden Beispiel wird festgelegt, dass die Option **Code in eigener Datei platzieren** angezeigt wird.  
  
```  
<VSTemplate Version="3.0.0" Type="Project"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>  
    <TemplateData>  
        <Name>MyWebProjecStarterKit</Name>  
        <Description>A simple Web template</Description>  
        <Icon>icon.ico</Icon>  
        <ProjectType>Web</ProjectType>  
        <ProjectSubType>CSharp</ProjectSubType>  
        <DefaultName>WebSite</DefaultName>  
        <SupportsCodeSeparation>true</SupportsCodeSeparation>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="WebApplication.webproj">  
            <ProjectItem>icon.ico</ProjectItem>  
            <ProjectItem OpenInEditor="true">Default.aspx</ProjectItem>  
            <ProjectItem>Default.aspx.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## Siehe auch  
 [Schemareferenz zu Visual Studio\-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [Erstellen von benutzerdefinierten Projekt\- und Elementvorlagen](../ide/creating-project-and-item-templates.md)