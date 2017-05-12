---
title: "IDebugExpression::Start | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugExpression.Start
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugExpression::Start"
ms.assetid: a7af3470-62b5-40f0-987d-63b6b22538b3
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpression::Start
Startet die Auswertung des Ausdrucks.  
  
## Syntax  
  
```  
HRESULT Start(  
   IDebugExpressionCallBack*  pdecb  
);  
```  
  
#### Parameter  
 `pdecb`  
 \[in\] Rückruf für die Angabe, wann die Ausdrucksauswertung abgeschlossen ist.  Wenn dieser Parameter `NULL` ist, werden keine Ereignisse ausgelöst und der Client muss den Ausdruckszustand optimieren, indem er `QueryIsComplete` verwendet.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode startet die Auswertung des Ausdrucks.  
  
## Siehe auch  
 [IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)   
 [IDebugExpression\-Schnittstelle](../../winscript/reference/idebugexpression-interface.md)