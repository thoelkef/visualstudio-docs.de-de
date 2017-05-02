---
title: "IEnumRemoteDebugApplications::Next | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumRemoteDebugApplications.Next
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IEnumRemoteDebugApplications::Next"
ms.assetid: 33f6c620-6dd3-4057-b982-b88a7a1f02b4
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumRemoteDebugApplications::Next
Die `Next`\-Methode ruft eine angegebene Anzahl von Segmenten in der Enumerationsfolge ab.  
  
## Syntax  
  
```  
HRESULT Next(  
   ULONG                      celt,  
   IRemoteDebugApplication**  ppda,  
   ULONG*                     pceltFetched  
);  
```  
  
#### Parameter  
 `celt`  
 \[in\] Die Anzahl von Segmenten abzurufen.  
  
 `ppda`  
 \[out\] Gibt ein Array `IRemoteDebugApplication`\-Schnittstellen zurück, das die Segmente darstellt, die abgerufen werden.  
  
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
 [IEnumRemoteDebugApplications\-Schnittstelle](../../winscript/reference/ienumremotedebugapplications-interface.md)