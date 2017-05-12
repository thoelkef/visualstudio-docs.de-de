---
title: "IActiveScriptSiteInterruptPoll::QueryContinue | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteInterruptPoll.QueryContinue
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteInterruptPoll::QueryContinue"
ms.assetid: 41ac3807-f8b4-4a0e-bcc6-556bc89f3904
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteInterruptPoll::QueryContinue
Ermöglicht einem Host, um anzugeben, dass ein Skript beendet werden soll.  
  
## Syntax  
  
```  
HRESULT QueryContinue();  
```  
  
#### Parameter  
 Diese Methode verwendet keine Parameter.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Der Aufruf erfolgreich war und der Host ermöglicht das Skript, mit denen.|  
|`S_FALSE`|Der Aufruf erfolgreich war und die Hostanforderungen, die das Skript beenden.|  
  
## Hinweise  
 Das gehostete Skript sollte beendet werden, es sei denn, der Rückgabewert der Methode `QueryContinue``S_OK` ist.  Ein Rückgabewert von `S_FALSE` gibt die Anforderungen des Hosts explizit an, die das Skript beenden.  
  
 Ein Multithreaddesigns Host verwendet möglicherweise die `IActiveScript::InterruptScriptThread`\-Methode, um ein Skript zu beenden.  
  
## Siehe auch  
 [IActiveScriptSiteInterruptPoll\-Schnittstelle](../../winscript/reference/iactivescriptsiteinterruptpoll-interface.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)