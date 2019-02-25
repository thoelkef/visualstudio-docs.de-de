---
title: Beenden und trennen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a727f30f6070b44e16dbc4206ac56e0224ff3d67
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56682166"
---
# <a name="termination-and-detaching"></a>Beenden und trennen
Der folgende Abschnitt beschreibt die normalen Beendigung.

## <a name="discussion"></a>Diskussion
 Nach der [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) oder [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) Schnittstelle wird fortgesetzt, wenn es sind keine Haltepunkte, Ausnahmen, Laufzeitfehlern führen oder Endlosschleifen in der Anwendung, die debuggt werden, das derzeit debuggte Programm wird bis zum Abschluss ausgeführt. Dieser Prozess wird die normale Beendigung.

 Senden Sie eine [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) normalen Beendigung zu implementieren. Normaler Beendigung muss mit den [IDebugProgramDestroyEvent2::GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) Methode.

## <a name="see-also"></a>Siehe auch
- [Erstellen einer benutzerdefinierten Debug-engine](../../extensibility/debugger/creating-a-custom-debug-engine.md)