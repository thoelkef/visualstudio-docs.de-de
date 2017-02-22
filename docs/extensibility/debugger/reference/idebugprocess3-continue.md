---
title: "IDebugProcess3::Continue | Microsoft Docs"
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
  - "IDebugProcess3::Continue"
helpviewer_keywords: 
  - "IDebugProcess3::Continue"
ms.assetid: 57506242-5763-4c08-adb9-8a78ce02cebb
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcess3::Continue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Setzt die Ausführung dieses Vorgangs aus einem Beendet fort.  Jeder vorherige Ausführungsstatus \(z. B. einem Schritt\) wird und die gestartet wird beibehalten, die erneut ausführen.  
  
> [!NOTE]
>  Diese Methode sollte statt [Weiter](../../../extensibility/debugger/reference/idebugprogram2-continue.md)verwendet werden.  
  
## Syntax  
  
```cpp  
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
 \[in\]  Ein Objekt, das den [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) Fortsetzung werden Thread darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. Gibt andernfalls Fehlercode zurück.  
  
## Hinweise  
 Diese Methode wird für diesen Prozess aufgerufen, unabhängig davon, wie viele Prozesse gedebuggt oder welcher Prozess die aufhörende Ereignis generiert hat.  Die Implementierung muss den vorherigen Ausführungsstatus beibehalten \(z. B. einem Schritt\) und die Ausführung fortsetzen, als ob sie nie beendet wurde, bevor sie ihre vorherige Ausführung abgeschlossen haben.  Das heißt, wenn ein Thread in diesem Prozess A Schritt\-über und tat Vorgang beendet wurde, da jeder andere beendeter Prozess und dann `Continue` aufgerufen wurden, muss der angegebene Thread die Vorlage Schritt\-über Vorgang abschließen.  
  
 **Warnung** senden aufhörendes ein Ereignis oder ein unmittelbares \(synchrone\) Ereignis nicht beim Behandeln dieses Aufrufs zu [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) . Andernfalls hängt vom Debugger kann.  
  
## Siehe auch  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)