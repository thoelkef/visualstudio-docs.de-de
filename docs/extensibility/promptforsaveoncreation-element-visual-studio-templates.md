---
title: "PromptForSaveOnCreation-Element (Visual Studio-Vorlagen) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/vstemplate/2005#PromptForSaveOnCreation"
helpviewer_keywords: 
  - "PromptForSaveOnCreation-Element [Visual Studio-Projektvorlagen]"
ms.assetid: 75174674-0c3c-4b57-b2fd-6ea8e817b67d
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# PromptForSaveOnCreation-Element (Visual Studio-Vorlagen)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gibt an, ob der Benutzer bei Projekterstellung aufgefordert wird, über das Dialogfeld **Neues Projekt** einen Speicherort anzugeben.  Wenn dieses Element auf `true` festgelegt wird, wird der Benutzer aufgefordert, einen Speicherort anzugeben. Wird `false` angegeben, wird er dazu nicht aufgefordert. \(In diesem Fall wird ein temporäres Projekt erstellt.\)  
  
## Syntax  
  
```  
<PromptForSaveOnCreation> true/false </PromptForSaveOnCreation>  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
 Keine.  
  
### Untergeordnete Elemente  
 Keine.  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Kategorisiert die Vorlage und definiert, wie diese in den Dialogfeldern **Neues Projekt** oder **Neues Element hinzufügen** angezeigt wird.|  
  
## Textwert  
 Ein Textwert ist erforderlich.  
  
 Der Text muss entweder `true` oder `false` lauten. `true` gibt an, dass der Benutzer bei Erstellung eines neuen Projekts zur Angabe eines Speicherorts aufgefordert wird.  
  
## Hinweise  
 `PromptForSaveOnCreation` ist ein optionales Element.  Der Standardwert ist `false`.  
  
 Temporäre Projekte sind Projekte, die Sie erstellen und ändern können, ohne den Inhalt des Projekts auf einem Datenträger zu speichern.  Weitere Informationen finden Sie unter [Temporäre Projekte](http://msdn.microsoft.com/de-de/9cf1944c-7045-44cc-8701-7b0eb4099f2b).  
  
## Beispiel  
 Im folgenden Beispiel wird der Wert von `PromptForSaveOnCreation` gleich `false` festgelegt. Dadurch wird angegeben, dass das Projekt als temporäres Projekt erstellt werden kann.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <PromptForSaveOnCreation>false</PromptForSaveOnCreation>  
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