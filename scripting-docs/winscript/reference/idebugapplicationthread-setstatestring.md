---
title: "IDebugApplicationThread::SetStateString | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplicationThread.SetStateString
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplicationThread::SetStateString"
ms.assetid: a59001d5-ea00-4fd0-bb20-0b592d9c795d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplicationThread::SetStateString
Legt die Beschreibung der Threadzustand fest.  
  
## Syntax  
  
```  
HRESULT SetStateString(  
   LPCOLESTR  pstrState  
);  
```  
  
#### Parameter  
 `pstrState`  
 \[in\] Die Beschreibung des Threadzustandes.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode wird die Beschreibung des Threadzustandes fest.  
  
## Siehe auch  
 [IDebugApplicationThread\-Schnittstelle](../../winscript/reference/idebugapplicationthread-interface.md)