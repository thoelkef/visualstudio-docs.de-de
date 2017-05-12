---
title: "IRemoteDebugApplication::GetRootNode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplication.GetRootNode
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplication::GetRootNode"
ms.assetid: 6c043aba-1dc5-41de-9711-96cde5e040f6
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplication::GetRootNode
Gibt den Anwendungsknoten zurück, unter dem alle Knoten, die der Anwendung zugeordnet sind, hinzugefügt werden.  
  
## Syntax  
  
```  
HRESULT GetRootNode(  
   IDebugApplicationNode**  ppdanRoot  
);  
```  
  
#### Parameter  
 `ppdanRoot`  
 \[out\] Der Debug\- Anwendungsknoten, unter dem alle Knoten, die der Anwendung zugeordnet sind, hinzugefügt werden.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode gibt den Anwendungsknoten zurück, unter dem alle Knoten, die der Anwendung zugeordnet sind, hinzugefügt werden.  
  
## Siehe auch  
 [IRemoteDebugApplication\-Schnittstelle](../../winscript/reference/iremotedebugapplication-interface.md)