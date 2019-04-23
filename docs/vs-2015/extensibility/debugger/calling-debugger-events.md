---
title: Aufrufen von Debuggerereignissen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2f162affe2324afaa8fb1d506c3177311386bfc1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60110348"
---
# <a name="calling-debugger-events"></a>Aufrufen von Debuggerereignissen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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
 [Erstellen einer benutzerdefinierten Debug-Engine](../../extensibility/debugger/creating-a-custom-debug-engine.md)
