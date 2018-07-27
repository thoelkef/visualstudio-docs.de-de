---
title: Beenden eines Programms | Microsoft-Dokumentation
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
ms.openlocfilehash: e1914d00af1eeda94ef1cf9129e637ce39306257
ms.sourcegitcommit: 8d38d5d2f2b75fc1563952c0d6de0fe43af12766
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/26/2018
ms.locfileid: "39276961"
---
# <a name="terminating-a-program"></a>Beenden eines Programms
Der folgende Abschnitt beschreibt die Beendigung der ein einzelnes Programm mit einem Thread an.  
  
## <a name="termination-process"></a>-Verbindungsbeendigungs-Prozess  
  
1.  Der DE sendet eine [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) mit einer gültigen [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md).  
  
2.  Der DE sendet eine [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) mit einer gültigen [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md).  
  
 Die IDE wechselt in den Entwurfsmodus. Die Debug-Engine oder die Laufzeitumgebung Aufrufe [IDebugPortNotify2::RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) , das Programm über den Port zu entfernen.  
  
## <a name="see-also"></a>Siehe auch  
 [Aufrufen von debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)