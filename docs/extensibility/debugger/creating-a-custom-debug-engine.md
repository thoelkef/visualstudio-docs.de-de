---
title: Erstellen einer benutzerdefinierten Debug-Engine | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ece2b480890054526552ad3aeea4f3bd1a437f74
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2018
ms.locfileid: "39203679"
---
# <a name="create-a-custom-debug-engine"></a>Erstellen einer benutzerdefinierten Debug-engine
Ein Debugmodul (DE) ist eine Komponente, die ermöglicht das Debuggen von bestimmten Laufzeit-Architekturen. Es gibt in der Regel nur eine Implementierung von DE pro-Umgebung ausgeführt.  
  
> [!NOTE]
>  Es gibt separate DE-Implementierungen für Transact-SQL und JScript, VBScript und JScript einer einzelnen DE freigeben.  
  
 Eine bereitgestellten Kompatibilitätsrichtlinie arbeitet mit den Interpreter oder Vorgang System solche Debugdienste Ausführung-Steuerelement, Haltepunkte und Ausdruck Evaluierungsversion bereit. Diese Dienste werden über die DE-Schnittstellen implementiert und können dazu führen, dass den Debugger für den Übergang zwischen verschiedenen Betriebsmodi. Weitere Informationen finden Sie unter [Betriebsmodi](../../extensibility/debugger/operational-modes.md).  
  
 Zur Erstellung einer bereitgestellten Kompatibilitätsrichtlinie gehören die folgenden Schritte aus:  
  
1.  Registrieren einer bereitgestellten Kompatibilitätsrichtlinie in Visual Studio  
  
2.  Aktivieren Sie zu debuggenden Programm  
  
3.  Implementieren Sie die Ausführung und Auswertung  
  
4.  Senden von Ereignissen  
  
5.  Richten Sie beenden und trennen  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Registrieren einer benutzerdefinierten Debug-engine](../../extensibility/debugger/registering-a-custom-debug-engine.md)  
 Erläutert die Schritte erforderlich, um eine Debug-Engine mit Visual Studio zu registrieren, sodass sie verwendet werden kann.  
  
 [Aktivieren Sie zu debuggenden Programm](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)  
 Erläutert, bevor Ihre DE ein Programm debuggen kann, müssen zunächst die DE starten oder fügen Sie ihn an ein vorhandenes Programm an.  
  
 [Implementieren Sie die Ausführung und Auswertung](../../extensibility/debugger/execution-control-and-state-evaluation.md)  
 Erläutert, warum Debuggen einer Anwendung erfordert die Implementierung von Ausführungsfunktionen für Steuerelement.  
  
 [Senden von Ereignissen](../../extensibility/debugger/sending-events.md)  
 Wird die Kommunikation zwischen dem Debugger und die DE als ein Ereignismodell, das auf DCOM basierende beschrieben.  
  
 [Richten Sie beenden und trennen](../../extensibility/debugger/termination-and-detaching.md)  
 Es wird erläutert, wie normalen Beendigung zu erreichen, d. h. Es gibt keine Haltepunkte, Ausnahmen, Laufzeitfehlern führen oder Endlosschleifen in der Anwendung, die debuggt werden.  
  
 [Aufrufen von debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)  
 Dokumentiert die Aufrufreihenfolge der Ereignisse, die in einer Debugsitzung an.  
  
 [Gewusst wie: Debuggen eine benutzerdefinierten Debug-engine](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md)  
 Erläutert, wie eine benutzerdefinierte DE zu debuggen.  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio-Debugger-Erweiterbarkeit](../../extensibility/debugger/visual-studio-debugger-extensibility.md)