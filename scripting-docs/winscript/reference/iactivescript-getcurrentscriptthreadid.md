---
title: "IActiveScript::GetCurrentScriptThreadID | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.GetCurrentScriptThreadID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_GetCurrentScriptThreadID"
ms.assetid: b09e8b48-4209-480e-8b71-e99ee9ae2e17
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::GetCurrentScriptThreadID
Ruft einen Skripterstellung\-Modul\-definierten Bezeichner für den aktuell ausgeführten Thread ab.  Der Bezeichner kann in nachfolgenden Aufrufen verwendet werden, um Threadausführungssteuerungsmethoden wie die [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)\-Methode zu erstellen.  
  
## Syntax  
  
```  
HRESULT GetCurrentScriptThreadID(  
    SCRIPTTHREADID *pstidThread  // receives scripting thread identifier  
);  
```  
  
#### Parameter  
 `pstidThread`  
 \[out\] Zugeordnete Adresse einer Variablen, die den Skriptthreadbezeichner empfängt, dem aktuellen Thread zu.  Die Darstellung dieses Bezeichners wird dem Skriptmodul überlassen, kann jedoch nur eine Kopie des Windows\-Threadbezeichners sein.  Wenn der Win32\-Thread endet, wird der Bezeichner nicht zugewiesen und kann zu einem anderen Thread anschließend zugewiesen werden.  
  
## Rückgabewert  
 Gibt zurück, wenn `S_OK` erfolgreich oder `E_POINTER`, wenn ein ungültiger Zeiger angegeben wurde.  
  
## Hinweise  
 Diese Methode kann von NichtBasis Threads mit dem Ergebnis einer NichtBasis Legende zu den Hostobjekten oder zur [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)\-Schnittstelle ohne aufgerufen werden.  
  
## Siehe auch  
 [IActiveScript](../../winscript/reference/iactivescript.md)