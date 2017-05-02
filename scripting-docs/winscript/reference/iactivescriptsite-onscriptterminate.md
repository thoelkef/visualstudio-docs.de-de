---
title: "IActiveScriptSite::OnScriptTerminate | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.OnScriptTerminate
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite::OnScriptTerminate"
ms.assetid: 3301ddf4-5929-404c-81d3-1a720e589008
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::OnScriptTerminate
Informiert den Host, dass das Skript die Ausführung abgeschlossen hat.  
  
## Syntax  
  
```  
HRESULT OnScriptTerminate(  
    VARIANT *pvarResult,   // address of script results  
    EXCEPINFO *pexcepinfo  // address of structure with exception information  
);  
```  
  
#### Parameter  
 `pvarResult`  
 \[in\] Adresse einer Variablen, die das Skriptergebnis enthält oder `NULL`, wenn das Skript kein Ergebnis geliefert hat.  
  
 `pexcepinfo`  
 \[in\] Generierte Adresse einer `EXCEPINFO`\-Struktur, die Ausnahmeinformationen enthält, als Skript beendet wurde oder `NULL`, wenn keine Ausnahme ausgelöst wurde.  
  
## Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK` zurückgegeben.  
  
## Hinweise  
 Das Skriptmodul ruft diese Methode auf, bevor der Aufruf der [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)\-Methode, mit dem SCRIPTSTATE\_INITIALIZED\-Flagssatz, abgeschlossen wird.  Diese Methode kann verwendet werden, um Abschlussstatus und Ergebnisse an den Host zurückzugeben.  Beachten Sie, dass viele Skriptsprachen, die auf Grundlage sinkende Ereignisse vom Host sind, Lebensdauer haben, die vom Host definiert werden.  In diesem Fall wird diese Methode möglicherweise nie aufgerufen.  
  
## Siehe auch  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)