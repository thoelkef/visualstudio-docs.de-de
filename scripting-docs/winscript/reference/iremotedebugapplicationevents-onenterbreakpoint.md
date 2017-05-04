---
title: "IRemoteDebugApplicationEvents::OnEnterBreakPoint | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationEvents.OnEnterBreakPoint
apilocation: jscript.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationEvents::OnEnterBreakPoint"
ms.assetid: e92a56a3-c462-4a76-8ae8-4b2e6836a711
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplicationEvents::OnEnterBreakPoint
Behandelt ein Ereignis zum Eingeben eines Haltepunkts.  
  
## Syntax  
  
```  
HRESULT OnEnterBreakPoint(  
   IRemoteDebugApplicationThread*  prdat  
);  
```  
  
#### Parameter  
 `prdat`  
 \[in\] Der Anwendungsthread, der den Haltepunkt eingegeben hat.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode behandelt ein Ereignis zum Eingeben eines Haltepunkts.  
  
## Siehe auch  
 [IRemoteDebugApplicationEvents\-Schnittstelle](../../winscript/reference/iremotedebugapplicationevents-interface.md)