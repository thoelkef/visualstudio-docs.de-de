---
title: Erstellen einer benutzerdefinierten Modul Debuggen | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0edee6528919cfe28c542be850b9a104188ce403
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="creating-a-custom-debug-engine"></a>Erstellen einer benutzerdefinierten Debugmodul
Ein Debugging-Modul (DE) ist eine Komponente, die ermöglicht das Debuggen von bestimmten-Laufzeit-Architekturen. Es ist in der Regel nur ein DE-Implementierung pro-Umgebung ausgeführt.  
  
> [!NOTE]
>  Es gibt separate DE-Implementierungen für Transact-SQL und JScript, VBScript und JScript einer einzelnen Deutschland freigeben.  
  
 Ein DE funktioniert mit Interpreter oder Vorgang solche Debugdienste Ausführung-Steuerelement, Haltepunkte und Ausdruck Evaluierungsversion bereit. Diese Dienste werden über die DE-Schnittstellen implementiert und können dazu führen, dass den Debugger für den Übergang zwischen den verschiedenen Betriebsmodi. Weitere Informationen finden Sie unter [Betriebsmodi](../../extensibility/debugger/operational-modes.md).  
  
 Erstellung einer bereitgestellten Kompatibilitätsrichtlinie gehören die folgenden Schritte aus:  
  
1.  Registrieren einer bereitgestellten Kompatibilitätsrichtlinie mit Visual Studio  
  
2.  Aktivieren ein Programm, das gedebuggt werden  
  
3.  Ausführung-Steuerelement und Status-Bewertung  
  
4.  Senden von Ereignissen  
  
5.  Beenden und trennen  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Registrieren eines benutzerdefinierten Debugmoduls](../../extensibility/debugger/registering-a-custom-debug-engine.md)  
 Erläutert die Schritte erforderlich, um ein Debugmodul mit Visual Studio zu registrieren, sodass sie verwendet werden kann.  
  
 [Aktivieren eines Programms für das Debuggen](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)  
 Erläutert, bevor Ihre DE ein Programm debuggen kann, muss zuerst die DE starten oder an ein vorhandenes Programm angefügt.  
  
 [Ausführungssteuerung und Zustandsauswertung](../../extensibility/debugger/execution-control-and-state-evaluation.md)  
 Erläutert, warum das Debuggen einer Anwendung benötigt Ausführungsfunktionen für Steuerelement implementieren.  
  
 [Senden von Ereignissen](../../extensibility/debugger/sending-events.md)  
 Wird die Kommunikation zwischen dem Debugger und die DE als ein Ereignismodell, basierend auf DCOM beschrieben.  
  
 [Beenden und Trennen](../../extensibility/debugger/termination-and-detaching.md)  
 Erläutert die normalen Beendigung zu erreichen, d. h. Es gibt keine Haltepunkte, Ausnahmen, die Laufzeitfehler oder Endlosschleifen in der Anwendung, die debuggt werden.  
  
 [Aufrufen von Debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)  
 Dokumentiert die aufrufende Reihenfolge der Ereignisse, die in einer Debugsitzung auftreten.  
  
 [Gewusst wie: Debuggen eines benutzerdefinierten Debugmoduls](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md)  
 Erläutert, wie eine benutzerdefinierte DE zu debuggen.  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio Debugger-Erweiterbarkeit](../../extensibility/debugger/visual-studio-debugger-extensibility.md)