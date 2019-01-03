---
title: Manager-Debugsitzung | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- session debug manager, unifying session views
- session debug manager, broadcasting
- debugging [Debugging SDK], session debug manager
- session debug manager
- session debug manager, debug engine multiplexing
- session debug manager, delegating
ms.assetid: fbb1928d-dddc-43d1-98a4-e23b0ecbae09
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 014ac5b4c310b97fb1c041eeaededef8c97ab88b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53905357"
---
# <a name="session-debug-manager"></a>Sitzungsbasierter Debug-manager
Sitzungsbasierter Debug-Manager (SDM) verwaltet eine beliebige Anzahl von Debug-Engines (DE), die über eine beliebige Anzahl von Computern eine beliebige Anzahl von Programmen in mehrere Prozesse debuggen. Ein Debugmodul multiplexer, sondern bietet das SDM einen einheitlichen Überblick über die Debugsitzung der IDE.  
  
## <a name="session-debug-manager-operation"></a>Vorgang der Debug-manager  
 Sitzungsbasierter Debug-Manager (SDM) verwaltet die DE. Es können mehrere Debug-Engine auf einem Computer ausgeführt wird, gleichzeitig vorhanden sein. Um die Multiplexing der DEs, das SDM dient als Wrapper für eine Reihe von Schnittstellen, von dem DEs und macht sie für die IDE als eine einzige Schnittstelle verfügbar.  
  
 Um die Leistung zu erhöhen, werden nicht einige Schnittstellen Multiplexbetrieb. Stattdessen werden sie direkt aus dem DE verwendet, und Aufrufe an diese Schnittstellen nicht das SDM durchlaufen. Beispielsweise sind nicht Schnittstellen, Arbeitsspeicher, Code und dokumentenkontexte Multiplexing, da sie auf eine bestimmte Anweisung, Arbeitsspeicher oder Dokuments in ein bestimmtes Programm debuggen, indem Sie eine bestimmte DE verweisen. Keine anderen DE muss in dieser Kommunikation einbezogen werden.  
  
 Dies gilt nicht für alle Kontexte. Aufrufe von Ausdruck Auswertung Context-Schnittstelle ist das SDM durchlaufen. Beim Auswerten, des Ausdrucks das SDM dient als Wrapper für die [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) -Schnittstelle, die sie für die IDE bietet, da bei diesen Ausdruck ausgewertet wird, es spielt mehrere DEs, die Programme im selben Prozess debuggen, die möglicherweise Klicken Sie auf dem gleichen Thread ausgeführt werden.  
  
 Das SDM fungiert in der Regel als einen delegierungsmechanismus, aber es kann als ein broadcast-Mechanismus verwendet werden. Beispielsweise fungiert beim Auswerten, des Ausdrucks das SDM als ein broadcast-Mechanismus alle DEs benachrichtigt, dass sie Code für einen angegebenen Thread ausgeführt werden können. Wenn das SDM Stopping-Ereignis empfängt, sendet es auf ähnliche Weise für die Programme an, dass diese Ausführung beendet werden soll. Wenn ein Schritt aufgerufen wird, überträgt das SDM für die Programme, die Ausführung fortgesetzt werden kann. Haltepunkte sind auch an jeder DE übertragen.  
  
 Das SDM verfolgt nicht die aktuellen Programm, Threads und Stapelrahmen. Der Prozess, Programm und Threadinformationen werden an das SDM in Verbindung mit bestimmten Debugereignisse gesendet.  
  
## <a name="see-also"></a>Siehe auch  
 [Debug-engine](../../extensibility/debugger/debug-engine.md)   
 [Debugger-Komponenten](../../extensibility/debugger/debugger-components.md)   
 [Debuggerkontexte](../../extensibility/debugger/debugger-contexts.md)