---
title: "ProvideDefaultName-Element (Visual Studio-Vorlagen) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/vstemplate/2005#ProvideDefaultName"
helpviewer_keywords: 
  - "ProvideDefaultName-Element [Visual Studio-Projektvorlagen]"
ms.assetid: 7b0e7b20-fd6b-42e2-81d0-e5100cea0528
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# ProvideDefaultName-Element (Visual Studio-Vorlagen)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gibt an, ob das [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Projektsystem in den Dialogfeldern **Neues Element hinzufügen** oder **Neues Projekt** einen Standardnamen für die Vorlage generiert.  
  
## Syntax  
  
```  
<ProvideDefaultName> true/false </ProvideDefaultName>  
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
  
 Der Text muss `true` oder `false` lauten. Dadurch wird angegeben, ob in den Dialogfeldern **Neues Element hinzufügen** oder **Neues Projekt** ein Standardname für die Vorlage generiert wird.  
  
## Hinweise  
 `ProvideDefaultName` ist ein optionales Element.  Der Standardwert ist `true`.  
  
 Wenn das `ProvideDefaultName`\-Element `false` lautet, enthalten die Felder **Name** in den Dialogfeldern **Neues Element hinzufügen** und **Neues Projekt** den Wert `<Namen_eingeben>`.  
  
 Verwenden Sie das [DefaultName](../extensibility/defaultname-element-visual-studio-templates.md)\-Element, um den Standardnamen des Projekts oder Elements in den Dialogfeldern **Neues Element hinzufügen** und **Neues Projekt** anzugeben.  
  
## Beispiel  
 Im folgenden Codebeispiel wird das `ProvideDefaultName`\-Element auf `false` festgelegt.  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <ProvideDefaultName>false</ProvideDefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## Siehe auch  
 [Schemareferenz zu Visual Studio\-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [Erstellen von benutzerdefinierten Projekt\- und Elementvorlagen](../ide/creating-project-and-item-templates.md)