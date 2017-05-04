---
title: "IActiveScript::SetScriptState | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.SetScriptState
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_SetScriptState"
ms.assetid: f2b2700c-0c8d-40db-ad84-dc751c5d9bc2
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScript::SetScriptState
Setzt das Skriptmodul in den angegebenen Zustand.  Diese Methode kann von NichtBasis Threads mit dem Ergebnis einer NichtBasis Legende zu den Hostobjekten oder zur [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)\-Schnittstelle ohne aufgerufen werden.  
  
## Syntax  
  
```  
HRESULT SetScriptState(  
    SCRIPTSTATE ss  // identifier of new state  
);  
```  
  
#### Parameter  
 `ss`  
 \[in\] legt das Skriptmodul zum angegebenen Zustand.  Kann einer der Werte, die in der [SCRIPTSTATE\-Enumeration](../../winscript/reference/scriptstate-enumeration.md)\-Enumeration definiert werden.  
  
## Rückgabewert  
 Gibt eine der folgenden Werte:  
  
|Rückgabewert|Bedeutung|  
|------------------|---------------|  
|`S_OK`|Erfolgreich.|  
|`E_FAIL`|Das Skriptmodul unterstützt den Übergang nicht zurück zum initialisierten Zustand.  Der Host muss dieses Skriptmodul verwerfen und ein neues Skriptmodul erstellen, initialisieren und laden, um die gleichen Effekt zu erzielen.|  
|`E_UNEXPECTED`|Der Aufruf wurde nicht erwartet \(beispielsweise, ist das Skriptmodul noch nicht geladen wurde oder initialisiert wurden\) und fehlgeschlagen ist daher.|  
|`OLESCRIPT_S_PENDING`|Die Methode wurde erfolgreich in die Warteschlange gestellt, aber der Zustand noch nicht geändert.  Wenn die Zustandsänderungen, die Site hinter durch die [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)\-Methode aufgerufen werden.|  
|`S_FALSE`|Die gefolgte Methode, aber das Skript waren bereits im angegebenen Zustand.|  
  
## Hinweise  
 Weitere Informationen zu Skriptmodulzustände, finden Sie im Skriptmodul\-Zustandsabschnitt von [Windows Script\-Module](../../winscript/windows-script-engines.md).  
  
## Siehe auch  
 [IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)   
 [IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)   
 [IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)   
 [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)