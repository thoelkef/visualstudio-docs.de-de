---
title: "WizardData-Element (Visual Studio-Vorlagen) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/vstemplate/2005#WizardData"
helpviewer_keywords: 
  - "<WizardData>-Element [Visual Studio-Vorlagen]"
  - "WizardData-Element [Visual Studio-Vorlagen]"
ms.assetid: d0403a16-5d07-4fe5-b474-19ae3d9fd3ab
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# WizardData-Element (Visual Studio-Vorlagen)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gibt benutzerdefinierten XML\-Code an.  
  
## Syntax  
  
```  
<WizardData>  
    <!-- XML to pass to the custom wizard extension -->  
    ...  
</WizardData>  
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
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Enthält alle Metadaten für die Projektvorlage, Elementvorlage oder das Starter Kit.|  
  
## Textwert  
 Ein Textwert ist optional.  
  
 Durch diesen Text wird der benutzerdefinierte XML\-Code angegeben, der an die mit dem [WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)\-Element angegebene benutzerdefinierte Assistentenerweiterung übergeben wird.  
  
## Hinweise  
 In diesem Element kann beliebiger XML\-Code angegeben werden.  Der XML\-Code wird als Parameter an die benutzerdefinierte Assistentenerweiterung übergeben. Dadurch hat die Erweiterung Zugriff auf den Inhalt dieses Elements.  Für diese Daten wird keine Validierung ausgeführt.  
  
 Der Inhalt des `WizardData`\-Elements wird innerhalb des Zeichenfolgenwörterbuchs für Parameter in der `IWizard.RunStarted`\-Methode unverändert als Parameter übergeben.  Der Parameter wird $WizardData$ genannt.  
  
## Beispiel  
 Im folgenden Beispiel werden die Metadaten für die Standardprojektvorlage einer Windows\-Anwendung in [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] veranschaulicht.  
  
```  
<VSTemplate Version="3.0.0" Type="Item"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyTemplate</Name>  
        <Description>Template using IWizard extension</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
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
    <WizardExtension>  
        <Assembly>MyWizard, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom=null</Assembly>  
        <FullClassName>MyWizard.CustomWizard</FullClassName>  
    </WizardExtension>  
    <WizardData>  
        <!-- XML to pass to the custom wizard extension -->  
    </WizardData>  
</VSTemplate>  
```  
  
## Siehe auch  
 [Schemareferenz zu Visual Studio\-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [Erstellen von benutzerdefinierten Projekt\- und Elementvorlagen](../ide/creating-project-and-item-templates.md)   
 [WizardExtension\-Element \(Visual Studio\-Vorlagen\)](../extensibility/wizardextension-element-visual-studio-templates.md)   
 [Gewusst wie: Verwenden von Assistenten mit Projektvorlagen](../extensibility/how-to-use-wizards-with-project-templates.md)