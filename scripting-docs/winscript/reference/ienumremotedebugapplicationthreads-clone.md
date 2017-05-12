---
title: "IEnumRemoteDebugApplicationThreads::Clone | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumRemoteDebugApplicationThreads.Clone
apilocation: pdm.dll
helpviewer_keywords: 
  - "IEnumRemoteDebugApplicationThreads::Clone"
ms.assetid: d016e7cf-ae73-48ff-aee7-810222e0b05c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumRemoteDebugApplicationThreads::Clone
Erstellt einen Enumerator, der den gleichen Zustand wie der aktuelle Enumerator enthält.  
  
## Syntax  
  
```  
HRESULT Clone(  
   IEnumRemoteDebugApplicationThreads**  pperdat  
);  
```  
  
#### Parameter  
 `pperdat`  
 \[out\] Gibt die `IEnumRemoteDebugApplicationThreads`\-Schnittstelle des Klons des Enumerators zurück.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode erstellt einen Enumerator, der denselben Zustand wie der aktuelle Enumerator enthält.  
  
## Siehe auch  
 [IEnumRemoteDebugApplicationThreads\-Schnittstelle](../../winscript/reference/ienumremotedebugapplicationthreads-interface.md)