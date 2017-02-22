---
title: "Parent-Element | Microsoft Docs"
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
  - "VSCT XML-Schemaelemente, übergeordneten"
  - "Übergeordnetes Element (VSCT-XML-Schema)"
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# Parent-Element
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Das übergeordnete Element eines Felds Schaltfläche oder ein Kombinationsfeld kann nur eine Gruppe sein. Das übergeordnete Element eines Menüs oder einer Gruppe kann einem anderen Menü oder einer Gruppe sein. In einem [CommandPlacement\-Element](../extensibility/commandplacement-element.md), dieses Element ist erforderlich; alle anderen Instanzen ist optional. Wenn dieses Element nicht angegeben ist, das übergeordnete Element des `Group_Undefined:0` wird impliziert werden.  
  
## Syntax  
  
```  
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|GUID|Erforderlich. GUID der GUID\/ID Befehlsbezeichner.|  
|ID|Erforderlich. ID der GUID\/ID Befehlsbezeichner.|  
  
### Untergeordnete Elemente  
 Keine  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[CommandTable\-Element](../extensibility/commandtable-element.md)|Definiert die Elemente aus, die Befehle, die ein VSPackage bietet auf der integrated Development Environment \(IDE\) darstellen. Z. B. Menüelemente, Menüs, Symbolleisten und Kombinationsfelder.|  
|[Schaltflächen\-Element](../extensibility/buttons-element.md)|Gruppiert [Button\-Element](../extensibility/button-element.md)\-Elemente.|  
|[Menüs\-Element](../extensibility/menus-element.md)|Definiert alle Menüs, die ein VSPackage implementiert.|  
|[Groups\-Element](../extensibility/groups-element.md)|Enthält Einträge, die die Befehl Benutzergruppen ein VSPackage definieren.|  
  
## Siehe auch  
 [Visual Studio\-Befehl\-Tabelle \(. VSCT\) Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)