---
title: "IDebugExpression::QueryIsComplete | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugExpression.QueryIsComplete
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugExpression::QueryIsComplete"
ms.assetid: 510d62e5-a316-46fb-b23f-d3ba902b295c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpression::QueryIsComplete
Bestimmt, ob der Vorgang abgeschlossen ist.  
  
## Syntax  
  
```  
HRESULT QueryIsComplete();  
```  
  
#### Parameter  
 Diese Methode verwendet keine Parameter.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode, die folgen, und der Vorgang abgeschlossen.|  
|`S_FALSE`|Der Vorgang ist noch ausstehend.|  
  
## Hinweise  
 Diese Methode bestimmt, wenn der Vorgang abgeschlossen ist.  
  
## Siehe auch  
 [IDebugExpression\-Schnittstelle](../../winscript/reference/idebugexpression-interface.md)