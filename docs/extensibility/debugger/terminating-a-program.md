---
title: "Beenden eines Programms | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Programme, die Beendigungsereignisse"
  - "Debuggen [Debugging-SDK], beenden ein Programm"
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# Beenden eines Programms
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Im Folgenden finden Sie eine Beschreibung der Beendigung eines einzelnen Programms mit einem Thread.  
  
## Kündigungs\-Prozess  
  
1.  DE [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)mit gültigen [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) sendet.  
  
2.  DE [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)mit gültigen [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) sendet.  
  
 Die IDE wechselt im Entwurfsmodus.  Die Laufzeit ruft Momentaufnahme für die Debug\- Modul\- oder [IDebugPortNotify2::RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) , um das Programm den Port zu entfernen.  
  
## Siehe auch  
 [Aufrufen von Debugger\-Ereignissen](../../extensibility/debugger/calling-debugger-events.md)