---
title: "IRemoteDebugApplication::EnumThreads | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplication.EnumThreads
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplication::EnumThreads"
ms.assetid: b4d7294c-1f15-4f7e-bdfd-700e3bf98cea
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplication::EnumThreads
Listet alle Threads, die bekannt sind, mit der Anwendung zugeordnet werden.  
  
## Syntax  
  
```  
HRESULT EnumThreads(  
   IEnumRemoteDebugApplicationThreads**  pperdat  
);  
```  
  
#### Parameter  
 `pperdat`  
 \[out\] Enumerator, der alle Threads aufgeführt werden, die bekannt sind, mit der Anwendung zugeordnet werden.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode listet alle Threads, die bekannt sind, mit der Anwendung zugeordnet werden.  Neue Threads werden jederzeit hinzugefügt werden.  
  
## Siehe auch  
 [IRemoteDebugApplication\-Schnittstelle](../../winscript/reference/iremotedebugapplication-interface.md)