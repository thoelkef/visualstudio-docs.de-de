---
title: "IApplicationDebugger::QueryAlive | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IApplicationDebugger.QueryAlive
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IApplicationDebugger::QueryAlive"
ms.assetid: 41181ebb-a3bf-4e41-82af-d6c7348dc706
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IApplicationDebugger::QueryAlive
Gibt an, ob der Debugger reagiert ist.  
  
## Syntax  
  
```  
HRESULT QueryAlive();  
```  
  
#### Parameter  
 Diese Methode verwendet keine Parameter.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode gibt an, wenn der Debugger reagiert ist.  Implementierungen dieser Methode sollten `S_OK` immer zurückgeben.  
  
 Wenn der Debuggerprozess unerwartet beendet wird, gibt COM einen Fehler aus Marshallingsproxy für Aufrufe dieser Methode zurück.  
  
## Siehe auch  
 [IApplicationDebugger\-Schnittstelle](../../winscript/reference/iapplicationdebugger-interface.md)