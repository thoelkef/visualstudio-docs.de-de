---
title: "TemplateID-Element (Visual Studio-Vorlagen) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#TemplateID"
helpviewer_keywords: 
  - "<TemplateID>-Element [Visual Studio-Vorlagen]"
  - "TemplateID-Element [Visual Studio-Vorlagen]"
ms.assetid: 6ca24b4e-0325-4a9e-855e-0cbbe7361d8f
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# TemplateID-Element (Visual Studio-Vorlagen)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Legt einen Bezeichner für eine Elementvorlage fest, die durch das [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md)\-Element in einer Gruppe von Elementvorlagen kategorisiert wird.  
  
## Syntax  
  
```  
<TemplateID> ... </TemplateID>  
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
 `string` legt einen Bezeichner für eine Elementvorlage fest, die durch das `TemplateGroupID`\-Element in einer Gruppe von Elementvorlagen kategorisiert wird.  
  
## Hinweise  
 `TemplateID` ist ein optionales Element.  
  
 Wenn das `TemplateID`\-Element in einer VSTEMPLATE\-Datei fehlt, wird das [Name](../extensibility/name-element-visual-studio-templates.md)\-Element als Bezeichner für die Vorlage verwendet.  
  
 Der Wert des `TemplateID`\-Elements wird zusammen mit dem Projektsystem\-Registrierungsschlüssel \(HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\11.0\\Projects\\\) verwendet, um die im Dialogfeld **Neues Element hinzufügen** angezeigten Vorlagen zu filtern.  
  
## Siehe auch  
 [Schemareferenz zu Visual Studio\-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [Erstellen von benutzerdefinierten Projekt\- und Elementvorlagen](../ide/creating-project-and-item-templates.md)