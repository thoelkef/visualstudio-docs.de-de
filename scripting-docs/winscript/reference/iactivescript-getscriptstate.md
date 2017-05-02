---
title: "IActiveScript::GetScriptState | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.GetScriptState
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_GetScriptState"
ms.assetid: 59837f7c-755d-45c4-8194-bd57638fe2e1
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::GetScriptState
Ruft den aktuellen Zustand des Skriptmoduls ab.  Diese Methode kann von NichtBasis Threads mit dem Ergebnis einer NichtBasis Legende zu den Hostobjekten oder zur [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)\-Schnittstelle ohne aufgerufen werden.  
  
## Syntax  
  
```  
HRESULT GetScriptState(  
    SCRIPTSTATE *pss  // address of structure for state information  
);  
```  
  
#### Parameter  
 `pss`  
 \[out\] Definierte Adresse einer Variablen, die einen Wert empfängt, in der [SCRIPTSTATE\-Enumeration](../../winscript/reference/scriptstate-enumeration.md)\-Enumeration.  Der Wert gibt den aktuellen Zustand des Skriptmoduls an, das mit den aufrufenden Thread zugeordnet ist.  
  
## Rückgabewert  
 Gibt zurück, wenn `S_OK` erfolgreich oder `E_POINTER`, wenn ein ungültiger Zeiger angegeben wurde.  
  
## Siehe auch  
 [IActiveScript](../../winscript/reference/iactivescript.md)