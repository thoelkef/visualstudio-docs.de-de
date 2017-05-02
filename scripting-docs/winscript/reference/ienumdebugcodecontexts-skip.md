---
title: "IEnumDebugCodeContexts::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugCodeContexts.Skip
apilocation: jscript.dll
helpviewer_keywords: 
  - "IEnumDebugCodeContexts::Skip"
ms.assetid: ba917f57-f7a9-419f-96d6-8f4378b12c57
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugCodeContexts::Skip
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
 [IEnumDebugCodeContexts\-Schnittstelle](../../winscript/reference/ienumdebugcodecontexts-interface.md)