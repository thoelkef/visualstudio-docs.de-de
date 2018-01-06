---
title: Manager-Debugsitzung | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- session debug manager, unifying session views
- session debug manager, broadcasting
- debugging [Debugging SDK], session debug manager
- session debug manager
- session debug manager, debug engine multiplexing
- session debug manager, delegating
ms.assetid: fbb1928d-dddc-43d1-98a4-e23b0ecbae09
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7d7acd147fd8d2b73b2172900baf7e1f49808e9a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="session-debug-manager"></a>Sitzungs-Debug-Manager
Die Sitzungs-Debug-Manager (SDM) verwaltet eine beliebige Anzahl von Debugmodule (DE), die eine beliebige Anzahl von Programmen in mehreren Prozessen in einer beliebigen Anzahl von Computern zu debuggen. Abgesehen davon, dass ein Debugmodul multiplexer, bietet die SDM einen schnellen Überblick über die Debugsitzung der IDE an.  
  
## <a name="session-debug-manager-operation"></a>Sitzung Debug-Manager-Vorgang  
 Die Sitzungs-Debug-Manager (SDM) verwaltet die Deutschland. Es gibt möglicherweise mehr als ein Debugging-Modul zur gleichen Zeit auf einem Computer ausgeführt. Zum Bündeln von des DEs der SDM dient als Wrapper für eine Anzahl von Schnittstellen, von dem DEs und macht sie der IDE als eine einzelne Schnittstelle verfügbar.  
  
 Zur Erhöhung der Leistung, sind einige Schnittstellen nicht Multiplexbetrieb. Stattdessen werden sie direkt aus dem DE verwendet und Aufrufe auf diese Schnittstellen nicht durchlaufen die SDM. Mit Speicher, Code und Kontexte Dokument verwendete Schnittstellen sind z. B. nicht Multiplexbetrieb, da sie auf eine bestimmte Anweisung, Arbeitsspeicher oder Dokuments in ein bestimmtes Programm von einem bestimmten DE gedebuggt verweisen. Keine anderen DE muss in dieser Ebene der Kommunikation beteiligten sein.  
  
 Dies gilt nicht für alle Kontexte. Aufrufe der Ausdruck Auswertung Kontextschnittstelle durchlaufen die SDM ab. Während der Auswertung von Ausdrücken, die SDM dient als Wrapper für die [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) -Schnittstelle, die sie für die IDE bietet, da bei diesen Ausdruck ausgewertet wird, es muss möglicherweise mehrere des-, die Programme im selben Prozess debuggen, die möglicherweise auf dem gleichen Thread ausgeführt wird.  
  
 Die SDM fungiert in der Regel als delegierungsmechanismus für die, jedoch möglicherweise fungiert als einem Übertragungsmechanismus. Während der Auswertung von Ausdrücken fungiert der SDM als einem Übertragungsmechanismus alle des-benachrichtigen, dass sie Code für einen angegebenen Thread ausgeführt werden können. Wenn die SDM Stopping-Ereignis empfängt, sendet es auf ähnliche Weise auf alle Programme, dass ihre Ausführung beendet werden soll. Wenn ein Schritt aufgerufen wird, sendet der SDM auf alle Programme, die Ausführung fortgesetzt werden kann. Haltepunkte werden auch an jeder DE übermittelt.  
  
 Die SDM verfolgt nicht den aktuellen Programm, den Thread oder den Stapelrahmen entspricht. Der Prozess, Programm- und Thread Informationen an die SDM in Verbindung mit bestimmten Debugereignisse gesendet.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen des Datenbankmoduls](../../extensibility/debugger/debug-engine.md)   
 [Debuggerkomponenten](../../extensibility/debugger/debugger-components.md)   
 [Debuggerkontexte](../../extensibility/debugger/debugger-contexts.md)