---
title: "DefaultName-Element (Visual Studio-Vorlagen) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/vstemplate/2005#DefaultName"
helpviewer_keywords: 
  - "DefaultName-Element [Visual Studio-Projektvorlagen]"
ms.assetid: 0ff056c8-b9d2-4747-9308-92adf1811491
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# DefaultName-Element (Visual Studio-Vorlagen)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gibt den Namen an, der vom Visual Studio\-Projektsystem bei der Projekt\- oder Elementerstellung generiert wird.  
  
## Syntax  
  
```  
<DefaultName>  
    Default Project Name  
</DefaultName>  
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
  
 Dieser Text gibt den Standardnamen des Projekts oder Elements an.  
  
## Hinweise  
 `DefaultName` ist ein optionales Element.  
  
 Bei Projekten gibt dieses Element den Namen des Verzeichnisses an, in dem das Projekt auf dem Datenträger gespeichert ist.  Bei Elementen gibt es den Dateinamen der Quelldatei an.  
  
 Wenn Sie ein Projekt oder Element erstellen, können Sie den Standardnamen mithilfe der Option **Name** ändern, die entweder im Dialogfeld **Neues Projekt** oder von Dialogfeld **Neues Element hinzufügen** verfügbar ist.  
  
 Wenn der Standardname für das Projekt oder Element nicht vom Projektsystem generiert werden soll, legen Sie das [ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md)\-Element auf `False` fest.  
  
## Beispiel  
 Im folgenden Beispiel werden die Metadaten für die Standardelementvorlage einer Klasse in [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] veranschaulicht.  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <DefaultName>MyClass.cs</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem ReplaceParameters="true">MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## Siehe auch  
 [Schemareferenz zu Visual Studio\-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [Erstellen von benutzerdefinierten Projekt\- und Elementvorlagen](../ide/creating-project-and-item-templates.md)