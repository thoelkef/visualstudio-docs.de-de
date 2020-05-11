---
title: Ausführungskontrolle und Zustandsbewertung | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], execution control
- expression evaluation, control of execution
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc76ae97e8baa6ce78dd4d565109d6a19e2051e2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738754"
---
# <a name="execution-control-and-state-evaluation"></a>Ausführungskontrolle und Zustandsbewertung
Das Debuggen einer Anwendung erfordert das Implementieren solcher Ausführungssteuerungsfunktionen als Eintreten in Funktionen, Anhalten an Haltepunkten und Fortsetzen der Ausführung. Das Visual Studio-Debuggen basiert seine Ausführungssteuerung auf Ereignissen, die zwischen Debuggerkomponenten gesendet werden.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Programmsteuerung](../../extensibility/debugger/program-control.md) Listet die folgenden Routinen auf, die auf Programmebene auftreten: Festlegen der nächsten Anweisung, Ausführen, Schrittweisen, Fortsetzen, Anhalten und Fortsetzen.

 [Breakpoint-bezogene Methoden](../../extensibility/debugger/breakpoint-related-methods.md) Definiert die gebundenen und ausstehenden Typen von Haltepunkten, die Visual Studio unterstützt.

 [Anrufstapelauswertung](../../extensibility/debugger/call-stack-evaluation.md) Erläutert die Implementierung der Methoden, die die Anzeige der Stapelrahmen der Aufrufliste während des Unterbrechungsmodus ermöglichen.

 [Ausdrucksauswertung](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md) Erläutert, wie das Debugmodul (DE), die Ausdrucksauswertung (EE) und der Sitzungsdebug-Manager an der Analyse und Auswertung eines Ausdrucks beteiligt sind, der in eines der Fenster der IDE eingegeben wurde.

 [Steuern von Ereignissen](../../extensibility/debugger/control-events.md) Erläutert die Schnittstelle, die zum Senden von Ereignissen während der kontrollierten Ausführung des Programms verwendet wird.
