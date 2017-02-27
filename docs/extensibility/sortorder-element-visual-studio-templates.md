---
title: "SortOrder-Element (Visual Studio-Vorlagen) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#SortOrder"
helpviewer_keywords: 
  - "<SortOrder>-Element [Visual Studio-Vorlagen]"
  - "SortOrder-Element [Visual Studio-Vorlagen]"
ms.assetid: 151932c1-f08a-4f78-a8d0-bd2f32211a9c
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# SortOrder-Element (Visual Studio-Vorlagen)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gibt einen Wert an, der die Anordnung der Vorlage unter anderen Vorlagen in derselben Kategorie bestimmt, wenn die Vorlage in den Dialogfeldern **Neues Projekt** oder **Neues Element hinzufügen** angezeigt wird.  
  
## Syntax  
  
```  
<SortOrder> ... </SortOrder>  
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
  
 `integer` zur Darstellung des Werts für die Sortierreihenfolge.  
  
## Hinweise  
 `SortOrder` ist ein optionales Element.  Der Standardwert ist 100, und alle Werte müssen ein Vielfaches von 10 sein.  
  
 Das `SortOrder`\-Element wird bei benutzererstellten Vorlagen ignoriert.  Alle benutzererstellten Vorlagen werden alphabetisch sortiert.  
  
 Vorlagen mit niedrigen Sortierreihenfolgewerten werden in den Dialogfeldern **Neues Projekt** oder **Neues Element hinzufügen** vor Vorlagen mit hohen Sortierreihenfolgewerten angezeigt.  
  
## Beispiel  
 Im folgenden Beispiel werden die Metadaten für die Vorlage einer Standardklasse in [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] veranschaulicht.  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class template.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <SortOrder>290</SortOrder>  
        <DefaultName>MyClass</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 In diesem Beispiel befindet sich das `SortOrder`\-Element relativ weit oben.  Wahrscheinlich verfügen andere [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]\-Elementvorlagen über einen niedrigeren `SortOrder`\-Wert als `290` und werden im Dialogfeld **Neues Element** vor dieser Vorlage angezeigt.  
  
## Siehe auch  
 [Schemareferenz zu Visual Studio\-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [Erstellen von benutzerdefinierten Projekt\- und Elementvorlagen](../ide/creating-project-and-item-templates.md)