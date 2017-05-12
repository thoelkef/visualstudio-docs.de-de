---
title: "IRemoteDebugApplicationEvents::OnBreakFlagChange | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationEvents.OnBreakFlagChange
apilocation: jscript.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationEvents::OnBreakFlagChange"
ms.assetid: 25684454-a0d8-47e0-85f5-2217069a9f45
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplicationEvents::OnBreakFlagChange
Behandelt ein Ereignis, wenn die Unterbrechungsflags ändern.  
  
## Syntax  
  
```  
HRESULT OnBreakFlagChange(  
   APPBREAKFLAGS                   abf,  
   IRemoteDebugApplicationThread*  prdatSteppingThread  
);  
```  
  
#### Parameter  
 `abf`  
 \[in\] Die aktuellen Unterbrechungsflags für die Anwendung.  
  
 `prdatSteppingThread`  
 \[in\] Der momentan ausgeführten Thread.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode behandelt das Ereignis wenn die Unterbrechungsflagsänderung.  
  
## Siehe auch  
 [IRemoteDebugApplicationEvents\-Schnittstelle](../../winscript/reference/iremotedebugapplicationevents-interface.md)   
 [APPBREAKFLAGS\-Enumeration](../../winscript/reference/appbreakflags-enumeration.md)