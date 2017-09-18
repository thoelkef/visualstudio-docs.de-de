---
title: "IDebugProgram2::Execute | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::Execute"
helpviewer_keywords: 
  - "IDebugProgram2::Execute"
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugProgram2::Execute
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Setzt die Ausführung des Programms aus einem Beendet fort.  Jeder vorherige Ausführungsstatus \(z. B. einem Schritt\) wird und das Programm gestartet wird gelöscht, die erneut ausführen.  
  
> [!NOTE]
>  Diese Methode ist veraltet.  Verwenden Sie stattdessen die [Ausführen](../../../extensibility/debugger/reference/idebugprocess3-execute.md)\-Methode.  
  
## Syntax  
  
```cpp#  
HRESULT Execute(  
   void  
);  
```  
  
```c#  
int Execute();  
```  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Wenn der Benutzer die Ausführung eines Programms eines anderen Thread im Beendet beginnt, wird diese Methode für das Programm aufgerufen.  Diese Methode wird auch aufgerufen, wenn der Benutzer den Startbefehl vom **Debuggen** Menü in der IDE aktiviert.  Die Implementierung dieser Methode kann so einfach wie das die [Fortsetzen](../../../extensibility/debugger/reference/idebugthread2-resume.md)\-Methode für den aktuellen Thread im Programm aufgerufen wird.  
  
> [!WARNING]
>  Senden Sie ein aufhörendes Ereignis oder ein unmittelbares \(synchrone\) Ereignis nicht beim Behandeln dieses Aufrufs zu [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) . Andernfalls hängt vom Debugger kann.  
  
## Siehe auch  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Fortsetzen](../../../extensibility/debugger/reference/idebugthread2-resume.md)