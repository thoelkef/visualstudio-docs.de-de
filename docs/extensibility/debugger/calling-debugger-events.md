---
title: Aufrufen von Debuggerereignissen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 869bd87952aebf8ad640c5aeb439c9e99929f4c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739166"
---
# <a name="call-debugger-events"></a>Aufrufen von Debuggerereignissen
Ereignisse in Debugsitzungen treten in einer bestimmten Reihenfolge auf.

## <a name="discussion"></a>Diskussion
 Um das Muster der Aufrufe zwischen dem Debugmodul (DE) und dem Sitzungsdebug-Manager (SDM) zu verstehen, stellt Folgendes die Aufrufreihenfolge der Ereignisse dar, die in einer typischen Debugsitzung auftreten:

1. [Anfügen und Trennen an einem Programm](../../extensibility/debugger/attaching-and-detaching-to-a-program.md)

2. [Starten des Debuggers](../../extensibility/debugger/launching-the-debugger.md)

3. [Beenden eines Programms](../../extensibility/debugger/terminating-a-program.md)

4. [Erstellen eines Haltepunkts](../../extensibility/debugger/creating-a-breakpoint.md)

5. [Wenn ein Haltepunkt bindet oder ungebunden wird](../../extensibility/debugger/when-a-breakpoint-binds-or-becomes-unbound.md)

6. [Breakpoint-Fehler](../../extensibility/debugger/breakpoint-errors.md)

7. [Treffen eines Haltepunkts](../../extensibility/debugger/hitting-a-breakpoint.md)

8. [Löschen eines Haltepunkts](../../extensibility/debugger/deleting-a-breakpoint.md)

9. [Eingabe des Pausenmodus](../../extensibility/debugger/entering-break-mode.md)

10. [Treten im Pausenmodus](../../extensibility/debugger/stepping-in-break-mode.md)

11. [Ausdrucksauswertung im Unterbrechungsmodus](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

12. [Ausnahmebehandlung](../../extensibility/debugger/exception-handling-visual-studio-sdk.md)

## <a name="see-also"></a>Weitere Informationen
- [Erstellen eines benutzerdefinierten Debugmoduls](../../extensibility/debugger/creating-a-custom-debug-engine.md)
