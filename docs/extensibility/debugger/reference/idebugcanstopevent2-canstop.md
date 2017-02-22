---
title: "IDebugCanStopEvent2::CanStop | Microsoft Docs"
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
  - "IDebugCanStopEvent2::CanStop"
helpviewer_keywords: 
  - "IDebugCanStopEvent2::CanStop"
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCanStopEvent2::CanStop
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Benachrichtigt das Debugmodul \(DE\) ob am aktuellen Speicherort des Codes beendet oder nur die Ausführung fortsetzt.  
  
## Syntax  
  
```cpp#  
HRESULT CanStop (   
   BOOL fCanStop  
);  
```  
  
```c#  
int CanStop (   
   int fCanStop  
);  
```  
  
#### Parameter  
 `fCanStop`  
 \[in\]  Ein Wert ungleich 0 \(`TRUE`\), wenn DE am aktuellen Speicherort des Codes beendet. Andernfalls Null \(`FALSE`\).  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Der Empfänger dieses Ereignisses wird i. d. R. die [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)\-Methode auf, um die Ursache zu bestimmen, welche DE beenden möchte und ruft dann die `IDebugCanStopEvent2::CanStop`\-Methode mit der entsprechenden Antwort an.  
  
 DE Wenn ein Ereignis beendet wird, sendet es die die Ursache für das Beenden beschreibt.  Es gibt in der Regel zwei Ereignisse gesendet werden, die einen Benutzer oder eine Signal\-Unterbrechung, die von der [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)\-Schnittstelle dargestellt werden, und ein Haltepunkt für Auswahlereignisse, das von der [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)\-Schnittstelle dargestellt wird.  
  
## Siehe auch  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)