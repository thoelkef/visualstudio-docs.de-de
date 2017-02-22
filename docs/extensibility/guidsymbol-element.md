---
title: "GuidSymbol-Element | Microsoft Docs"
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
  - "VSCT XML-Schemaelemente, GuidSymbol"
  - "GuidSymbol-Element (VSCT-XML-Schema)"
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# GuidSymbol-Element
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die `GuidSymbol` Element enthält die GUID des GUID:ID\-Paar, das ein Menü, eine Gruppe oder ein Befehl darstellt. Die ID stammt aus einer `IDSymbol` Element in der `GuidSymbol` Element. Die `GuidSymbol` Element verfügt über ein `name` \-Attribut, das einen Anzeigenamen für die GUID enthält, das in enthalten ist die `value` Attribut.  
  
## Syntax  
  
```  
<GuidSymbol name="guidMyCommandSet" value="{xxxxxxxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx}">  
  <IDSymbol>... </IDSymbol>  
  <IDSymbol>... </IDSymbol>  
</GuidSymbol>  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|Name|Erforderlich. Der Name der GUID\-Symbol.|  
|Wert|Erforderlich. Die GUID der GUID\-Symbol.|  
  
### Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[IDSymbol\-Element](../extensibility/idsymbol-element.md)|Enthält die ID des GUID:ID\-Paars, die ein Menü, eine Gruppe oder ein Befehl darstellt.|  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[Symbole\-Element](../extensibility/symbols-element.md)|Gruppen `GuidSymbol` Elemente in einer VSCT\-Datei.|  
  
## Hinweise  
 In der Regel eine VSCT\-Datei enthält drei `GuidSymbol` Elemente in der `Symbols` im Abschnitt für das Paket selbst, eine für den Befehl ein \(die Auflistung von Menüs, Gruppen und Befehle, die das Paket zur Verfügung stellt\) und eine für die Bitmaps, die Symbole für Schaltflächen und anderen visuellen Komponenten bereitstellen. Jeder `IDSymbol` Element in einer bestimmten `GuidSymbol` Element muss einen eindeutigen haben `value`. Allerdings `IDSymbol` Elemente mit identischen Werten können in einem Paket existieren, solange sie anderen übergeordneten Objekte verfügen.  
  
## Siehe auch  
 [Visual Studio\-Befehl\-Tabelle \(. VSCT\) Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)