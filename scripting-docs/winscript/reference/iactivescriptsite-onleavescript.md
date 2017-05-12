---
title: "IActiveScriptSite::OnLeaveScript | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.OnLeaveScript
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_OnLeaveScript"
ms.assetid: 79af0e22-fbe3-4fae-8a5f-7af8b857678d
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::OnLeaveScript
Informiert den Host, dass das Skriptmodul durch Ausführung des Skriptcodes zurückgegeben wird.  
  
## Syntax  
  
```  
HRESULT OnLeaveScript(void);  
```  
  
## Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK` zurückgegeben.  
  
## Hinweise  
 Das Skriptmodul muss diese Methode aufrufen, bevor Steuerelement zu einem aufrufende Anwendung zurückgibt, das das Skriptmodul eingegeben hat.  Wenn das Skript ein Objekt aufgerufen wird, das dann ein Ereignis auslöst, das durch das Skriptmodul behandelt wird, muss das Skriptmodul die [IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md)\-Methode, bevor das Ereignis aufrufen ausführt, und muss `IActiveScriptSite::OnLeaveScript` aufrufen, nachdem das Ereignis ausgeführt hat, bevor es an das Objekt zurückgibt, das das Ereignis ausgelöst hat.  Aufrufe dieser Methode können geschachtelt werden.  Jeder Aufruf von `IActiveScriptSite::OnEnterScript` erfordert einen entsprechenden Aufruf der Methode.  
  
## Siehe auch  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)