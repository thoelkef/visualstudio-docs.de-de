---
title: "IDebugExceptionEvent2::PassToDebuggee | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExceptionEvent2::PassToDebuggee"
helpviewer_keywords: 
  - "IDebugExceptionEvent2::PassToDebuggee"
ms.assetid: a20d0f0b-2ca0-4437-bd22-9213c81d2738
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugExceptionEvent2::PassToDebuggee
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt an, ob die Ausnahme an das Programm übergeben werden soll, das gedebuggt wird, wenn die Ausführung fortsetzt bzw. wenn die Ausnahme verworfen wird.  
  
## Syntax  
  
```cpp#  
HRESULT PassToDebuggee(  
   BOOL fPass  
);  
```  
  
```c#  
int PassToDebuggee(  
   int fPass  
);  
```  
  
#### Parameter  
 `fPass`  
 \[in\]  Ein Wert ungleich 0 \(`TRUE`\), wenn die Ausnahme an das Programm übergeben wird, das gedebuggt wird, wenn die Ausführung fortsetzt, oder`FALSE`\(null\), wenn die Ausnahme verworfen wird.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Das Aufrufen dieser Methode bewirkt keinen Code tatsächlich im Programm ausgeführt wird, der gedebuggt wird.  Der Aufruf ist lediglich den Zustand für die nächste Codeausführung festzulegen.  Beispielsweise geben möglicherweise Aufrufe der [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)\-Methode `S_OK` mit [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md)zurück.`dwState` Feld festgelegt `EXCEPTION_STOP_SECOND_CHANCE`.  
  
 Die IDE das [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)\-Ereignis empfangen und ruft die [Weiter](../../../extensibility/debugger/reference/idebugprogram2-continue.md)\-Methode auf.  Das Debugmodul \(DE\) sollte ein Standardverhalten verfügen, wenn die Groß\- und Kleinschreibung zu behandeln, wenn die `PassToDebuggee`\-Methode nicht aufgerufen wird.  
  
## Siehe auch  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)   
 [Weiter](../../../extensibility/debugger/reference/idebugprogram2-continue.md)