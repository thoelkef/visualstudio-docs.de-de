---
title: "IRemoteDebugApplication::CauseBreak | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplication.CauseBreak
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplication::CauseBreak"
ms.assetid: 6a2c27bb-dca0-475c-9918-bdbb70a50d26
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IRemoteDebugApplication::CauseBreak
Bewirkt, dass die Anwendung im Debugger bei der nächstmöglichen Möglichkeit zu unterbrechen.  
  
## Syntax  
  
```  
HRESULT CauseBreak();  
```  
  
#### Parameter  
 Diese Methode verwendet keine Parameter.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Das Aufrufen dieser Methode verursacht keine Anwendung, sofort zu unterbrechen.  Wenn die Anwendung nicht nur Skriptcode ausführt, übergibt möglicherweise lange vor der Ausführung der Anwendung tatsächlich.  
  
## Siehe auch  
 [IRemoteDebugApplication\-Schnittstelle](../../winscript/reference/iremotedebugapplication-interface.md)