---
title: "CommandPlacements-Element | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CommandPlacements"
helpviewer_keywords: 
  - "CommandPlacements-Element (VSCT-XML-Schema)"
  - "VSCT XML-Schemaelemente, CommandPlacements"
ms.assetid: 78a5724a-3b9f-4c78-9c0d-8faa3924f81c
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# CommandPlacements-Element
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Das Element CommandPlacements Gruppen CommandPlacement Elemente und CommandPlacements b.  
  
 Das CommandPlacements\-Element ist optional. Wenn keine Befehle, Gruppen oder Menüs an einem sekundären Standort berücksichtigt werden müssen, müssen Sie keinen dieser Abschnitt in der VSCT\-Datei enthalten.  
  
## Syntax  
  
```  
<CommandPlacements>  
  <CommandPlacement>... </CommandPlacement>  
  <CommandPlacement>... </CommandPlacement>  
</CommandPlacements>  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|Bedingung|Optional. Siehe [Bedingten Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|CommandPlacements|Gruppen CommandPlacement Elementen und anderen CommandPlacements Gruppierungen.|  
|[CommandPlacement\-Element](../extensibility/commandplacement-element.md)|Ermöglicht es, Schaltflächen, Gruppen und Menüs in mehr als eine Gruppe oder einem Menü enthalten sein.|  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[CommandTable\-Element](../extensibility/commandtable-element.md)|Definiert die Elemente aus, die Befehle darstellen.|  
  
## Beispiel  
  
```  
<CommandPlacements> <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions" priority="0x0300"> <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/> </CommandPlacement> </CommandPlacements>  
```  
  
## Siehe auch  
 [CommandPlacement\-Element](../extensibility/commandplacement-element.md)   
 [Visual Studio\-Befehl\-Tabelle \(. VSCT\) Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)