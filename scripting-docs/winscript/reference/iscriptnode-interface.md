---
title: Iscriptnode-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IScriptNode interface
ms.assetid: cfa76c4a-6543-48e8-a946-d212cd0bf934
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 38ab73ddb1bd924035cb6ba61d26e65f16f53eed
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577518"
---
# <a name="iscriptnode-interface"></a>IScriptNode-Schnittstelle
Ein Objekt, das die `IScriptNode`-Schnittstelle implementiert, stellt eine Webseite dar.  
  
 Zusätzlich zu den Methoden, die von `IUnknown` geerbt werden, macht die `IScriptNode`-Schnittstelle die folgenden Methoden verfügbar.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IScriptNode::Alive](../../winscript/reference/iscriptnode-alive.md)|Gibt an, ob ein Objekt noch aktiv ist.|  
|[IScriptNode:: CreateChildEntry](../../winscript/reference/iscriptnode-createchildentry.md)|Fügt eine untergeordnete Instanz von `IScriptEntry` hinzu.|  
|[IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md)|Fügt ein Scriptlet als untergeordnete Instanz eines `IScriptNode` hinzu.|  
|[IScriptNode::Delete](../../winscript/reference/iscriptnode-delete.md)|Löscht die Objektstruktur.|  
|[IScriptNode::GetChild](../../winscript/reference/iscriptnode-getchild.md)|Gibt das untergeordnete Element zurück, das sich am angegebenen Index im Knoten befindet.|  
|[IScriptNode::GetCookie](../../winscript/reference/iscriptnode-getcookie.md)|Gibt einen von der Anwendung definierten Wert zurück, der verwendet wird, um ein Scriptlet dem Host Objekt zuzuordnen.|  
|[IScriptNode::GetIndexInParent](../../winscript/reference/iscriptnode-getindexinparent.md)|Gibt den Index eines Objekts in der untergeordneten Liste des übergeordneten Elements zurück.|  
|[IScriptNode::GetLanguage](../../winscript/reference/iscriptnode-getlanguage.md)|Gibt die Skriptsprache zurück, die vom aktuellen Skript Knoten verwendet wird.|  
|[IScriptNode::GetNumberOfChildren](../../winscript/reference/iscriptnode-getnumberofchildren.md)|Gibt die Anzahl der untergeordneten Knoten des `IScriptNode`-Objekts zurück.|  
|[IScriptNode::GetParent](../../winscript/reference/iscriptnode-getparent.md)|Gibt das `IScriptNode` Objekt zurück, das dem-Objekt übergeordnet ist.|  
  
## <a name="see-also"></a>Siehe auch  
 [Active Script-Autorisierungsschnittstellen](../../winscript/reference/active-script-authoring-interfaces.md)