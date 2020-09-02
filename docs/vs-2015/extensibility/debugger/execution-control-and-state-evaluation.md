---
title: Ausführungs Steuerung und Zustands Auswertung | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152768"
---
# <a name="execution-control-and-state-evaluation"></a>Ausführungssteuerung und Zustandsauswertung
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Das Debuggen einer Anwendung erfordert die Implementierung solcher Ausführungs Steuerungsfunktionen als schrittweise Ausführung von Funktionen, Anhalten an Haltepunkten und Fortsetzen der Ausführung. Das Visual Studio-debuggen basiert auf den Ereignissen, die zwischen Debugger-Komponenten gesendet werden  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Programmsteuerung](../../extensibility/debugger/program-control.md)  
 Listet die folgenden Routinen auf, die auf der Programmebene auftreten: Festlegen der nächsten Anweisung, ausführen, Schritt-und fortsetzen, anhalten und fortsetzen.  
  
 [Auf Haltepunkte bezogene Methoden](../../extensibility/debugger/breakpoint-related-methods.md)  
 Definiert die gebundenen und ausstehenden Typen von Breakpoints, die von Visual Studio unterstützt werden.  
  
 [Auswertung der Aufrufliste](../../extensibility/debugger/call-stack-evaluation.md)  
 Erläutert die Implementierung der Methoden, die das Anzeigen der Stapel Rahmen der aufzurufenden Stapel Rahmen im Break-Modus ermöglichen.  
  
 [Ausdrucksauswertung](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
 Erläutert, wie die Debug-Engine (de), Ausdrucks Auswertung (EE) und Session Debug Manager an der Analyse und Auswertung eines Ausdrucks beteiligt sind, der in eines der Fenster der IDE eingegeben wurde.  
  
 [Steuerelementereignisse](../../extensibility/debugger/control-events.md)  
 Erläutert die Schnittstelle, die zum Senden von Ereignissen während der kontrollierten Ausführung des Programms verwendet wird.
