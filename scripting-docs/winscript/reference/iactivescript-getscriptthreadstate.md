---
title: "IActiveScript::GetScriptThreadState | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.GetScriptThreadState
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_GetScriptThreadState"
ms.assetid: 7cac94d0-436e-4c29-895b-0c4afa0b3ccc
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScript::GetScriptThreadState
Ruft den aktuellen Zustand eines Skriptthreads ab.  
  
## Syntax  
  
```  
HRESULT GetScriptThreadState(  
    SCRIPTTHREADID stidThread,    // identifier of script thread  
    SCRIPTTHREADSTATE *pstsState  // receives state flag  
);  
```  
  
#### Parameter  
 `stidThread`  
 \[in\] Bezeichner des Threads, für den der Zustand erforderlich ist oder einer der folgenden speziellen Threadbezeichner:  
  
|Wert|Bedeutung|  
|----------|---------------|  
|SCRIPTTHREADID\_BASE|Der Basistyp Thread; das heißt, der Thread, in dem das Skriptmodul instanziiert wurde.|  
|SCRIPTTHREADID\_CURRENT|Der momentan ausführende Thread.|  
  
 `pstsState`  
 \[out\] Adresse einer Variablen, die den Zustand des angegebenen Threads empfängt.  Der Zustand wird durch einen der Werte der benannten Konstante festgelegt, die in [SCRIPTTHREADSTATE\-Enumeration](../../winscript/reference/scriptthreadstate-enumeration.md)\-Enumeration definiert werden.  Wenn dieser Parameter nicht den aktuellen Thread identifiziert, ändert sich der Zustand jederzeit.  
  
## Rückgabewert  
 Gibt eine der folgenden Werte:  
  
|Rückgabewert|Bedeutung|  
|------------------|---------------|  
|`S_OK`|Erfolgreich.|  
|`E_POINTER`|Ein ungültiger Zeiger wurde angegeben.|  
|`E_UNEXPECTED`|Der Aufruf wurde nicht erwartet \(beispielsweise, ist das Skriptmodul noch nicht geladen wurde oder initialisiert wurden\).|  
  
## Hinweise  
 Diese Methode kann von NichtBasis Threads mit dem Ergebnis einer NichtBasis Legende zu den Hostobjekten oder zur [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)\-Schnittstelle ohne aufgerufen werden.  
  
## Siehe auch  
 [IActiveScript](../../winscript/reference/iactivescript.md)