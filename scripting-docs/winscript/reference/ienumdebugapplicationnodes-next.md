---
title: "IEnumDebugApplicationNodes::Next | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugApplicationNodes.Next
apilocation: pdm.dll
helpviewer_keywords: 
  - "IEnumDebugApplicationNodes::Next"
ms.assetid: 925511c8-4f11-423d-ba2d-01589457050c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugApplicationNodes::Next
Ruft eine angegebene Anzahl von Segmenten in der Enumerationssequenz ab.  
  
## Syntax  
  
```  
HRESULT Next(  
   ULONG                    celt,  
   IDebugApplicationNode**  pprddp,  
   ULONG*                   pceltFetched  
);  
```  
  
#### Parameter  
 `celt`  
 \[in\] Die Anzahl von Segmenten abzurufen.  
  
 `pprddp`  
 \[out\] Gibt ein Array `IDebugApplicationNode`\-Schnittstellen zurück, das die Segmente darstellt, die abgerufen werden.  
  
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
 [IEnumDebugApplicationNodes\-Schnittstelle](../../winscript/reference/ienumdebugapplicationnodes-interface.md)