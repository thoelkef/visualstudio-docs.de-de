---
title: "IEnumDebugStackFrames::Next | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugStackFrames.Next
apilocation: jscript.dll
helpviewer_keywords: 
  - "IEnumDebugStackFrames::Next"
ms.assetid: ade3f5b0-8ff3-48a0-9433-270789e6d53e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugStackFrames::Next
Ruft eine angegebene Anzahl von Segmenten in der Enumerationssequenz ab.  
  
## Syntax  
  
```  
HRESULT Next(  
   ULONG                       celt,  
   DebugStackFrameDescriptor*  prgdsfd,  
   ULONG*                      pceltFetched  
);  
```  
  
#### Parameter  
 `celt`  
 \[in\] Die Anzahl von Segmenten abzurufen.  
  
 `prgdsfd`  
 \[out\] Gibt ein Array `DebugStackFrameDescriptor`\-Schnittstellen zurück, das die Segmente darstellt, die abgerufen werden.  
  
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
 [IEnumDebugStackFrames\-Schnittstelle](../../winscript/reference/ienumdebugstackframes-interface.md)   
 [DebugStackFrameDescriptor\-Struktur](../../winscript/reference/debugstackframedescriptor-structure.md)