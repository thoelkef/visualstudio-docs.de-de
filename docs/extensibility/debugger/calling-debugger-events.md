---
title: Aufrufen von Debugger-Ereignissen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3deef418620ab17297b4ef7e824a0d95c25e439e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85904320"
---
# <a name="call-debugger-events"></a>Debugger-Ereignisse aufzurufen
Ereignisse in Debugsitzungen treten in einer bestimmten Reihenfolge auf.

## <a name="discussion"></a>Diskussion (Discussion)
 Um das Muster von Aufrufen zwischen Debug Engine (de) und Session Debug Manager (SDM) zu verstehen, stellt Folgendes die Aufruf Reihenfolge der Ereignisse dar, die in einer typischen Debugsitzung auftreten:

1. [Anfügen und trennen an ein Programm](../../extensibility/debugger/attaching-and-detaching-to-a-program.md)

2. [Starten des Debuggers](../../extensibility/debugger/launching-the-debugger.md)

3. [Beenden eines Programms](../../extensibility/debugger/terminating-a-program.md)

4. [Erstellen eines Breakpoints](../../extensibility/debugger/creating-a-breakpoint.md)

5. [Wenn ein Breakpoint gebunden wird oder die Bindung aufgehoben wird](../../extensibility/debugger/when-a-breakpoint-binds-or-becomes-unbound.md)

6. [Haltepunkt Fehler](../../extensibility/debugger/breakpoint-errors.md)

7. [Treffen eines Haltepunkts](../../extensibility/debugger/hitting-a-breakpoint.md)

8. [Löschen eines Breakpoints](../../extensibility/debugger/deleting-a-breakpoint.md)

9. [Wechseln in den Umbruch Modus](../../extensibility/debugger/entering-break-mode.md)

10. [Schrittweise im Break-Modus](../../extensibility/debugger/stepping-in-break-mode.md)

11. [Ausdrucks Auswertung im Break-Modus](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

12. [Ausnahmebehandlung](../../extensibility/debugger/exception-handling-visual-studio-sdk.md)

## <a name="see-also"></a>Weitere Informationen
- [Erstellen einer benutzerdefinierten Debug-Engine](../../extensibility/debugger/creating-a-custom-debug-engine.md)
