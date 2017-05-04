---
title: "IDebugStackFrameSniffer::EnumStackFrames | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugStackFrameSniffer.EnumStackFrames
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugStackFrameSniffer::EnumStackFrames"
ms.assetid: a7629ab3-ef7d-4bbe-a137-bb2a8ad0f384
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugStackFrameSniffer::EnumStackFrames
Gibt einen Enumerator von Stapelrahmen für den aktuellen Thread zurück.  
  
## Syntax  
  
```  
HRESULT EnumStackFrames(  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### Parameter  
 `ppedsf`  
 \[out\] Enumerator von Stapelrahmen für den aktuellen Thread.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Der Stapelrahmenenumerator gibt die Rahmen zuletzt beginnend am Anfang des Stapels, beginnend mit den gedrückten Frames zurück.  
  
## Siehe auch  
 [IDebugStackFrameSniffer\-Schnittstelle](../../winscript/reference/idebugstackframesniffer-interface.md)