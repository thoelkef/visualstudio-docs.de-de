---
title: "IActiveScriptSite | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptSite-Schnittstelle"
ms.assetid: 4d604a11-5365-46cf-ab71-39b3dbbe9f22
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite
Wird von den Host, um eine Website für die Windows Script\-Modul zu erstellen.  Normalerweise wird diese Site mit dem Container aller Objekte zugeordnet, die dem Skript sichtbar sind \(beispielsweise, die ActiveX\-Steuerelemente\).  In der Regel entspricht dieser Container zum Dokument oder Seite, die angezeigt wird.  Microsoft Internet Explorer beispielsweise würde einen solchen Container für jede HTML\-Seite erstellen, die angezeigt wurde.  Jedes ActiveX\-Steuerelement \(oder anderen Automatisierungsobjekt\) auf der Seite und das Skriptmodul selbst, werden innerhalb dieses Containers aufzählbar sein.  
  
## Methoden in Vtable\-Reihenfolge  
  
|||  
|-|-|  
|Methode|Description|  
|[IActiveScriptSite::GetLCID](../../winscript/reference/iactivescriptsite-getlcid.md)|Ruft den Gebietsschemabezeichner ab, den der Host zum Anzeigen von Benutzeroberflächenelementen verwendet.|  
|[IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)|Informationen über ein Element, das einem Modul durch einen Aufruf der Methode [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) hinzugefügt wurde.|  
|[IActiveScriptSite::GetDocVersionString](../../winscript/reference/iactivescriptsite-getdocversionstring.md)|Ruft eine Zeichenfolge ab, die Host\-definierte eindeutig die Version des aktuellen Dokuments aus Sicht des Hosts identifiziert.|  
|[IActiveScriptSite::OnScriptTerminate](../../winscript/reference/iactivescriptsite-onscriptterminate.md)|Wird aufgerufen, wenn das Skript die Ausführung abgeschlossen hat.|  
|[IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)|Informiert den Host, dass das Skriptmodul Zustände geändert hat.|  
|[IActiveScriptSite::OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md)|Informiert den Host, dass ein Ausführungsfehler aufgetreten ist, während das Modul das Skript ausgeführt hat.|  
|[IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md)|Informiert den Host, dass das Skriptmodul gestartet wurde, den Skriptcode ausgeführt wird.|  
|[IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md)|Informiert den Host, dass das Skriptmodul durch Ausführung des Skriptcodes zurückgegeben wird.|  
  
## Siehe auch  
 [Active Script\-Schnittstellen](../../winscript/reference/active-script-interfaces.md)