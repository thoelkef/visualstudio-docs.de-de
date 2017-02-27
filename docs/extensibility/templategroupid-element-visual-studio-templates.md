---
title: "TemplateGroupID-Element (Visual Studio-Vorlagen) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#TemplateGroupID"
helpviewer_keywords: 
  - "<TemplateGroupID>-Element [Visual Studio-Vorlagen]"
  - "TemplateGroupID-Element [Visual Studio-Vorlagen]"
ms.assetid: bce7b49a-90bc-4691-aff3-a87e209f6d83
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# TemplateGroupID-Element (Visual Studio-Vorlagen)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gibt an, in welcher Art von Projekt eine Elementvorlage angezeigt wird.  Dieses Element ist von Bedeutung, wenn [ShowByDefault \(Visual Studio\-Vorlagen\)](../extensibility/showbydefault-visual-studio-templates.md) auf `false` festgelegt ist.  Wenn [ShowByDefault \(Visual Studio\-Vorlagen\)](../extensibility/showbydefault-visual-studio-templates.md) auf `true` festgelegt ist, ist eine Elementvorlage in allen Projekttypen verfügbar.  
  
## Syntax  
  
```  
<TemplateGroupID> ... </TemplateGroupID>  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
 Keine  
  
### Untergeordnete Elemente  
 Keine  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Kategorisiert die Vorlage und definiert, wie diese in den Dialogfeldern **Neues Projekt** oder **Neues Element hinzufügen** angezeigt wird.|  
  
## Textwert  
 Ein Textwert ist erforderlich.  
  
 Der Text gibt einen Bezeichner für eine Kategorie von Elementvorlagen an.  
  
## Hinweise  
 `TemplateGroupID` ist ein Element.  
  
 Der Wert des `TemplateGroupID`\-Elements dient zusammen mit der Projektsystemregistrierung \(HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\< Versionsnummer \>*\\Projects\\\) der Filterung von Vorlagen, die im Dialogfeld **Neues Element hinzufügen** angezeigt werden.  
  
|Visual C\+\+\-Wert|Bedeutung|  
|------------------------|---------------|  
|VC\-systemeigen|Für systemeigene Projekte verwendet.  Auch die Standardeinstellung, wenn ein Projekttyp nicht bestimmt werden kann.|  
|VC\-verwaltet|Für verwaltete Projekte \(\/clr\) verwendet.|  
|VC\-Windows|Für alle Projekte verwendet, die auf die Windows\-Plattform abzielen \(systemeigen\/verwaltet\/Speicher\).|  
|WinRT\-systemeigen\-UAP|Für Windows 10\-Speicherprojekte verwendet.|  
|CodeSharing\-systemeigen|Für freigegebene Elementprojekte verwendet.|  
|WinRT\-systemeigen\-6.3|Für Windows 8.1\-Speicherprojekte verwendet.|  
|WinRT\-systemeigen\-Phone\-6.3|Für Windows Phone 8.1\-Projekte verwendet.|  
|WinRT\-systemeigen|Für Windows 8.0\-Speicherprojekte verwendet.|  
|VC\-Android|Für Android\-Projekte verwendet.|  
  
## Siehe auch  
 [Schemareferenz zu Visual Studio\-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [Erstellen von benutzerdefinierten Projekt\- und Elementvorlagen](../ide/creating-project-and-item-templates.md)