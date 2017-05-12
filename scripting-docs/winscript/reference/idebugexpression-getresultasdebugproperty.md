---
title: "IDebugExpression::GetResultAsDebugProperty | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugExpression.GetResultAsDebugProperty
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugExpression::GetResultAsDebugProperty"
ms.assetid: 9075bf2f-d5bb-464e-b6c2-3fa3215e9ae0
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpression::GetResultAsDebugProperty
Gibt das Ergebnis der Ausdrucksauswertung als Eigenschaft Debug\- und der Rückgabewert des Vorgangs zurück.  
  
## Syntax  
  
```  
HRESULT GetResultAsDebugProperty(  
   HRESULT*          phrResult,  
   IDebugProperty**  ppdp  
);  
```  
  
#### Parameter  
 `phrResult`  
 \[out\] Der Rückgabewert des Vorgangs.  
  
 `ppdp`  
 \[out\] Die Debugsitzung Eigenschaft für den Ausdruck.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_PENDING`|Der Vorgang ist noch ausstehend.|  
  
## Hinweise  
 Diese Methode gibt das Ergebnis der Ausdrucksauswertung als `IDebugProperty` und `HRESULT` des Vorgangs zurück.  
  
 Diese Methode gibt zurück `S_OK` und `phrResult``E_ABORT` gibt zurück, wenn `Abort` den Vorgang abbricht.  
  
## Siehe auch  
 [IDebugExpression\-Schnittstelle](../../winscript/reference/idebugexpression-interface.md)   
 [IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)