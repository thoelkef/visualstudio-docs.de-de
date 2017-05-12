---
title: "IActiveScript::InterruptScriptThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.InterruptScriptThread
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_InterruptScriptThread"
ms.assetid: 2304d035-6d39-4811-acd3-8a9640fdbef6
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::InterruptScriptThread
Unterteilt die Ausführung eines laufenden Skriptthreads \(eine Ereignissenke, eine unmittelbare Ausführung oder ein Makroaufruf\).  Diese Methode kann verwendet werden, um ein Skript zu beenden, die In wird \(beispielsweise, in einer Endlosschleife\).  Sie kann von NichtBasis Threads mit dem Ergebnis einer NichtBasis Legende zu den Hostobjekten oder zur [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)\-Methode ohne aufgerufen werden.  
  
## Syntax  
  
```  
HRESULT InterruptScriptThread(  
    SCRIPTTHREADID   stidThread,  // identifier of thread  
    const EXCEPINFO *pexcepinfo,  // receives error information  
    DWORD dwFlags  
);  
```  
  
#### Parameter  
 `stidThread`  
 \[in\] beschränkt Bezeichner des Threads zu unterbrechen oder einer des folgenden speziellen Threadbezeichners:  
  
|Wert|Bedeutung|  
|----------|---------------|  
|SCRIPTTHREADID\_ALL|Alle Threads.  Die Unterbrechung wird auf alle laufenden Skriptmethoden nur angewendet.  Beachten Sie, dass es sei denn, der Aufrufer, dass das Skript getrennt wird, der folgende vorbereitete Ereignisursachenskriptcode anfordert, um erneut ausgeführt werden, indem er die [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md)\-Methode mit festgelegten SCRIPTSTATE\_DISCONNECTED\- oder SCRIPTSTATE\_INITIALIZED\-Flags aufgerufen hat.|  
|SCRIPTTHREADID\_BASE|Der Basistyp Thread; das heißt, der Thread, in dem das Skriptmodul instanziiert wurde.|  
|SCRIPTTHREADID\_CURRENT|Der momentan ausführende Thread.|  
  
 `pexcepinfo`  
 \[in\] Adresse einer `EXCEPINFO`\-Struktur, die die Fehlerinformationen enthält, die in den Skript ausgegeben werden sollen.  
  
 `dwFlags`  
 \[in\] Optionsflags zugeordnete der Unterbrechung.  Einer der folgenden Werte ist möglich:  
  
|Wert|Bedeutung|  
|----------|---------------|  
|SCRIPTINTERRUPT\_DEBUG|Wenn Sie unterstützt werden, geben Sie den Debugger des Skriptmoduls am aktuellen Skriptausführungspunkt ein.|  
|SCRIPTINTERRUPT\_RAISEEXCEPTION|Wenn Sie durch die Sprache des Skriptmoduls unterstützt werden, lassen Sie das Skript die Ausnahme behandeln.  Andernfalls wird die Skriptmethode abgebrochen und der Fehlercode wird an den Aufrufer zurückgegeben; das heißt, der Ereignisquellen\- oder Makrofragesteller.|  
  
## Rückgabewert  
 Gibt eine der folgenden Werte:  
  
|Rückgabewert|Bedeutung|  
|------------------|---------------|  
|`S_OK`|Erfolgreich.|  
|`E_INVALIDARG`|Ein Argument war ungültig.|  
|`E_POINTER`|Ein ungültiger Zeiger wurde angegeben.|  
|`E_UNEXPECTED`|Der Aufruf wurde nicht erwartet \(beispielsweise, ist das Skriptmodul noch nicht geladen wurde oder initialisiert wurden\).|  
  
## Siehe auch  
 [IActiveScript](../../winscript/reference/iactivescript.md)