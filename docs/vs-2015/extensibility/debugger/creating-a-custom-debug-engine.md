---
title: Erstellen einer benutzerdefinierten Debug-Engine | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 829e484ffe4968cdb89ff04e4e7f145decd07c9c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60111518"
---
# <a name="creating-a-custom-debug-engine"></a>Erstellen einer benutzerdefinierten Debug-Engine
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ein Debugmodul (DE) ist eine Komponente, die ermöglicht das Debuggen von bestimmten Laufzeit-Architekturen. Es gibt in der Regel nur eine Implementierung von DE pro-Umgebung ausgeführt.  
  
> [!NOTE]
>  Es gibt separate DE-Implementierungen für Transact-SQL und JScript, VBScript und JScript einer einzelnen DE freigeben.  
  
 Eine bereitgestellten Kompatibilitätsrichtlinie arbeitet mit den Interpreter oder Vorgang System solche Debugdienste Ausführung-Steuerelement, Haltepunkte und Ausdruck Evaluierungsversion bereit. Diese Dienste werden über die DE-Schnittstellen implementiert und können dazu führen, dass den Debugger für den Übergang zwischen verschiedenen Betriebsmodi. Weitere Informationen finden Sie unter [Betriebsmodi](../../extensibility/debugger/operational-modes.md).  
  
 Zur Erstellung einer bereitgestellten Kompatibilitätsrichtlinie gehören die folgenden Schritte aus:  
  
1. Registrieren einer bereitgestellten Kompatibilitätsrichtlinie mit Visual Studio  
  
2. Aktivieren eines Programms, die debuggt werden  
  
3. Ausführung und Auswertung  
  
4. Senden von Ereignissen  
  
5. Beenden und trennen  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Registrieren einer benutzerdefinierten Debug-Engine](../../extensibility/debugger/registering-a-custom-debug-engine.md)  
 Erläutert die Schritte erforderlich, um eine Debug-Engine mit Visual Studio zu registrieren, sodass sie verwendet werden kann.  
  
 [Aktivieren eines Programms für das Debuggen](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)  
 Erläutert, bevor Ihre DE ein Programm debuggen kann, müssen zunächst die DE starten oder fügen Sie ihn an ein vorhandenes Programm an.  
  
 [Ausführungssteuerung und Zustandsauswertung](../../extensibility/debugger/execution-control-and-state-evaluation.md)  
 Erläutert, warum Debuggen einer Anwendung erfordert die Implementierung von Ausführungsfunktionen für Steuerelement.  
  
 [Senden von Ereignissen](../../extensibility/debugger/sending-events.md)  
 Wird die Kommunikation zwischen dem Debugger und die DE als ein Ereignismodell, das auf DCOM basierende beschrieben.  
  
 [Beenden und Trennen](../../extensibility/debugger/termination-and-detaching.md)  
 Es wird erläutert, wie normalen Beendigung zu erreichen, d. h. Es gibt keine Haltepunkte, Ausnahmen, Laufzeitfehlern führen oder Endlosschleifen in der Anwendung, die debuggt werden.  
  
 [Aufrufen von Debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)  
 Dokumentiert die Aufrufreihenfolge der Ereignisse, die in einer Debugsitzung an.  
  
 [How To: Debug a Custom Debug Engine (Vorgehensweise: Debuggen einer benutzerdefinierten Debug-Engine)](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md)  
 Erläutert, wie eine benutzerdefinierte DE zu debuggen.  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio Debugger-Erweiterbarkeit](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
