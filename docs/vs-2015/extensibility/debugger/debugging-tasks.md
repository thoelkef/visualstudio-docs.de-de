---
title: Debuggingaufgaben | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 64a9a55a659b4aaa81a1e491445400d18de30a40
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47522736"
---
# <a name="debugging-tasks"></a>Debuggingaufgaben
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Debuggen Aufgaben](https://docs.microsoft.com/visualstudio/extensibility/debugger/debugging-tasks).  
  
Um ein Programm zu debuggen, es muss gestartet werden und eine Debug-Engine (DE) angefügt werden muss, andernfalls die DE muss an eine bereits gestartete Programm angefügt werden. Nach dem Anfügen, muss die DE bestimmte Startup-Ereignisse generieren. Das debugpaket versucht, in der Antwort die Haltepunkte, die in der IDE zu binden. Wenn das Programm einen gebundenen Haltepunkt trifft, hält und Benutzereingaben wartet.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Sicherheitsprobleme](../../extensibility/debugger/security-issues.md)  
 Erläutert die Schritte, die zum Debuggen eines Programms erforderlich sind.  
  
 [Starten eines Programms](../../extensibility/debugger/launching-a-program.md)  
 Enthält schrittweise Anleitungen zum Angeben einer bereitgestellten Kompatibilitätsrichtlinie, das Betriebssystem Ruft, um das Programm zu starten.  
  
 [Direktes Anfügen an ein Programm](../../extensibility/debugger/attaching-directly-to-a-program.md)  
 Beschreibt den Prozess verwendet, um ein Programm in einem Prozess zu debuggen, die bereits ausgeführt wird.  
  
 [Senden von Startereignissen nach einem Start](../../extensibility/debugger/sending-startup-events-after-a-launch.md)  
 Listet die Ereignisse, die stattfinden, sobald die DE für das Programm, angefügt ist, bis das Programm auf der Haupteinstiegspunkt und zum Debuggen bereit ist.  
  
 [Steuern der Ausführung](../../extensibility/debugger/control-of-execution.md)  
 Erläutert, wie die DE in der Regel ein Einstiegspunkt-Ereignis, ein Load-complete-Ereignis oder eine Beenden-Ereignis, je nach den Umständen sendet.  
  
 [Binden von Haltepunkten](../../extensibility/debugger/binding-breakpoints.md)  
 Beschreibt, wie, wenn der Benutzer einen Haltepunkt festlegt, die IDE die Anforderung formuliert und werden aufgefordert, die Debugsitzung, um den Haltepunkt zu erstellen.  
  
 [Auswerten von Ausdrücken](../../extensibility/debugger/evaluating-expressions.md)  
 Erläutert, wie Ausdrücke erstellt werden und was geschieht, wenn ein Ausdruck ausgewertet wird.  
  
 [Visualisieren und Anzeigen von Daten](../../extensibility/debugger/visualizing-and-viewing-data.md)  
 Erläutert, wie von der ausdrucksauswertung (EE) typschnellansichten und benutzerdefinierten Viewer unterstützt werden.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md)  
 Beschreibt die wichtigsten Konzepte für das Debuggen Architektur an.  
  
 [Debuggerkomponenten](../../extensibility/debugger/debugger-components.md)  
 Bietet eine Übersicht über Visual Studio debugging-Komponenten, z. B. die DE, EE und Symbol Handler (SH).  
  
 [Debuggerkontexte](../../extensibility/debugger/debugger-contexts.md)  
 Erläutert, wie die DE gleichzeitig in Code, Dokumentationen und Auswertung von ausdruckskontexten arbeitet. Beschreibt, für jede der drei Kontexten, Speicherort, Position oder Auswertung, die für sie relevant.  
  
## <a name="see-also"></a>Siehe auch  
 [Erste Schritte](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)

