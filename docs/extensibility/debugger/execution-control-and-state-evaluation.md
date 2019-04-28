---
title: Ausführungssteuerung und Zustandsauswertung | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], execution control
- expression evaluation, control of execution
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bd04cfa1e271f94f1b37aa0fbd62e9b846d9a70d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62925711"
---
# <a name="execution-control-and-state-evaluation"></a>Ausführung und Auswertung
Debuggen einer Anwendung erfordert die Implementierung von Ausführung Steuerelement Features wie Funktionen schrittweise an Haltepunkten anhalten und Fortsetzen der Ausführung. Visual Studio-debugging Basen werden die Steuerung der Ausführung auf Ereignissen zwischen Debuggerkomponenten gesendet.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Die Programmsteuerung](../../extensibility/debugger/program-control.md) enthält die folgenden Routinen, die auf Programmebene auftreten: Festlegen der nächsten Anweisung, Ausführung, schrittweise ausführen, Sie den Vorgang fortsetzen, Anhalten und fortsetzen.

 [Auf Haltepunkte bezogene Methoden](../../extensibility/debugger/breakpoint-related-methods.md) definiert die Grenze und die ausstehenden Typen von Haltepunkten, die Visual Studio unterstützt.

 [Auswertung der Aufrufliste](../../extensibility/debugger/call-stack-evaluation.md) Implementierung der Methoden, mit denen der Stapelrahmen der Aufrufliste anzeigen, während des Unterbrechungsmodus können erläutert.

 [Auswertung des Ausdrucks](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md) wird erläutert, wie die Debug-Engine (DE), Auswertung von Ausdrücken (EE) und sitzungsbasierter Debug-Manager an die Analyse und Auswertung eines Ausdrucks in eines der Fenster der IDE eingegeben beteiligt sind.

 [Steuern von Ereignissen](../../extensibility/debugger/control-events.md) wird erläutert, die verwendete Schnittstelle zum Senden von Ereignissen während der kontrollierten Ausführung des Programms.