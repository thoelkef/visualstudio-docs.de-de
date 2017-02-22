---
title: "RequiredFrameworkVersion-Element (Visual Studio-Vorlagen) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "<RequiredFrameworkVersion> (Visual Studio-Vorlagen)"
  - "RequiredFrameworkVersion (Visual Studio-Vorlagen)"
ms.assetid: 08a4f609-51a5-4723-b89f-99277fb18871
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# RequiredFrameworkVersion-Element (Visual Studio-Vorlagen)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gibt die minimale Version von .NET Framework an, die für die template.Schema\-Hierarchie erforderlich ist.  
  
## Syntax  
  
```  
<RequiredFrameworkVersion> .... </RequiredFrameworkVersion>  
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
  
 Der Text muss die kleinstmögliche Versionsnummer von .NET Framework sein, die für die Vorlage erforderlich ist.  
  
## Hinweise  
 `RequiredFrameworkVersion` ist ein optionales Element.  Verwenden Sie dieses Element, wenn die Vorlage nur eine bestimmte minimale Version und höhere Versionen, sofern zutreffend, von .NET Framework unterstützt.  
  
## Siehe auch  
 [Schemareferenz zu Visual Studio\-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [Erstellen von benutzerdefinierten Projekt\- und Elementvorlagen](../ide/creating-project-and-item-templates.md)   
 [Festlegen einer bestimmten .NET\-Framework\-Zielversion](../ide/targeting-a-specific-dotnet-framework-version.md)