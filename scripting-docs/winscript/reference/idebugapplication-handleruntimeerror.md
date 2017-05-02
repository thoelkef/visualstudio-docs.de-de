---
title: "IDebugApplication::HandleRuntimeError | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.HandleRuntimeError
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::HandleRuntimeError"
ms.assetid: f8f3bbaf-09e5-4d01-8a35-f380bc7ff8ed
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::HandleRuntimeError
Veranlasst den aktuellen Thread zu blockieren und sendet eine Benachrichtigung des Fehlers an den Debugger IDE.  
  
## Syntax  
  
```  
HRESULT HandleRuntimeError(  
   IActiveScriptErrorDebug*  pErrorDebug,  
   IActiveScriptSite*        pScriptSite,  
   BREAKRESUMEACTION*        pbra,  
   ERRORRESUMEACTION*        perra,  
   BOOL*                     pfCallOnScriptError  
);  
```  
  
#### Parameter  
 `pErrorDebug`  
 \[in\] Der Fehler, der aufgetreten ist.  
  
 `pScriptSite`  
 \[in\] Die Skriptsite des Threads.  
  
 `pbra`  
 \[out\] Aktion zu erhalten, wenn der Debugger die Anwendung fortgesetzt.  
  
 `perra`  
 \[out\] Aktion zu erhalten, wenn der Debugger die Anwendung fortgesetzt wird, wenn ein Fehler auftritt.  
  
 `pfCallOnScriptError`  
 \[out\] Flag, das `TRUE` ist, wenn das Modul die `IActiveScriptSite::OnScriptError`\-Methode aufruft.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Ein Sprachmodul ruft diese Methode im Kontext eines Threads an, der einen Laufzeitfehler verursacht.  Diese Methode wird der aktuelle Thread zu blockieren und sendet eine an den Debugger IDE zu sendende Fehlerbenachrichtigung.  Wenn der Debugger IDE die Anwendung fortgesetzt, gibt diese Methode mit der auszuführenden Aktion.  
  
> [!NOTE]
>  Während im Laufzeitfehler, wird das Sprachmodul vom Thread aufgerufen werden, um solche Aufgaben wie auszuführen auflisten Stapelrahmen oder Ausdrücke.  
  
## Siehe auch  
 [IDebugApplication\-Schnittstelle](../../winscript/reference/idebugapplication-interface.md)   
 [IActiveScriptErrorDebug\-Schnittstelle](../../winscript/reference/iactivescripterrordebug-interface.md)   
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)   
 [BREAKRESUMEACTION\-Enumeration](../../winscript/reference/breakresumeaction-enumeration.md)   
 [ERRORRESUMEACTION\-Enumeration](../../winscript/reference/errorresumeaction-enumeration.md)