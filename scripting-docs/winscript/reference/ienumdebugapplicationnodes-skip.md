---
title: "IEnumDebugApplicationNodes::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugApplicationNodes.Skip
apilocation: pdm.dll
helpviewer_keywords: 
  - "IEnumDebugApplicationNodes::Skip"
ms.assetid: b2ad1957-95b5-4c09-9a44-5a765a5308ae
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugApplicationNodes::Skip
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
 [IEnumDebugApplicationNodes\-Schnittstelle](../../winscript/reference/ienumdebugapplicationnodes-interface.md)