---
title: "IDSymbol-Element | Microsoft Docs"
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
  - "IDSymbol-Element (VSCT-XML-Schema)"
  - "VSCT XML-Schemaelemente, IDSymbol"
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDSymbol-Element
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die `IDSymbol` Element enthält die ID des GUID:ID\-Paar, das ein Menü, eine Gruppe oder ein Befehl darstellt. Die GUID wird aus dem übergeordneten `GuidSymbol` Element. Die `IDSymbol` Element verfügt über ein `name` \-Attribut, das einen Anzeigenamen für die ID der in enthalten ist, bietet die `value` Attribut.  
  
## Syntax  
  
```  
<IDSymbol name=ElementName value="0x0010" />  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|Name|Erforderlich. Der Name der ID\-Symbol.|  
|Wert|Erforderlich. Numerische ID\-Wert des ID\-Symbol.|  
  
### Untergeordnete Elemente  
 Keine.  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[GuidSymbol\-Element](../extensibility/guidsymbol-element.md)|Enthält die GUID des GUID:ID\-Paars, die ein Menü, eine Gruppe oder ein Befehl darstellt. Gruppiert `IDSymbol`\-Elemente.|  
  
## Hinweise  
 Jeder `IDSymbol` Element in einer bestimmten `GuidSymbol` Element muss einen eindeutigen haben `value`. Allerdings `IDSymbol` Elemente mit identischen Werten können in einem Paket existieren, solange sie anderen übergeordneten Objekte verfügen.  
  
## Siehe auch  
 [Visual Studio\-Befehl\-Tabelle \(. VSCT\) Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)