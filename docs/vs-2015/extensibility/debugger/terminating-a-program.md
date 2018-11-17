---
title: Beenden eines Programms | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- programs, termination events
- debugging [Debugging SDK], terminating a program
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c3bc26486db7cdc5f8a29477b4380041b506c4e6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51772910"
---
# <a name="terminating-a-program"></a>Beenden eines Programms
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Folgendes ist eine Beschreibung für die Beendigung der ein einzelnes Programm mit einem Thread.  
  
## <a name="termination-process"></a>-Verbindungsbeendigungs-Prozess  
  
1. Der DE sendet eine [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) mit einer gültigen [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md).  
  
2. Der DE sendet eine [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) mit einer gültigen [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md).  
  
   Die IDE wechselt in den Entwurfsmodus. Die Debug-Engine oder die Laufzeitumgebung Aufrufe [IDebugPortNotify2::RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) , das Programm über den Port zu entfernen.  
  
## <a name="see-also"></a>Siehe auch  
 [Aufrufen von Debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)

