---
title: "IDebugEngineProgram2::WatchForThreadStep | Microsoft Docs"
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
  - "IDebugEngineProgram2::WatchForThreadStep"
helpviewer_keywords: 
  - "IDebugEngineProgram2::WatchForThreadStep"
ms.assetid: b70922a3-1313-409a-b3b7-50c7cd13e394
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEngineProgram2::WatchForThreadStep
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Beobachtet \(oder bei der Ausführung abgebrochen, zur Ausführung\) zu überwachen, die auf dem angegebenen Thread zu fungieren.  
  
## Syntax  
  
```cpp#  
HRESULT WatchForThreadStep(   
   IDebugProgram2* pOriginatingProgram,  
   DWORD           dwTid,  
   BOOL            fWatch,  
   DWORD           dwFrame  
);  
```  
  
```c#  
int WatchForThreadStep(   
   IDebugProgram2 pOriginatingProgram,  
   uint           dwTid,  
   int            fWatch,  
   uint           dwFrame  
);  
```  
  
#### Parameter  
 `pOriginatingProgram`  
 \[in\]  Ein [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)\-Objekt, das das Programm hergestellt wird, darstellt.  
  
 `dwTid`  
 \[in\]  Gibt den Bezeichner des Threads auf, um zu überwachen.  
  
 `fWatch`  
 \[in\]  Ungleich 0 \(`TRUE`\) bedeutet, der den Einstieg zur Ausführung auf dem Thread überwacht, der von `dwTid`identifiziert wird. Andernfalls`FALSE`\(null\) bedeutet, der zum Beenden der Ausführung auf `dwTid`überwacht.  
  
 `dwFrame`  
 \[in\]  Gibt einen Frame Index an, der den Typ des Schritts steuert.  Wenn dieser Wert ist null \(0\), wird der Schritt im Schritt ist „Typ“ ist und das Programm beendet werden soll, sobald der Thread, der durch `dwTid` identifiziert wird, ausgeführt wird.  Gleich wenn `dwFrame` ungleich 0 \(null\) ist, wird der Schritt überspringen „Typ“ und das Programm beendet werden soll, wenn der Thread, der identifiziert wird, in `dwTid` Ausführung Rahmen, deren Index ist oder auf dem Stapel als `dwFrame`höher.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Wenn die Programmdebuginformationen Schritte des Managers der Sitzung \(SDM\) eines Programms, identifiziert durch den `pOriginatingProgram`\-Parameter, es alle anderen angefügten Programme benachrichtigt, indem Sie diese Methode aufrufen.  
  
 Diese Methode ist nur anwendbar schrittweisen Thread Gleich soll.  
  
## Siehe auch  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)