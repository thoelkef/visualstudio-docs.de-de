---
title: "IEnumRemoteDebugApplicationThreads::Next | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumRemoteDebugApplicationThreads.Next
apilocation: pdm.dll
helpviewer_keywords: 
  - "IEnumRemoteDebugApplicationThreads::Next"
ms.assetid: d8d10d7e-3468-49be-acf9-d842db9940e7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumRemoteDebugApplicationThreads::Next
Die `Next`\-Methode ruft eine angegebene Anzahl von Segmenten in der Enumerationsfolge ab.  
  
## Syntax  
  
```  
HRESULT Next(  
   ULONG                            celt,  
   IRemoteDebugApplicationThread**  pprdat,  
   ULONG*                           pceltFetched  
);  
```  
  
#### Parameter  
 `celt`  
 \[in\] Die Anzahl von Segmenten abzurufen.  
  
 `pprdat`  
 \[out\] Gibt ein Array `IRemoteDebugApplicationThread`\-Schnittstellen zurück, das die Segmente darstellt, die abgerufen werden.  
  
 `pceltFetched`  
 \[out\] Die tatsächliche Anzahl von Segmenten abgerufen vom Enumerator.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode ruft eine angegebene Anzahl von Segmenten in der Enumerationsfolge ab.  
  
## Siehe auch  
 [IEnumRemoteDebugApplicationThreads\-Schnittstelle](../../winscript/reference/ienumremotedebugapplicationthreads-interface.md)