---
title: "IEnumDebugExpressionContexts::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugExpressionContexts.Skip
apilocation: jscript.dll
helpviewer_keywords: 
  - "IEnumDebugExpressionContexts::Skip"
ms.assetid: 3498cbb5-8581-4dcd-b016-e86b049c7831
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugExpressionContexts::Skip
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
 [IEnumDebugExpressionContexts\-Schnittstelle](../../winscript/reference/ienumdebugexpressioncontexts-interface.md)