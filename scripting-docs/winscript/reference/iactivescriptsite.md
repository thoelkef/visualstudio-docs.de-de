---
title: Iactivescriptsite | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSite interface
ms.assetid: 4d604a11-5365-46cf-ab71-39b3dbbe9f22
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 56b2a749eb3553044bda5816639498a0682e37e0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570084"
---
# <a name="iactivescriptsite"></a>IActiveScriptSite
Wird vom Host zum Erstellen einer Website für die Windows Script-Engine implementiert. Normalerweise wird diese Site dem Container aller Objekte zugeordnet, die für das Skript sichtbar sind (z. b. die ActiveX-Steuerelemente). In der Regel entspricht dieser Container dem Dokument oder der Seite, die angezeigt wird. Microsoft Internet Explorer würde z. b. einen solchen Container für jede angezeigte HTML-Seite erstellen. Jedes ActiveX-Steuerelement (oder ein anderes Automatisierungs Objekt) auf der Seite und die Skript-Engine selbst können in diesem Container aufgelistet werden.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|||  
|-|-|  
|Methode|Beschreibung|  
|[IActiveScriptSite::GetLCID](../../winscript/reference/iactivescriptsite-getlcid.md)|Ruft den Gebiets Schema Bezeichner ab, der vom Host zum Anzeigen von Elementen der Benutzeroberfläche verwendet wird.|  
|[IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)|Ruft Informationen zu einem Element ab, das einer Engine durch einen-Rückruf der [IActiveScript:: addnameditem](../../winscript/reference/iactivescript-addnameditem.md) -Methode hinzugefügt wurde.|  
|[IActiveScriptSite::GetDocVersionString](../../winscript/reference/iactivescriptsite-getdocversionstring.md)|Ruft eine vom Host definierte Zeichenfolge ab, die die aktuelle Dokument Version aus der Sicht des Hosts eindeutig identifiziert.|  
|[IActiveScriptSite::OnScriptTerminate](../../winscript/reference/iactivescriptsite-onscriptterminate.md)|Wird aufgerufen, wenn die Ausführung des Skripts abgeschlossen ist.|  
|[IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)|Benachrichtigt den Host, dass die Skript-Engine den Status geändert hat.|  
|[IActiveScriptSite::OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md)|Benachrichtigt den Host, dass während der Ausführung des Skripts durch die Engine ein Ausführungsfehler aufgetreten ist.|  
|[IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md)|Informiert den Host, dass die Skript-Engine mit der Ausführung des Skriptcodes begonnen hat.|  
|[IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md)|Benachrichtigt den Host, dass die Skript-Engine von der Ausführung von Skriptcode zurückgegeben hat.|  
  
## <a name="see-also"></a>Siehe auch  
 [Active Script-Schnittstellen](../../winscript/reference/active-script-interfaces.md)