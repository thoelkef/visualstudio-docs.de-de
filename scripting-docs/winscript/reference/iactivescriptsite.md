---
title: IActiveScriptSite | Microsoft-Dokumentation
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
ms.openlocfilehash: 67e16e2825f03c9ae452e639d6a086bee584ac95
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58152641"
---
# <a name="iactivescriptsite"></a>IActiveScriptSite
Vom Host zum Erstellen einer Website für die Windows-Skript-Engine implementiert. In der Regel werden diese Website der Container aller Objekte zugeordnet, die an das Skript (z. B. ActiveX-Steuerelemente) sichtbar sind. Dieser Container entsprechen in der Regel in das Dokument oder eine Seite angezeigt wird. Microsoft Internet Explorer würden z. B. solche einen Container für jedes HTML-Seite angezeigt wird erstellen. Jede ActiveX-Steuerelement (oder ein anderes Automatisierungsobjekt) auf der Seite, und die Skript-Engine selbst innerhalb dieses Containers aufzählbare wäre.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|||  
|-|-|  
|Methode|Beschreibung|  
|[IActiveScriptSite::GetLCID](../../winscript/reference/iactivescriptsite-getlcid.md)|Ruft die Gebietsschema-ID, die vom Host verwendet werden, für die Anzeige der Elemente der Benutzeroberfläche ab.|  
|[IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)|Ruft Informationen über ein Element, das ein Modul durch einen Aufruf von hinzugefügt wurde, die [Addnameditem](../../winscript/reference/iactivescript-addnameditem.md) Methode.|  
|[IActiveScriptSite::GetDocVersionString](../../winscript/reference/iactivescriptsite-getdocversionstring.md)|Ruft eine vom Host definierte Zeichenfolge, die eindeutig für die aktuelle Version aus der Sicht des Hosts ab.|  
|[IActiveScriptSite::OnScriptTerminate](../../winscript/reference/iactivescriptsite-onscriptterminate.md)|Wird aufgerufen, wenn das Skript die Ausführung abgeschlossen ist.|  
|[IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)|Informiert den Host, dass die Skript-Engine Status geändert hat.|  
|[IActiveScriptSite::OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md)|Informiert den Host, dass ein Ausführungsfehler aufgetreten, während die Engine das Skript ausgeführt wurde.|  
|[IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md)|Informiert den Host, dass die Skript-Engine begonnen hat, den Skriptcode ausführen.|  
|[IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md)|Informiert, dass die Skript-Engine, vom Ausführen von Skriptcode zurückgegeben hat des Hosts.|  
  
## <a name="see-also"></a>Siehe auch  
 [Active Script-Schnittstellen](../../winscript/reference/active-script-interfaces.md)