---
title: "IDebugProcess3::Execute | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess3::Execute"
helpviewer_keywords: 
  - "IDebugProcess3::Execute"
ms.assetid: d831cd81-d7bf-4172-8517-aa699867791f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProcess3::Execute
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Setzt die Ausführung dieses Vorgangs aus einem Beendet fort.  Jeder vorherige Ausführungsstatus \(z. B. einem Schritt\) wird und der Prozess gestartet wird gelöscht, die erneut ausführen.  
  
> [!NOTE]
>  Diese Methode sollte statt [Ausführen](../../../extensibility/debugger/reference/idebugprogram2-execute.md)verwendet werden.  
  
## Syntax  
  
```cpp  
HRESULT Execute(  
   IDebugThread2* pThread  
);  
```  
  
```c#  
int Execute(  
   IDebugThread2 pThread  
);  
```  
  
#### Parameter  
 `pThread`  
 \[in\]  Ein [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)\-Objekt, das den Thread darstellt, der ausgeführt werden soll.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. Gibt andernfalls Fehlercode zurück.  
  
## Hinweise  
 Wenn der Benutzer die Ausführung eines anderen Prozesses beliebigen Thread im Beendet beginnt, wird diese Methode für diesen Prozess aufgerufen.  Diese Methode wird auch aufgerufen, wenn der Benutzer den Startbefehl vom **Debuggen** Menü in der IDE aktiviert.  Die Implementierung dieser Methode kann so einfach wie das die [Fortsetzen](../../../extensibility/debugger/reference/idebugthread2-resume.md)\-Methode für den aktuellen Thread im Prozess aufgerufen wird.  
  
> [!WARNING]
>  Senden Sie ein aufhörendes Ereignis oder ein unmittelbares \(synchrone\) Ereignis nicht beim Behandeln dieses Aufrufs zu [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) . Andernfalls hängt vom Debugger kann.  
  
## Siehe auch  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Fortsetzen](../../../extensibility/debugger/reference/idebugthread2-resume.md)   
 [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)