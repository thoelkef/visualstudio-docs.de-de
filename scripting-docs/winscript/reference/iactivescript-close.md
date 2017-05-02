---
title: "IActiveScript::Close | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.Close
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_Close"
ms.assetid: cc7dd63b-1d7e-410a-857b-09ea3aade275
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScript::Close
Veranlasst das Skriptmodul, um jedes aktuell geladene Skript abzubrechen, seinen Zustand zu verlieren und alle Schnittstellenzeiger freizugeben, die es andere Objekte muss und so gibt einen geschlossenen Zustand.  Ereignissenken, sofort ausgeführter Skripttext und Makroaufrufe, die bereits ausgeführt werden, werden vor den Zustandsänderungen abgeschlossen \(Verwendung [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md), einen laufenden Skriptthread abgebrochen\).  Diese Methode muss vom erstellenden Host aufgerufen werden, bevor die Schnittstelle freigegeben wird, um Zirkelverweisprobleme zu verhindern.  
  
## Syntax  
  
```  
HRESULT Close(void);  
```  
  
## Rückgabewert  
 Gibt eine der folgenden Werte:  
  
|Wert|Bedeutung|  
|----------|---------------|  
|`S_OK`|Erfolgreich.|  
|`E_UNEXPECTED`|Der Aufruf wurde nicht erwartet \(beispielsweise, konnte das Skriptmodul bereits im Zustand "\).|  
|`OLESCRIPT_S_PENDING`|Die Methode wurde erfolgreich in die Warteschlange gestellt, aber der Zustand noch nicht geändert.  Wenn die Zustandsänderungen, die Site hinter aufgerufen werden soll [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) auf der Methode.|  
|`S_FALSE`|Die gefolgte Methode, das Skript ist bereits geschlossen.|  
  
## Siehe auch  
 [IActiveScript](../../winscript/reference/iactivescript.md)