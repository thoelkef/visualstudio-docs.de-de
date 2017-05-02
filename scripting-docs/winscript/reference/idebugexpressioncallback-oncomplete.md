---
title: "IDebugExpressionCallBack::onComplete | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugExpressionCallBack.onComplete
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugExpressionCallBack::onComplete"
ms.assetid: d0b89db3-38e7-44e0-93fe-60205f9149dd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpressionCallBack::onComplete
Gibt an, dass die Ausdrucksauswertung abgeschlossen ist.  
  
## Syntax  
  
```  
HRESULT onComplete();  
```  
  
#### Parameter  
 Diese Methode verwendet keine Parameter.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode wird aufgerufen, wenn die Ausdrucksauswertung abgeschlossen ist.  Die `IDebugExpression::GetResultAsString`\-Methode kann aus diesem Ereignishandler aufgerufen werden.  
  
## Siehe auch  
 [IDebugExpressionCallBack\-Schnittstelle](../../winscript/reference/idebugexpressioncallback-interface.md)   
 [IDebugExpression::GetResultAsString](../../winscript/reference/idebugexpression-getresultasstring.md)