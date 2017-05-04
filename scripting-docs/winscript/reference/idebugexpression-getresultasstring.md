---
title: "IDebugExpression::GetResultAsString | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugExpression.GetResultAsString
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugExpression::GetResultAsString"
ms.assetid: edadd2ad-9369-4878-bf87-cea15be9f363
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpression::GetResultAsString
Gibt das Ergebnis der Ausdrucksauswertung als Zeichenfolge und der Rückgabewert des Vorgangs zurück.  
  
## Syntax  
  
```  
HRESULT GetResultAsString(  
   HRESULT*  phrResult,  
   BSTR*     pbstrResult  
);  
```  
  
#### Parameter  
 `phrResult`  
 \[out\] Der Rückgabewert des Vorgangs.  
  
 `pbstrResult`  
 \[out\] Das Ergebnis der Ausdrucksauswertung.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_PENDING`|Der Vorgang ist noch ausstehend.|  
  
## Hinweise  
 Diese Methode gibt das Ergebnis der Ausdrucksauswertung als Zeichenfolge und `HRESULT` des Vorgangs zurück.  
  
 Diese Methode gibt zurück `S_OK` und `phrResult``E_ABORT` gibt zurück, wenn `Abort` den Vorgang abbricht.  
  
## Siehe auch  
 [IDebugExpression\-Schnittstelle](../../winscript/reference/idebugexpression-interface.md)