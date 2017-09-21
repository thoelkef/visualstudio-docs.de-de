---
title: "IDebugProgram2::Terminate | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::Terminate"
helpviewer_keywords: 
  - "IDebugProgram2::Terminate"
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProgram2::Terminate
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Beendet das Programm.  
  
## Syntax  
  
```cpp#  
HRESULT Terminate(   
   void   
);  
```  
  
```c#  
int Terminate();  
```  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Wenn möglich, wird das Programm beendet und aus dem Prozess entladen. Andernfalls führt das Debugmodul \(DE\) jedes notwendige Bereinigung aus.  
  
 Diese Methode oder die [Beenden](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)\-Methode wird von der IDE, i. d. R. als Reaktion auf den Benutzer aufgerufen, der alle Debuggen enthält.  Die Implementierung dieser Methode muss das Programm ideal innerhalb des Prozesses beenden.  Wenn dies nicht möglich ist, sollte am Ausführen des Programms DE mehr in diesem Prozess verhindern \(und entweder die notwendigen Bereinigungsvorgänge\).  Wenn die `IDebugProcess2::Terminate`\-Methode von der IDE aufgerufen wurde, wird der gesamten Prozess einmal beendet, nachdem die `IDebugProgram2::Terminate`\-Methode aufgerufen wurde.  
  
## Siehe auch  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [Beenden](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)