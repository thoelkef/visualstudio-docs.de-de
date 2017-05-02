---
title: "IActiveScriptSiteDebug::OnScriptErrorDebug | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteDebug.OnScriptErrorDebug
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteDebug::OnScriptErrorDebug"
ms.assetid: 87f201da-36eb-49a2-b000-e1e1e8c4cdb7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteDebug::OnScriptErrorDebug
Ermöglicht einem Smarthost, um festzustellen, wie Laufzeitfehler behandelt.  
  
## Syntax  
  
```  
HRESULT OnScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug,  
   BOOL*                     pfEnterDebugger,  
   BOOL*                     pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### Parameter  
 `pErrorDebug`  
 \[in\] Der Laufzeitfehler, der aufgetreten ist  
  
 `pfEnterDebugger`  
 \[out\] kennzeichnen Sie das Angeben, ob der Fehler an den Debugger führt, um JIT\-Debuggen durchzuführen.  
  
 `pfCallOnScriptErrorWhenContinuing`  
 \[out\] kennzeichnen Sie das Angeben, ob `IActiveScriptSite::OnScriptError` aufruft, wenn der Benutzer entscheidet, um fortzufahren, ohne Debuggen.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht auf den Wert in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Ein Smarthost kann diese Methode verwenden, um zu bestimmen, wie Laufzeitfehler behandelt.  
  
## Siehe auch  
 [IActiveScriptSiteDebug\-Schnittstelle](../../winscript/reference/iactivescriptsitedebug-interface.md)