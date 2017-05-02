---
title: "IEnumDebugStackFrames::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugStackFrames.Skip
apilocation: jscript.dll
helpviewer_keywords: 
  - "IEnumDebugStackFrames::Skip"
ms.assetid: d893d6e9-e119-4f14-99d0-bf23dbd2d625
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugStackFrames::Skip
Überspringt eine angegebene Anzahl von Segmenten in einer Enumerationssequenz.  
  
## Syntax  
  
```  
HRESULT Skip(  
   ULONG  celt  
);  
```  
  
#### Parameter  
 `celt`  
 \[in\] Zahl der zu überspringenden Segmente in der Enumerationsfolge.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode überspringt eine angegebene Anzahl von Segmenten in einer Enumerationsfolge.  
  
## Siehe auch  
 [IEnumDebugStackFrames\-Schnittstelle](../../winscript/reference/ienumdebugstackframes-interface.md)