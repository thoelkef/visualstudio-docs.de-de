---
title: IActiveScriptSite | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSite interface
ms.assetid: 4d604a11-5365-46cf-ab71-39b3dbbe9f22
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c23dba403a7889fe46817a21ed8e4be65b1c05b4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsite"></a>IActiveScriptSite
Vom Host zum Erstellen einer Website für die Windows-Skriptmodul implementiert. In der Regel werden diese Website mit dem Container aller Objekte verknüpft, die für das Skript (z. B. ActiveX-Steuerelemente) sichtbar sind. In der Regel entspricht dieses Containers in das Dokument oder die Seite angezeigt wird. Microsoft Internet Explorer, würden z. B. solche einen Container für jede HTML-Seite angezeigt wird erstellen. Jede ActiveX-Steuerelement (oder andere Automatisierungsobjekt) auf der Seite und dem Skriptmodul selbst innerhalb dieses Containers aufzählbare wäre.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|||  
|-|-|  
|Methode|Beschreibung|  
|[IActiveScriptSite::GetLCID](../../winscript/reference/iactivescriptsite-getlcid.md)|Ruft die Gebietsschema-ID, die vom Host verwendet werden, für die Anzeige von Benutzeroberflächenelementen ab.|  
|[IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)|Ruft Informationen über ein Element, das ein Modul durch einen Aufruf von hinzugefügte der [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) Methode.|  
|[IActiveScriptSite::GetDocVersionString](../../winscript/reference/iactivescriptsite-getdocversionstring.md)|Ruft eine Zeichenfolge mit Host definiert, die eindeutig für die aktuelle Dokumentversion aus Sicht des Hosts ab.|  
|[IActiveScriptSite::OnScriptTerminate](../../winscript/reference/iactivescriptsite-onscriptterminate.md)|Wird aufgerufen, wenn das Skript die Ausführung abgeschlossen wurde.|  
|[IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)|Benachrichtigt den Host, dass das Skriptmodul Status geändert hat.|  
|[IActiveScriptSite::OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md)|Informieren dem Host, dass ein Ausführungsfehler aufgetreten, während das Modul, das Skript ausgeführt wurde.|  
|[IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md)|Benachrichtigt den Host, dass das Skriptmodul begonnen hat den Skriptcode ausführen.|  
|[IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md)|Benachrichtigt den Host, dass das Skriptmodul von Skriptcode ausführen zurückgegeben hat.|  
  
## <a name="see-also"></a>Siehe auch  
 [Active Script-Schnittstellen](../../winscript/reference/active-script-interfaces.md)