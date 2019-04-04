---
title: Manager-Debugsitzung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- session debug manager, unifying session views
- session debug manager, broadcasting
- debugging [Debugging SDK], session debug manager
- session debug manager
- session debug manager, debug engine multiplexing
- session debug manager, delegating
ms.assetid: fbb1928d-dddc-43d1-98a4-e23b0ecbae09
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9fd7c7555c19f850a15161f6fba00b1184621a9e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58960877"
---
# <a name="session-debug-manager"></a>Sitzungsbasierter Debug-Manager
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Sitzungsbasierter Debug-Manager (SDM) verwaltet eine beliebige Anzahl von Debug-Engines (DE) eine beliebige Anzahl von Programmen in mehreren Prozessen auf eine beliebige Anzahl von Computern zu debuggen. Ein Debugmodul multiplexer, sondern bietet das SDM einen einheitlichen Überblick über die Debugsitzung der IDE.  
  
## <a name="session-debug-manager-operation"></a>Vorgang der Debug-Manager  
 Sitzungsbasierter Debug-Manager (SDM) verwaltet die DE. Es gibt möglicherweise mehr als eine Debug-Engine auf einem Computer zur gleichen Zeit ausgeführt. Um die Multiplexing der DEs, das SDM dient als Wrapper für eine Reihe von Schnittstellen, von dem DEs und macht sie für die IDE als eine einzige Schnittstelle verfügbar.  
  
 Um die Leistung zu erhöhen, werden einige Schnittstellen nicht Multiplexbetrieb. Stattdessen werden sie direkt aus dem DE verwendet, und Aufrufe an diese Schnittstellen navigieren nicht über das SDM. Mit Speicher, Code und dokumentenkontexte verwendete Schnittstellen sind z. B. nicht Multiplexing, da sie auf eine bestimmte Anweisung, Arbeitsspeicher oder Dokuments in ein bestimmtes Programm debuggen, indem Sie eine bestimmte DE verweisen. Keine anderen DE muss in dieser Kommunikation einbezogen werden.  
  
 Dies gilt nicht für alle Kontexte. Aufrufe von Ausdruck Auswertung Context-Schnittstelle ist das SDM durchlaufen. Beim Auswerten, des Ausdrucks das SDM dient als Wrapper für die [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) -Schnittstelle, die sie für die IDE bietet, da bei diesen Ausdruck ausgewertet wird, es spielt mehrere DEs, die Programme im selben Prozess debuggen, die möglicherweise Klicken Sie auf dem gleichen Thread ausgeführt werden.  
  
 Das SDM fungiert in der Regel als einen delegierungsmechanismus, aber es kann als ein broadcast-Mechanismus verwendet werden. Beispielsweise fungiert beim Auswerten, des Ausdrucks das SDM als ein broadcast-Mechanismus alle DEs benachrichtigt, dass sie Code für einen angegebenen Thread ausgeführt werden können. Wenn das SDM Stopping-Ereignis empfängt, sendet es auf ähnliche Weise auf alle Programme, dass diese Ausführung beendet werden soll. Wenn ein Schritt aufgerufen wird, überträgt das SDM auf alle Programme, die Ausführung fortgesetzt werden kann. Haltepunkte sind auch an jeder DE übertragen.  
  
 Das SDM verfolgt nicht die aktuellen Programm, Threads und Stapelrahmen. Der Prozess, Anwendung und Thread Informationen an das SDM in Verbindung mit bestimmten Debugereignisse gesendet.  
  
## <a name="see-also"></a>Siehe auch  
 [Debug-Engine](../../extensibility/debugger/debug-engine.md)   
 [Debugger-Komponenten](../../extensibility/debugger/debugger-components.md)   
 [Debuggerkontexte](../../extensibility/debugger/debugger-contexts.md)
