---
title: Beenden eines Programms | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debugging [Debugging SDK], terminating a program
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bc5d711783b3238c9cfe42ba3fc4edd776bcb060
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="terminating-a-program"></a>Beenden eines Programms
Im folgenden ist eine Beschreibung des Beendens der ein einzelnes Programm mit einem Thread.  
  
## <a name="termination-process"></a>Beendigungsprozess  
  
1.  Sendet die DE ein [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) durch einen gültigen [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md).  
  
2.  Sendet die DE ein [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) durch einen gültigen [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md).  
  
 Die IDE wechselt in den Entwurfsmodus zu wechseln. Die Debugging-Modul oder eine Umgebung zur Laufzeit ruft [IDebugPortNotify2::RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) Sie das Programm den Port aufheben.  
  
## <a name="see-also"></a>Siehe auch  
 [Aufrufen von Debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)