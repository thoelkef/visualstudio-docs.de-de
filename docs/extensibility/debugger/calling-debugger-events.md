---
title: Aufrufen von Debuggerereignissen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7564010055218065a8971f40989af2152acd5d95
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66332482"
---
# <a name="call-debugger-events"></a>Aufrufen von debuggerereignissen
Ereignisse in Debugsitzungen treten in einer bestimmten Reihenfolge.

## <a name="discussion"></a>Diskussion
 Um das Muster der Aufrufe zwischen der Debug-Engine (DE) und sitzungsbasierter Debug-Manager (SDM) zu verstehen, die Folgendes die Aufrufreihenfolge der Ereignisse, die in eine typische Debuggingsitzung auftreten:

1. [Anfügen und Trennen von einem Programm](../../extensibility/debugger/attaching-and-detaching-to-a-program.md)

2. [Starten des Debuggers](../../extensibility/debugger/launching-the-debugger.md)

3. [Beenden eines Programms](../../extensibility/debugger/terminating-a-program.md)

4. [Erstellen eines Haltepunkts](../../extensibility/debugger/creating-a-breakpoint.md)

5. [Wenn ein Haltepunkt gebunden oder ungebunden immer](../../extensibility/debugger/when-a-breakpoint-binds-or-becomes-unbound.md)

6. [Haltepunktfehler](../../extensibility/debugger/breakpoint-errors.md)

7. [Erreichen eines Haltepunkts](../../extensibility/debugger/hitting-a-breakpoint.md)

8. [Löschen eines Haltepunkts](../../extensibility/debugger/deleting-a-breakpoint.md)

9. [In den Unterbrechungsmodus](../../extensibility/debugger/entering-break-mode.md)

10. [Schrittausführung im Unterbrechungsmodus](../../extensibility/debugger/stepping-in-break-mode.md)

11. [Ausdrucksauswertung im Unterbrechungsmodus](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

12. [Ausnahmebehandlung](../../extensibility/debugger/exception-handling-visual-studio-sdk.md)

## <a name="see-also"></a>Siehe auch
- [Erstellen einer benutzerdefinierten Debug-engine](../../extensibility/debugger/creating-a-custom-debug-engine.md)