---
title: "IActiveScriptSite::OnEnterScript | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.OnEnterScript
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_OnEnterScript"
ms.assetid: 1ed9178c-fe80-41c4-b74d-23b85f9cddbf
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::OnEnterScript
Informiert den Host, dass das Skriptmodul gestartet wurde, den Skriptcode ausgeführt wird.  
  
## Syntax  
  
```  
HRESULT OnEnterScript(void);  
```  
  
## Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK` zurückgegeben.  
  
## Hinweise  
 Das Skriptmodul muss diese Methode auf jedem Eintrag oder Wiedereintritt im Skriptmodul aufrufen.  Wenn das Skript ein Objekt aufgerufen wird, das dann ein Ereignis auslöst, das durch das Skriptmodul behandelt wird, muss das Skriptmodul `IActiveScriptSite::OnEnterScript`, bevor das Ereignis aufrufen ausführt, und muss die [IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md)\-Methode aufrufen, nachdem das Ereignis jedoch ausgeführt hat, bevor es an das Objekt zurückgibt, das das Ereignis ausgelöst hat.  Aufrufe dieser Methode können geschachtelt werden.  Jeder Aufruf dieser Methode erfordert einen entsprechenden Aufruf von `IActiveScriptSite::OnLeaveScript`.  
  
## Siehe auch  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)