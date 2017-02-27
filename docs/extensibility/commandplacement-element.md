---
title: "CommandPlacement-Element | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CommandPlacements-Element (VSCT-XML-Schema)"
  - "VSCT XML-Schemaelemente, CommandPlacements"
ms.assetid: 2cbd7ac8-c55a-43d8-a26d-713b3d790016
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# CommandPlacement-Element
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Das Element CommandPlacement kann Schaltflächen, Gruppen und Menüs in mehr als eine Gruppe oder einem Menü enthalten sein. Verwenden Sie das CommandPlacement\-Element, müssen Sie keinen dieser Elemente vollständig neu definieren, um die Darstellung einer Benutzeroberfläche zu ändern.  
  
 Weitere Informationen finden Sie unter [Erstellen von wieder verwendbaren Gruppen von Schaltflächen](../extensibility/creating-reusable-groups-of-buttons.md).  
  
## Syntax  
  
```  
<CommandPlacement guid=guidMyCommandSet" id="MyCommand" priority="0x001" >  
  <Parent>... </Parent>  
</CommandPlacement>  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|GUID|Erforderlich. Die Guid für den Befehlssatz, gemäß der [Symbole\-Element](../extensibility/symbols-element.md).|  
|ID|Erforderlich. Die Id der Menüs, die Gruppe oder den Befehl platziert werden, wie in definiert, und die `Symbols Element`.|  
|priority|Erforderlich. Bestimmt die sichtbare Position des Elements in seinem übergeordneten Element.|  
|Bedingung|Optional. Siehe [Bedingten Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|Übergeordnetes Element|Erforderlich. Die im Menü oder die Gruppe, der das Element platziert werden hostet.|  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[CommandPlacements\-Element](../extensibility/commandplacements-element.md)|Gibt Gruppen von CommandPlacements und CommandPlacement\-Elemente.|  
  
## Beispiel  
  
```  
<CommandPlacements> <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions" priority="0x0300"> <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/> </CommandPlacement> </CommandPlacements>  
```  
  
## Siehe auch  
 [CommandPlacements\-Element](../extensibility/commandplacements-element.md)   
 [Visual Studio\-Befehl\-Tabelle \(. VSCT\) Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)