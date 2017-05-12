---
title: "IApplicationDebugger::onHandleBreakPoint | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IApplicationDebugger.onHandleBreakPoint
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IApplicationDebugger::onHandleBreakPoint"
ms.assetid: 31adcecd-d6c1-4222-ab2c-32ec2fefb322
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IApplicationDebugger::onHandleBreakPoint
Behandelt ein Haltepunktereignis.  
  
## Syntax  
  
```  
HRESULT onHandleBreakPoint(  
   IRemoteDebugApplicationThread*  prpt,  
   BREAKREASON                     br,  
   IActiveScriptErrorDebug*        pError  
);  
```  
  
#### Parameter  
 `prpt`  
 \[in\] Der Thread, wo der Haltepunkt aufgetreten ist.  
  
 `br`  
 \[in\] Der Grund für den Haltepunkt.  
  
 `pError`  
 \[in\] Ablauffehlerinformationen, vorausgesetzt, wenn der Wert von `br` BREAKREASON\_ERROR ist.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode wird aufgerufen, wenn ein Haltepunkt erreicht wird und `IDebugApplication::HandleBreakPoint` aufgerufen wird.  
  
 Die Anwendung bleibt angehalten, bis der Debugger IDE `IRemoteDebugApplication::ResumeFromBreakPoint` aufruft.  
  
## Siehe auch  
 [IApplicationDebugger\-Schnittstelle](../../winscript/reference/iapplicationdebugger-interface.md)   
 [IDebugApplication::HandleBreakPoint](../../winscript/reference/idebugapplication-handlebreakpoint.md)   
 [IRemoteDebugApplication::ResumeFromBreakPoint](../../winscript/reference/iremotedebugapplication-resumefrombreakpoint.md)   
 [BREAKREASON\-Enumeration](../../winscript/reference/breakreason-enumeration.md)