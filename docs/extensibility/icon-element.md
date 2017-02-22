---
title: "Icon-Element | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSCT XML-Schemaelemente, Symbol"
  - "Icon-Element (VSCT-XML-Schema)"
ms.assetid: 73c58fe3-d53c-4f4e-b025-29567c6cbb7c
caps.latest.revision: 5
caps.handback.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
---
# Icon-Element
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Das Guid\-Attribut des Tags Symbol ist die Guid einer definierten Bitmap.  Das Id\-Attribut markiert den Slot im Bitmap Balken. Dieses Element ist optional.  Wenn dieses Element nicht angegeben, wird der Wert des **guidOfficeIcon:msotcidNoIcon** wird impliziert werden.  
  
## Syntax  
  
```  
<Icon guid="guidImages" id="bmpPic1" />  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|GUID|Erforderlich. Die Guid einer definierten Bitmap.|  
|ID|Erforderlich. Wählt den Slot in der Bitmap Streifen.|  
  
### Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|Keine.|Keine|  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[Schaltflächen\-Element](../extensibility/buttons-element.md)||  
  
## Siehe auch  
 [Visual Studio\-Befehl\-Tabelle \(. VSCT\) Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)