---
title: "IEnumDebugCodeContexts::Next | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugCodeContexts.Next
apilocation: jscript.dll
helpviewer_keywords: 
  - "IEnumDebugCodeContexts::Next"
ms.assetid: 844cc353-ae0b-45e1-84a6-32b0bb67f57f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugCodeContexts::Next
Ruft eine angegebene Anzahl von Segmenten in der Enumerationssequenz ab.  
  
## Syntax  
  
```  
HRESULT Next(  
   ULONG                celt,  
   IDebugCodeContext**  pscc,  
   ULONG*               pceltFetched  
);  
```  
  
#### Parameter  
 `celt`  
 \[in\] Die Anzahl von Segmenten abzurufen.  
  
 `pscc`  
 \[out\] Gibt ein Array `IDebugCodeContext`\-Schnittstellen zurück, das die Segmente darstellt, die abgerufen werden.  
  
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
 [IEnumDebugCodeContexts\-Schnittstelle](../../winscript/reference/ienumdebugcodecontexts-interface.md)