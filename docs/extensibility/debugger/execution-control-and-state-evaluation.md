---
title: Steuerung der Ausführung und Auswertung Status | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], execution control
- expression evaluation, control of execution
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d306ffe484605a081afa81afdcdcaa1a70339c84
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="execution-control-and-state-evaluation"></a>Steuerung der Ausführung und Auswertung Zustand
Debuggen einer Anwendung erfordert die Ausführung Steuerelement mit Funktionen wie die schrittweise Ausführung von Funktionen an Haltepunkten anhalten und Fortsetzen der Ausführung zu implementieren. Visual Studio-debugging Basen werden die Steuerung der Ausführung auf Ereignisse zwischen Debuggerkomponenten gesendet.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Programmsteuerung](../../extensibility/debugger/program-control.md)  
 Listet die folgenden Routinen, die auf der Ebene des Programms auftreten: Festlegen der nächsten Anweisung, Ausführung, schrittweises Ausführen, Sie den Vorgang fortsetzen, Anhalten und fortsetzen.  
  
 [Auf Haltepunkte bezogene Methoden](../../extensibility/debugger/breakpoint-related-methods.md)  
 Definiert die Grenze und ausstehende Typen von Haltepunkten, die Visual Studio unterstützt.  
  
 [Auswertung der Aufrufliste](../../extensibility/debugger/call-stack-evaluation.md)  
 Beschreibt die Implementierung der Methoden, mit die Anzeige der Stapelrahmen der Aufrufliste im Unterbrechungsmodus können.  
  
 [Ausdrucksauswertung](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
 Erklärt, wie die Debugging-Modul (DE) Ausdruck Evaluation (EE) und Sitzung Debug-Managers in die Analyse beteiligt sind, und Auswertung eines Ausdrucks in eines der Fenster der IDE eingegeben.  
  
 [Steuerelementereignisse](../../extensibility/debugger/control-events.md)  
 Beschreibt die Schnittstelle, die zum Senden von Ereignissen während der gesteuerte Ausführung des Programms an.