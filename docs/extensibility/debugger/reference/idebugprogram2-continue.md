---
title: "IDebugProgram2::Continue | Microsoft Docs"
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
  - "IDebugProgram2::Continue"
helpviewer_keywords: 
  - "IDebugProgram2::Continue"
ms.assetid: e5a6e02a-d21b-4a03-a034-e8de1f71ce2e
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgram2::Continue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Setzt die Ausführung des Programms aus einem Beendet fort.  Jeder vorherige Ausführungsstatus \(z. B. einem Schritt\) wird und das Programm gestartet wird beibehalten, die erneut ausführen.  
  
> [!NOTE]
>  Diese Methode ist veraltet.  Verwenden Sie stattdessen die [Weiter](../../../extensibility/debugger/reference/idebugprocess3-continue.md)\-Methode.  
  
## Syntax  
  
```cpp#  
HRESULT Continue(   
   IDebugThread2* pThread  
);  
```  
  
```c#  
int Continue(   
   IDebugThread2 pThread  
);  
```  
  
#### Parameter  
 `pThread`  
 \[in\]  Ein [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)\-Objekt, das den Thread darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Diese Methode wird für dieses Programm aufgerufen, unabhängig davon, wie viele Anwendungen gedebuggt werden oder das Programm das aufhörende Ereignis generiert hat.  Die Implementierung muss den vorherigen Ausführungsstatus beibehalten \(z. B. einem Schritt\) und die Ausführung fortsetzen, als ob sie nie beendet wurde, bevor sie ihre vorherige Ausführung abgeschlossen haben.  Das heißt, wenn ein Thread in diesem Programm eine Schritt\-über Vorgang tat und beendet wurde, weil ein anderes Programm als auch die diese Methode anschließend aufgerufen wurden, muss das Programm die Vorlage Schritt\-über Vorgang abschließen.  
  
> [!WARNING]
>  Senden Sie ein aufhörendes Ereignis oder ein unmittelbares \(synchrone\) Ereignis nicht beim Behandeln dieses Aufrufs zu [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) . Andernfalls hängt vom Debugger kann.  
  
## Siehe auch  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)