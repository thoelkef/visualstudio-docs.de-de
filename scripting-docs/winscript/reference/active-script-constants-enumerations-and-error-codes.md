---
title: "Konstanten, Enumerationen und Fehlercodes f&#252;r Active Script | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: aab24471-5817-45c0-be07-ffe4648923ed
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Konstanten, Enumerationen und Fehlercodes f&#252;r Active Script
In diesem Abschnitt werden die Enumerationen und die Fehlercodes, die in Windows\-Skriptmodulen verwendet werden.  
  
## Konstanten  
  
|Konstante|Description|  
|---------------|-----------------|  
|[SCRIPTTHREADID\-Konstanten](../../winscript/reference/scriptthreadid-constants.md)|Gibt den Typ des Threads an.|  
  
## Eigenschaften  
  
|Eigenschaft|Description|  
|-----------------|-----------------|  
|[SCRIPTPROP\_HOSTKEEPALIVE\-Eigenschaft](../../winscript/reference/scriptprop-hostkeepalive-property.md)|Wird verwendet, um, ob das Skriptmodul vollständig betrachtet werden sollte funktionsfähiges festgelegt, wenn ausstehende Verweise gibt.|  
  
## Enumerationen  
  
|Enumeration|Description|  
|-----------------|-----------------|  
|[SCRIPTGCTYPE\-Enumeration](../../winscript/reference/scriptgctype-enumeration.md)|Der Typ der Garbage Collection auszuführen.|  
|[SCRIPTLANGUAGEVERSION\-Enumeration](../../winscript/reference/scriptlanguageversion-enumeration.md)|Gibt die möglichen Skripterstellungsversionen an.|  
|[SCRIPTSTATE\-Enumeration](../../winscript/reference/scriptstate-enumeration.md)|Gibt den Zustand eines Skriptmoduls an.|  
|||  
|[SCRIPTTHREADSTATE\-Enumeration](../../winscript/reference/scriptthreadstate-enumeration.md)|Gibt den Status eines Threads in einem Skriptmodul an.|  
|[SCRIPTTRACEINFO\-Enumeration](../../winscript/reference/scripttraceinfo-enumeration.md)|Stellt das Skriptereignis dar, das aufgezeichnet wird.  Wird in [IActiveScriptSiteTraceInfo::SendScriptTraceInfo\-Methode](../../winscript/reference/iactivescriptsitetraceinfo-sendscripttraceinfo-method.md).|  
|[SCRIPTUICHANDLING\-Enumeration](../../winscript/reference/scriptuichandling-enumeration.md)|Stellt die Methode dar, die das UI\-Steuerelement behandelt werden soll.|  
|[SCRIPTUICITEM\-Enumeration](../../winscript/reference/scriptuicitem-enumeration.md)|Stellt den Typ des Benutzeroberflächenelements dar.  Wird in [IActiveScriptSiteUIControl::GetUIBehavior\-Methode](../../winscript/reference/iactivescriptsiteuicontrol-getuibehavior-method.md).|  
  
## Fehlercodes  
  
|Fehlercode|Description|  
|----------------|-----------------|  
|[SCRIPT\_E\_PROPAGATE\-Fehlercode](../../winscript/reference/script-e-propagate-error-code.md)|Ein Skriptfehler wird an den Aufrufer zurückgegeben, der sich in einem anderen Thread ist.|  
|[SCRIPT\_E\_RECORDED\-Fehlercode](../../winscript/reference/script-e-recorded-error-code.md)|Ein Fehler ist zwischen das Skriptmodul und Host übergeben wurde.|  
|[SCRIPT\_E\_REPORTED\-Fehlercode](../../winscript/reference/script-e-reported-error-code.md)|Das Skriptmodul hat ein Ausnahme an den Host gemeldet.|  
  
## Siehe auch  
 [Active Script\-Schnittstellen](../../winscript/reference/active-script-interfaces.md)