---
title: "IDebugExpressionEvaluator::SetLocale | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpressionEvaluator::SetLocale"
helpviewer_keywords: 
  - "IDebugExpressionEvaluator::SetLocale-Methode"
ms.assetid: d3d2027d-74e2-4ae6-bcc7-59d12f873b7c
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugExpressionEvaluator::SetLocale
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode legt die Sprache fest, der verwendet wird, um druckbaren Ergebnisse zu erstellen.  
  
## Syntax  
  
```cpp#  
HRESULT SetLocale(   
   WORD wLangID  
);  
```  
  
```c#  
int SetLocale(  
   ushort wLangID  
);  
```  
  
#### Parameter  
 `wLangID`  
 \[in\]  Die Sprach\-ID.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Diese Methode wird oft aufgerufen, während der Ausdrucksauswertung \(EE\) geladen wird. Daher muss die EE in der Lage sein, Sprachen spontan zu wechseln.  Die EE verwendet dieses Gebietsschema, um Fehlermeldungen und Zeichenfolgen in der entsprechenden Sprache zurückzugeben.  
  
## Siehe auch  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)