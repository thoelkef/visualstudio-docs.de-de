---
title: Beenden eines Programms | Microsoft-Dokumentation
ms.date: 11/04/2016
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
ms.openlocfilehash: 28be8f34602a3a175c40d630463686f0ca99c919
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53958851"
---
# <a name="terminating-a-program"></a>Beenden eines Programms
Der folgende Abschnitt beschreibt die Beendigung der ein einzelnes Programm mit einem Thread an.  
  
## <a name="termination-process"></a>-Verbindungsbeendigungs-Prozess  
  
1. Der DE sendet eine [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) mit einer gültigen [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md).  
  
2. Der DE sendet eine [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) mit einer gültigen [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md).  
  
   Die IDE wechselt in den Entwurfsmodus. Die Debug-Engine oder die Laufzeitumgebung Aufrufe [IDebugPortNotify2::RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) , das Programm über den Port zu entfernen.  
  
## <a name="see-also"></a>Siehe auch  
 [Aufrufen von debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)