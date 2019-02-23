---
title: Erstellen einer benutzerdefinierten Debug-Engine | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5273270905c99b565fe4fd455e9c5c505af9c878
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56711097"
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
 [Registrieren eine benutzerdefinierten Debug-Engine](../../extensibility/debugger/registering-a-custom-debug-engine.md) erläutert die Schritte erforderlich, um eine Debug-Engine mit Visual Studio zu registrieren, sodass sie verwendet werden kann.

 [Aktivieren ein Programms zu debuggende](../../extensibility/debugger/enabling-a-program-to-be-debugged.md) erläutert wird, bevor Ihre DE ein Programm debuggen kann, müssen zunächst die DE starten oder fügen Sie ihn an ein vorhandenes Programm.

 [Implementieren Sie die Ausführung und Auswertung](../../extensibility/debugger/execution-control-and-state-evaluation.md) erläutert, warum Debuggen einer Anwendung erfordert die Implementierung von Ausführungsfunktionen für Steuerelement.

 [Senden von Ereignissen](../../extensibility/debugger/sending-events.md) beschreibt Kommunikation zwischen dem Debugger und die DE ein Ereignismodell auf der Grundlage von DCOM.

 [Richten Sie beenden und trennen](../../extensibility/debugger/termination-and-detaching.md) wird erläutert, wie normalen Beendigung zu erreichen, d. h. Es gibt keine Haltepunkte, Ausnahmen, Laufzeitfehlern führen oder Endlosschleifen in der Anwendung, die debuggt werden.

 [Aufrufen von debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md) dokumentiert die Aufrufreihenfolge der Ereignisse, die in einer Debugsitzung.

 [How To: Debuggen eine benutzerdefinierten Debug-Engine](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md) wird erläutert, wie eine benutzerdefinierte DE zu debuggen.

## <a name="see-also"></a>Siehe auch
- [Visual Studio-Debugger-Erweiterbarkeit](../../extensibility/debugger/visual-studio-debugger-extensibility.md)