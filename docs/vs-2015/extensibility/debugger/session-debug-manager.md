---
title: Sitzungs-Debug-Manager | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157823"
---
# <a name="session-debug-manager"></a>Sitzungsbasierter Debug-Manager
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Der Sitzungs-Debug-Manager (SDM) verwaltet beliebig viele Programme in mehreren Prozessen auf einer beliebigen Anzahl von Computern. Die SDM ist nicht nur ein Debug Engine Multiplexer, sondern bietet eine einheitliche Ansicht der Debugsitzung für die IDE.  
  
## <a name="session-debug-manager-operation"></a>Sitzungs-Debug-Manager-Vorgang  
 Der Sitzungs-Debug-Manager (SDM) verwaltet den de. Auf einem Computer können gleichzeitig mehrere Debug-Engine ausgeführt werden. Der SDM umschließt eine Reihe von Schnittstellen aus dem des und macht Sie als eine einzige Schnittstelle für die IDE verfügbar, um den des zu multiplizieren.  
  
 Um die Leistung zu verbessern, werden einige Schnittstellen nicht multiplext. Stattdessen werden Sie direkt von der de verwendet, und Aufrufe an diese Schnittstellen durchlaufen nicht die SDM. Beispielsweise werden Schnittstellen, die mit Speicher-, Code-und Dokument Kontexten verwendet werden, nicht multiplext, da Sie auf eine bestimmte Anweisung, einen Speicher oder ein Dokument in einem bestimmten Programm verweisen, das von einer bestimmten de debuggten wird. An dieser Kommunikationsebene muss keine andere de beteiligt sein.  
  
 Dies gilt nicht für alle Kontexte. Aufrufe der Kontext Schnittstelle der Ausdrucks Auswertung durchlaufen die SDM. Während der Ausdrucks Auswertung umschließt SDM die [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) -Schnittstelle, die es der IDE zuweist, denn wenn dieser Ausdruck ausgewertet wird, kann er mehrere des umfassen, die Programme in demselben Prozess Debuggen, der möglicherweise im gleichen Thread ausgeführt wird.  
  
 Der SDM fungiert in der Regel als Delegierungs Mechanismus, kann aber auch als Übertragungsmechanismus fungieren. Während der Ausdrucks Auswertung fungiert die SDM z. b. als Übertragungsmechanismus, mit dem alle des benachrichtigt werden, dass Sie Code in einem bestimmten Thread ausführen können. Wenn das SDM ein anhalteereignis empfängt, sendet es auf ähnliche Weise an alle Programme, die nicht mehr ausgeführt werden sollen. Wenn ein Schritt aufgerufen wird, überträgt SDM an alle Programme, die Sie weiter ausführen können. Breakpoints werden ebenfalls an alle de gesendet.  
  
 Der SDM verfolgt das aktuelle Programm, den Thread oder den Stapel Rahmen nicht. Prozess-, Programm-und Thread Informationen werden in Verbindung mit bestimmten debuggingereignissen an die SDM gesendet.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Debug-Engine](../../extensibility/debugger/debug-engine.md)   
 [Debugger-Komponenten](../../extensibility/debugger/debugger-components.md)   
 [Debuggerkontexte](../../extensibility/debugger/debugger-contexts.md)
