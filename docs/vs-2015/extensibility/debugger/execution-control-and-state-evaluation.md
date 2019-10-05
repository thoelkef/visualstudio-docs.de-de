---
title: Ausführungssteuerung und Zustandsauswertung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], execution control
- expression evaluation, control of execution
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bc6476c925f37d70ab45bae129a8b8a379ee519c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68152768"
---
# <a name="execution-control-and-state-evaluation"></a>Ausführungssteuerung und Zustandsauswertung
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Debuggen einer Anwendung erfordert die Implementierung von Ausführung Steuerelement Features wie Funktionen schrittweise an Haltepunkten anhalten und Fortsetzen der Ausführung. Visual Studio-debugging Basen werden die Steuerung der Ausführung auf Ereignissen zwischen Debuggerkomponenten gesendet.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Programmsteuerung](../../extensibility/debugger/program-control.md)  
 Listet die folgenden Routinen, die auf Programmebene auftreten: Festlegen der nächsten Anweisung, Ausführung, schrittweise ausführen, Sie den Vorgang fortsetzen, Anhalten und fortsetzen.  
  
 [Auf Haltepunkte bezogene Methoden](../../extensibility/debugger/breakpoint-related-methods.md)  
 Definiert die Grenze und die ausstehenden Typen von Haltepunkten, die Visual Studio unterstützt.  
  
 [Auswertung der Aufrufliste](../../extensibility/debugger/call-stack-evaluation.md)  
 Beschreibt die Implementierung der Methoden, mit die der Stapelrahmen der Aufrufliste anzeigen, während des Unterbrechungsmodus können.  
  
 [Ausdrucksauswertung](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
 Erläutert, wie die Debug-Engine (DE), Ausdruck Evaluation (EE) und Sitzung Debug-Manager sind beteiligt, bei der Analyse und Auswertung eines Ausdrucks in eines der Fenster der IDE.  
  
 [Steuerelementereignisse](../../extensibility/debugger/control-events.md)  
 Erläutert die verwendete Schnittstelle zum Senden von Ereignissen während der kontrollierten Ausführung des Programms an.
