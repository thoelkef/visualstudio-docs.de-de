---
title: "IScriptNode-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IScriptNode-Schnittstelle"
ms.assetid: cfa76c4a-6543-48e8-a946-d212cd0bf934
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# IScriptNode-Schnittstelle
Ein Objekt, das die `IScriptNode`\-Schnittstelle implementiert, stellt eine Webseite dar.  
  
 Zusätzlich zu den von `IUnknown` geerbten Methoden macht die `IScriptNode`\-Schnittstelle die folgenden Methoden verfügbar.  
  
## Methoden in Vtable\-Reihenfolge  
  
|Methode|Description|  
|-------------|-----------------|  
|[IScriptNode::Alive](../../winscript/reference/iscriptnode-alive.md)|Gibt an, ob ein Objekt noch aktiv ist.|  
|[IScriptNode::CreateChildEntry](../../winscript/reference/iscriptnode-createchildentry.md)|Fügt eine untergeordnete Instanz von `IScriptEntry` hinzu.|  
|[IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md)|Fügt ein Skriptlet als untergeordnete Instanz von `IScriptNode` hinzu.|  
|[IScriptNode::Delete](../../winscript/reference/iscriptnode-delete.md)|Löscht die Objektstruktur.|  
|[IScriptNode::GetChild](../../winscript/reference/iscriptnode-getchild.md)|Gibt das untergeordnete Element zurück, das am angegebenen Index im Knoten ist.|  
|[IScriptNode::GetCookie](../../winscript/reference/iscriptnode-getcookie.md)|Gibt einen anwendungsdefinierten Wert zurück, der verwendet wird, um ein Skriptlet mit dem Hostobjekt zuzuordnen.|  
|[IScriptNode::GetIndexInParent](../../winscript/reference/iscriptnode-getindexinparent.md)|Gibt den Index des Objekts in der untergeordneten Liste des übergeordneten Elements.|  
|[IScriptNode::GetLanguage](../../winscript/reference/iscriptnode-getlanguage.md)|Gibt die Skriptsprache zurück, die vom aktuellen Skripts\-Knoten verwendet wird.|  
|[IScriptNode::GetNumberOfChildren](../../winscript/reference/iscriptnode-getnumberofchildren.md)|Gibt die Anzahl der untergeordneten Knoten des `IScriptNode`\-Objekts zurück.|  
|[IScriptNode::GetParent](../../winscript/reference/iscriptnode-getparent.md)|Gibt das `IScriptNode`\-Objekt zurück, das das übergeordnete Element eines Objekts ist.|  
  
## Siehe auch  
 [Active Script\-Autorisierungsschnittstellen](../../winscript/reference/active-script-authoring-interfaces.md)