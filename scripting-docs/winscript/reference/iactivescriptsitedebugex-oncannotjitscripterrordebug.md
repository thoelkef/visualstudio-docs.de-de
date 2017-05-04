---
title: "IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteDebugEx.OnCanNotJITScriptErrorDebug
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug"
ms.assetid: 83f81476-bf12-47f2-897d-1d37d21137d4
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
Informiert den Host über einen Skriptlaufzeitfehler, wenn der Prozessdebug\-Manager keinen Just\-in\-timeskriptdebugger sucht.  
  
 Um einen Debugger im Host zu implementieren, sollten Sie [IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md) behandeln.  Auf Grundlage eine Benutzeraktion Host kann entweder den Debugger und die Rückgabe anfügen, oder geben Sie das Starten des Debuggers im Parameter OnScriptErrorDebug `pfEnterDebugger` zurück.  Sie sollten diese Schnittstelle implementieren, um die Benachrichtigung über den Laufzeitfehler abzurufen, auch wenn keine externen Debugger gibt, die vom Prozessdebug\-Manager interpretiert werden.  
  
## Syntax  
  
```  
HRESULT OnCanNotJITScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug  
   BOOL *pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### Parameter  
 `pErrorDebug`  
 \[in\] Der Laufzeitfehler, der aufgetreten ist.  
  
 `pfCallOnScriptErrorWhenContinuingt`  
 \[out\] ob [IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md) aufruft, wenn der Benutzer entscheidet, um fortzufahren, ohne Debuggen.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Sie sollten diese Schnittstelle implementieren, um eine Benachrichtigung abzurufen.  
  
## Siehe auch  
 [IActiveScriptSiteDebugEx\-Schnittstelle](../../winscript/reference/iactivescriptsitedebugex-interface.md)