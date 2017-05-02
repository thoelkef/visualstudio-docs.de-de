---
title: "IDebugApplicationNode-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationNode-Schnittstelle"
ms.assetid: 30be3a97-8191-45ac-8706-3f7056c163d6
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugApplicationNode-Schnittstelle
Die `IDebugApplicationNode`\-Schnittstelle erweitert die Funktionalität der `IDebugDocumentProvider`\-Schnittstelle, indem sie einen Kontext innerhalb einer Projektstruktur bereitstellt.  
  
 Zusätzlich zu den von `IDebugDocumentProvider` geerbten Methoden macht die `IDebugApplicationNode`\-Schnittstelle die folgenden Methoden verfügbar.  
  
## Methoden in der vtab\-Reihenfolge  
  
|Methode|Description|  
|-------------|-----------------|  
|[IDebugApplicationNode::EnumChildren](../../winscript/reference/idebugapplicationnode-enumchildren.md)|Listet die untergeordneten Knoten des Anwendungsknotens auf.|  
|[IDebugApplicationNode::GetParent](../../winscript/reference/idebugapplicationnode-getparent.md)|Gibt den übergeordneten Knoten dieses Anwendungsknotens zurück.|  
|[IDebugApplicationNode::SetDocumentProvider](../../winscript/reference/idebugapplicationnode-setdocumentprovider.md)|Legt den Dokumentenanbieter für diesen Anwendungsknoten fest.|  
|[IDebugApplicationNode::Close](../../winscript/reference/idebugapplicationnode-close.md)|Verursacht diese Anwendung, alle Verweise freizugeben und einen inaktiven Zustand übergeht.|  
|[IDebugApplicationNode::Attach](../../winscript/reference/idebugapplicationnode-attach.md)|Fügt der angegebenen diesen Anwendungsknoten Projektstruktur hinzu.|  
|[IDebugApplicationNode::Detach](../../winscript/reference/idebugapplicationnode-detach.md)|Entfernt den Anwendungsknoten aus der Projektstruktur.|