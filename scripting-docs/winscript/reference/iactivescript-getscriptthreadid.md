---
title: "IActiveScript::GetScriptThreadID | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.GetScriptThreadID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_GetScriptThreadID"
ms.assetid: 2595d76e-30b5-429f-88b4-1d026645dd9b
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScript::GetScriptThreadID
Ruft einen Skripterstellung\-Modul\-definierten Bezeichner für den Thread ab, der mit dem angegebenen Win32\-Thread zugeordnet ist.  
  
## Syntax  
  
```  
HRESULT GetScriptThreadID(  
    DWORD dwWin32ThreadID,       // Win32 thread identifier.  
    SCRIPTTHREADID *pstidThread  // Receives scripting thread. identifier  
);  
```  
  
#### Parameter  
 `dwWin32ThreadID` ,  
 \[in\] Threadbezeichner eines laufenden Win32\-Threads im aktuellen Prozess.  Verwenden Sie die [IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)\-Funktion, um den Threadbezeichner des momentan ausgeführten Threads abzurufen.  
  
 `pstidThread` ,  
 \[out\] Zugeordnete Adresse einer Variablen, die den Skriptthreadbezeichner empfängt, mit dem angegebenen Win32\-Thread zu.  Die Darstellung dieses Bezeichners wird dem Skriptmodul überlassen, kann jedoch nur eine Kopie des Windows\-Threadbezeichners sein.  Beachten Sie, dass, wenn der Win32\-Thread endet, dieser Bezeichner wird möglicherweise nicht zugewiesen und anschließend zu einem anderen Thread zugewiesen ist.  
  
## Rückgabewert  
 Gibt eine der folgenden Werte:  
  
|Rückgabewert|Bedeutung|  
|------------------|---------------|  
|`S_OK`|Erfolgreich.|  
|`E_POINTER`|Ein ungültiger Zeiger wurde angegeben.|  
|`E_UNEXPECTED`|Der Aufruf wurde nicht erwartet \(beispielsweise, ist das Skriptmodul noch nicht geladen wurde oder initialisiert wurden\) und fehlgeschlagen ist daher.|  
  
## Hinweise  
 Der abgerufene Bezeichner kann in nachfolgenden Aufrufen verwendet werden, um Threadausführungssteuerungsmethoden wie die [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)\-Methode zu erstellen.  
  
 Diese Methode kann von NichtBasis Threads mit dem Ergebnis einer NichtBasis Legende zu den Hostobjekten oder zur [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)\-Schnittstelle ohne aufgerufen werden.  
  
## Siehe auch  
 [IActiveScript](../../winscript/reference/iactivescript.md)