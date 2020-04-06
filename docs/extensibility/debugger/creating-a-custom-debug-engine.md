---
title: Erstellen einer benutzerdefinierten Debug-Engine | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a350d640fffcc6e09cf8f981c797b97071a0cacf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739039"
---
# <a name="create-a-custom-debug-engine"></a>Erstellen eines benutzerdefinierten Debugmoduls
Ein Debugmodul (DE) ist eine Komponente, die das Debuggen bestimmter Laufzeitarchitekturen ermöglicht. Es gibt in der Regel nur eine DE-Implementierung pro Laufzeitumgebung.

> [!NOTE]
> Obwohl es separate DE-Implementierungen für Transact-SQL und JScript gibt, teilen VBScript und JScript eine einzelne DE.

 Eine DE arbeitet mit dem Interpreter oder Betriebssystem zusammen, um Debugdienste wie Ausführungssteuerung, Haltepunkte und Ausdrucksauswertung bereitzustellen. Diese Dienste werden über die DE-Schnittstellen implementiert und können dazu führen, dass der Debugger zwischen verschiedenen Betriebsmodi wechselt. Weitere Informationen finden Sie unter [Betriebsmodi](../../extensibility/debugger/operational-modes.md).

 Das Erstellen einer DE besteht aus den folgenden Schritten:

1. Registrieren einer DE bei Visual Studio

2. Aktivieren des Debuggens eines Programms

3. Implementieren von Ausführungssteuerung und Zustandsbewertung

4. Senden von Ereignisse

5. Beenden und Trennen einrichten

## <a name="in-this-section"></a>In diesem Abschnitt
 [Registrieren eines benutzerdefinierten Debugmoduls](../../extensibility/debugger/registering-a-custom-debug-engine.md) Erläutert die Schritte, die zum Registrieren eines Debugmoduls bei Visual Studio erforderlich sind, damit es verwendet werden kann.

 [Aktivieren des Debuggens eines Programms](../../extensibility/debugger/enabling-a-program-to-be-debugged.md) Erläutert, dass Sie die DE zuerst starten oder an ein vorhandenes Programm anfügen müssen, bevor Ihre DE ein Programm debuggen kann.

 [Implementieren von Ausführungssteuerung und Zustandsbewertung](../../extensibility/debugger/execution-control-and-state-evaluation.md) Erläutert, warum das Debuggen einer Anwendung das Implementieren von Ausführungssteuerungsfeatures erfordert.

 [Senden von Ereignissen](../../extensibility/debugger/sending-events.md) Beschreibt die Kommunikation zwischen dem Debugger und der DE als Ereignismodell basierend auf DCOM.

 [Beenden und Trennen](../../extensibility/debugger/termination-and-detaching.md) einrichten Erläutert, wie eine normale Beendigung erreicht wird, d. h., es gibt keine Haltepunkte, Ausnahmen, Laufzeitfehler oder Endlosschleifen in der zu debuggenden Anwendung.

 [Aufrufen von Debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md) Dokumentiert die Aufrufreihenfolge der Ereignisse, die in einer Debugsitzung auftreten.

 [Gewusst wie: Debuggen eines benutzerdefinierten Debugmoduls](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md) Erläutert, wie eine benutzerdefinierte DE gedebugpft wird.

## <a name="see-also"></a>Weitere Informationen
- [Erweiterbarkeit des Visual Studio-Debuggers](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
