---
title: Beenden und trennen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e5af218098f6d79cf6208c66b314c35d2471af15
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="termination-and-detaching"></a>Beenden und trennen
Im folgenden wird die normalen Beendigung beschrieben.  
  
## <a name="discussion"></a>Diskussion  
 Nach der [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) oder [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) Schnittstelle wird fortgesetzt, wenn keine Haltepunkte, die Ausnahmen, die Laufzeitfehler oder die Endlosschleifen in der Anwendung, die debuggt werden, vorhanden sind das Programm, der debuggt wird bis zum Abschluss ausgeführt. Dies ist die normale Beendigung.  
  
 Senden Sie eine [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) normalen Beendigung zu implementieren. Implementieren Sie dazu die [IDebugProgramDestroyEvent2::GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen eines benutzerdefinierten Debugmoduls](../../extensibility/debugger/creating-a-custom-debug-engine.md)