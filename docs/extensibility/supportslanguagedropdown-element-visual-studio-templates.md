---
title: "SupportsLanguageDropDown-Element (Visual Studio-Vorlagen) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#SupportsLanguageDropDown"
helpviewer_keywords: 
  - "<SupportsLanguageDropDown>-Element [Visual Studio-Vorlagen]"
  - "SupportsLanguageDropDown-Element [Visual Studio-Vorlagen]"
ms.assetid: 641197d5-f724-4c06-bc47-2e22dad3fbfb
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# SupportsLanguageDropDown-Element (Visual Studio-Vorlagen)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gibt an, ob die Webelementvorlage für mehrere Programmiersprachen identisch ist und ob im Dialogfeld **Neues Element hinzufügen** die Option **Sprache** aktiviert ist.  
  
## Syntax  
  
```  
<SupportsLanguageDropDown> true/false </SupportsLanguageDropDown>  
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
  
 Der Text muss `true` oder `false` lauten. Dadurch wird angegeben, ob die Option **Sprache** im Dialogfeld **Neues Element hinzufügen** verfügbar ist oder nicht.  
  
## Hinweise  
 `SupportsLanguageDropDown` ist ein optionales Element.  Der Standardwert ist `false`.  
  
 Das `SupportsLanguageDropDown`\-Element ist nur für Webelementvorlagen verfügbar.  
  
 Wenn der Wert dieses Elements auf `true` festgelegt ist, ist die Elementvorlage für alle Programmiersprachen identisch, und die Option **Sprache** wird im Dialogfeld **Neues Element hinzufügen** aktiviert.  Über diese Option können Sie die Programmiersprache des neuen Elements auswählen, das Sie von der Vorlage erstellen möchten.  
  
## Beispiel  
 Im folgenden Beispiel wird festgelegt, dass die Dropdownoption **Sprache** angezeigt wird.  
  
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
        <SupportsLanguageDropDown>true</SupportsLanguageDropDown>  
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