---
title: "IDebugApplication::HandleBreakPoint | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.HandleBreakPoint
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::HandleBreakPoint"
ms.assetid: 97219bdf-a39a-4e69-81ac-4ca2afe77ce5
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::HandleBreakPoint
Veranlasst den aktuellen Thread zu blockieren und sendet eine Benachrichtigung des Haltepunkts an den Debugger IDE.  
  
## Syntax  
  
```  
HRESULT HandleBreakPoint(  
   BREAKREASON         br,  
   BREAKRESUMEACTION*  pbra  
);  
```  
  
#### Parameter  
 `br`  
 \[in\] Der Grund für die Unterbrechung.  
  
 `pbra`  
 \[out\] Aktion zu erhalten, wenn der Debugger die Anwendung fortgesetzt.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Ein Sprachmodul ruft diese Methode im Kontext eines Threads an, einen Haltepunkt trifft.  Diese Methode blockiert den aktuellen Thread und sendet eine Haltepunktbenachrichtigung an den Debugger IDE.  Wenn der Debugger die Anwendung fortgesetzt, gibt der `pbra`\-Parameter an, welche Aktion zu akzeptieren.  
  
> [!NOTE]
>  Das Sprachmodul wird vom Thread aufgerufen werden, um Aufgaben wie auszuführen auflisten Stapelrahmen oder Ausdrücke während des Haltepunkts.  
  
 Diese Methode wird `IApplicationDebugger::onHandleBreakPoint` aufgerufen werden.  
  
## Siehe auch  
 [IDebugApplication\-Schnittstelle](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onHandleBreakPoint](../../winscript/reference/iapplicationdebugger-onhandlebreakpoint.md)   
 [BREAKREASON\-Enumeration](../../winscript/reference/breakreason-enumeration.md)   
 [BREAKRESUMEACTION\-Enumeration](../../winscript/reference/breakresumeaction-enumeration.md)