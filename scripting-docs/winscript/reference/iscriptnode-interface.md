---
title: IScriptNode-Schnittstelle | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IScriptNode interface
ms.assetid: cfa76c4a-6543-48e8-a946-d212cd0bf934
caps.latest.revision: "21"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 788be3fe9cb5ba529e3d1ca653d4f0f5c35b5932
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptnode-interface"></a>IScriptNode-Schnittstelle
Ein Objekt, implementiert die `IScriptNode` Schnittstelle stellt eine Webseite dar.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IScriptNode` Schnittstelle macht die folgenden Methoden verfügbar.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IScriptNode::Alive](../../winscript/reference/iscriptnode-alive.md)|Gibt an, ob ein Objekt noch aktiv ist.|  
|[IScriptNode:: CreateChildEntry](../../winscript/reference/iscriptnode-createchildentry.md)|Fügt eine untergeordnete Instanz `IScriptEntry`.|  
|[IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md)|Fügt eine Scriptlet als untergeordnete Instanz von einem `IScriptNode`.|  
|[IScriptNode::Delete](../../winscript/reference/iscriptnode-delete.md)|Löscht die Baumstruktur im Objekt.|  
|[IScriptNode::GetChild](../../winscript/reference/iscriptnode-getchild.md)|Gibt das untergeordnete Element, das am angegebenen Index im Knoten "" ist.|  
|[IScriptNode::GetCookie](../../winscript/reference/iscriptnode-getcookie.md)|Gibt einen anwendungsdefinierten Wert, der verwendet wird, das Hostobjekt, das Scriptlet zugeordnet werden soll.|  
|[IScriptNode::GetIndexInParent](../../winscript/reference/iscriptnode-getindexinparent.md)|Gibt den Index eines Objekts in die untergeordnete Liste des übergeordneten Elements zurück.|  
|[IScriptNode::GetLanguage](../../winscript/reference/iscriptnode-getlanguage.md)|Gibt die Skriptsprache, die vom aktuellen Knoten Skript verwendet wird.|  
|[IScriptNode::GetNumberOfChildren](../../winscript/reference/iscriptnode-getnumberofchildren.md)|Gibt die Anzahl der untergeordneten Knoten des der `IScriptNode` Objekt.|  
|[IScriptNode::GetParent](../../winscript/reference/iscriptnode-getparent.md)|Gibt die `IScriptNode` -Objekt, das das übergeordnete Element eines Objekts ist.|  
  
## <a name="see-also"></a>Siehe auch  
 [Active Script-Autorisierungsschnittstellen](../../winscript/reference/active-script-authoring-interfaces.md)