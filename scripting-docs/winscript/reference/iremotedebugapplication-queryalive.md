---
title: "IRemoteDebugApplication::QueryAlive | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplication.QueryAlive
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplication::QueryAlive"
ms.assetid: 08e49d3b-6fb3-4438-960e-f05395ba9b17
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplication::QueryAlive
Gibt an, ob die Anwendung reagiert weiterhin ist.  
  
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
 Diese Methode gibt an, wenn die Anwendung reagiert weiterhin ist.  Implementierungen dieser Methode sollten `S_OK` immer zurückgeben.  
  
 Wenn der Anwendungsprozess unerwartet beendet wird, gibt COM einen Fehler aus Marshallingsproxy für Aufrufe dieser Methode zurück.  
  
## Siehe auch  
 [IRemoteDebugApplication\-Schnittstelle](../../winscript/reference/iremotedebugapplication-interface.md)