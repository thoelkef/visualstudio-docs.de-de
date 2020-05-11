---
title: Kündigung und Ablösung | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b88255d618ce42fa55d878f192d31523ba3f83b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712494"
---
# <a name="termination-and-detaching"></a>Kündigung und Ablösung
Im folgenden Abschnitt wird die normale Beendigung beschrieben.

## <a name="discussion"></a>Diskussion
 Nachdem die [IDebugLoadCompleteEvent2-](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) oder [IDebugEntryPointEvent2-Schnittstelle](../../extensibility/debugger/reference/idebugentrypointevent2.md) fortgesetzt wurde, wird das zu debuggende Programm bis zum Abschluss ausgeführt, wenn keine Haltepunkte, Ausnahmen, Laufzeitfehler oder Endlosschleifen in der zu debuggenden Anwendung vorhanden sind. Dieser Prozess ist eine normale Beendigung.

 Sie müssen ein [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) senden, um die normale Beendigung zu implementieren. Die normale Beendigung erfordert die Ausführung der [IDebugProgramDestroyEvent2::GetExitCode-Methode.](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md)

## <a name="see-also"></a>Weitere Informationen
- [Erstellen eines benutzerdefinierten Debugmoduls](../../extensibility/debugger/creating-a-custom-debug-engine.md)
