---
title: Ausführungs Steuerung und Zustands Auswertung | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738754"
---
# <a name="execution-control-and-state-evaluation"></a>Ausführungs Steuerung und Zustands Auswertung
Das Debuggen einer Anwendung erfordert die Implementierung solcher Ausführungs Steuerungsfunktionen als schrittweise Ausführung von Funktionen, Anhalten an Haltepunkten und Fortsetzen der Ausführung. Das Visual Studio-debuggen basiert auf den Ereignissen, die zwischen Debugger-Komponenten gesendet werden

## <a name="in-this-section"></a>In diesem Abschnitt
 [Programmsteuerung](../../extensibility/debugger/program-control.md) Listet die folgenden Routinen auf, die auf der Programmebene auftreten: Festlegen der nächsten Anweisung, ausführen, Schritt-und fortsetzen, anhalten und fortsetzen.

 [Methoden im Zusammenhang mit Breakpoints](../../extensibility/debugger/breakpoint-related-methods.md) Definiert die gebundenen und ausstehenden Typen von Breakpoints, die von Visual Studio unterstützt werden.

 [Auswertung von aufrufstapeln](../../extensibility/debugger/call-stack-evaluation.md) Erläutert die Implementierung der Methoden, die das Anzeigen der Stapel Rahmen der aufzurufenden Stapel Rahmen im Break-Modus ermöglichen.

 [Ausdrucks Auswertung](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md) Erläutert, wie die Debug-Engine (de), Ausdrucks Auswertung (EE) und Session Debug Manager an der Analyse und Auswertung eines Ausdrucks beteiligt sind, der in eines der Fenster der IDE eingegeben wurde.

 [Steuerelement Ereignisse](../../extensibility/debugger/control-events.md) Erläutert die Schnittstelle, die zum Senden von Ereignissen während der kontrollierten Ausführung des Programms verwendet wird.
