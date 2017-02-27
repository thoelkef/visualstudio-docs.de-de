---
title: "IDebugExpression2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpression2"
helpviewer_keywords: 
  - "IDebugExpression2-Schnittstelle"
ms.assetid: f5e4b124-1e30-47c8-a511-80084a02dba5
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugExpression2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle stellt einen analysierten Ausdruck dar, der zum Binden und zum Auswerten bereit ist.  
  
## Syntax  
  
```  
IDebugExpression2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Das Debugmodul \(DE\) implementiert diese Schnittstelle, um einen analysierten Ausdruck dargestellt werden, der ausgewertet werden kann.  
  
## Hinweise für Aufrufer  
 Ein Aufruf von [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) gibt diese Schnittstelle zurück.  [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) gibt die [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)\-Schnittstelle zurück.  Diese Schnittstellen sind nur verfügbar, wenn das Programm, das gedebuggt wird, angehalten wurde und ein Stapelrahmen verfügbar ist.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDebugExpression2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Wertet den Ausdruck asynchron aus.|  
|[Abbrechen](../../../extensibility/debugger/reference/idebugexpression2-abort.md)|Beendet die asynchrone Ausdrucksauswertung.|  
|[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Wertet den Ausdruck synchron aus.|  
  
## Hinweise  
 Wenn ein Programm angehalten wurde, erhält der Debug\- Manager der Sitzung \(SDM\) ein Stapelrahmen von DE mit einem Aufruf von [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md).  Das SDM ruft dann [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) auf, um die [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)\-Schnittstelle abzurufen.  Dies wird bei einem Aufruf von [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) befolgt, um die `IDebugExpression2`\-Schnittstelle zu erstellen, die den analysierten Ausdruck darstellt, der ausgewertet werden kann.  
  
 Das SDM ruft entweder [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) oder [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) an, um den Ausdruck auszuwerten und tatsächlich einen Wert zu erzeugen.  
  
 In einer Implementierung von `IDebugExpressionContext2::ParseText`DE `CoCreateInstance`\-Funktion verwendet, COM, um einen Ausdrucksauswertung zu instanziieren und eine [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)\-Schnittstelle abzurufen \(finden Sie im Beispiel in der `IDebugExpressionEvaluator`\-Schnittstelle\).  DE [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) wird anschließend zum Abrufen einer Verbindung [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)\-Schnittstelle.  Diese Schnittstelle wird in der Implementierung von `IDebugExpression2::EvaluateSync` und `IDebugExpression2::EvaluateAsync` verwendet, um die Evaluierung auszuführen.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)