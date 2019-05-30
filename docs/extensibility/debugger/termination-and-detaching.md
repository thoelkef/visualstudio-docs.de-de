---
title: Beenden und trennen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8aafb94e0a07462d93cc77a34f7199f61f944d0f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333728"
---
# <a name="termination-and-detaching"></a>Beenden und trennen
Der folgende Abschnitt beschreibt die normalen Beendigung.

## <a name="discussion"></a>Diskussion
 Nach der [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) oder [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) Schnittstelle wird fortgesetzt, wenn es sind keine Haltepunkte, Ausnahmen, Laufzeitfehlern führen oder Endlosschleifen in der Anwendung, die debuggt werden, das derzeit debuggte Programm wird bis zum Abschluss ausgeführt. Dieser Prozess wird die normale Beendigung.

 Senden Sie eine [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) normalen Beendigung zu implementieren. Normaler Beendigung muss mit den [IDebugProgramDestroyEvent2::GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) Methode.

## <a name="see-also"></a>Siehe auch
- [Erstellen einer benutzerdefinierten Debug-engine](../../extensibility/debugger/creating-a-custom-debug-engine.md)