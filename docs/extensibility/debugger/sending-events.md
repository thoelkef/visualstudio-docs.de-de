---
title: Senden von Ereignissen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5ec0d3aa29da562147b71b8efde49baf07d8ae0b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713040"
---
# <a name="send-events"></a>Senden von Ereignisse
Der Mechanismus für die Kommunikation zwischen dem Debugger und dem Debugmodul (DE) ist ein auf DCOM basierendes Ereignismodell. Ereignisse werden als COM-Objekte gesendet, und jedes Ereignis verfügt über Parameter, die Folgendes angeben:

- Die DE, die das Ereignis aufgerufen hat.

- Eine Beschreibung dessen, was passiert ist.

- Die Prozess-, Programm- und Threadinformationen, die den Kontext des Ereignisses identifizieren. Der Prozess wird nicht für Ereignisse gesendet, die von einer DE gesendet werden.

- Der Ereignistyp, der angibt, ob das Ereignis synchron oder asynchron ist.

  Alle Debugereignisse werden mit der Methode [IDebugEventCallback2::Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md)gesendet.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Ereignisquellen](../../extensibility/debugger/event-sources-visual-studio-sdk.md) Erläutert die beiden Ereignisquellen: das Debugmodul (DE) und den Sitzungsdebug-Manager (SDM).

 [Unterstützte Ereignistypen](../../extensibility/debugger/supported-event-types.md) Erläutert die aktuell unterstützten Ereignistypen: asynchron und synchron.

 [Ereignisbeschreibungen](../../extensibility/debugger/event-descriptions.md) Definiert Ereignisse und die Gründe für ihre Verwendung.

## <a name="related-sections"></a>Verwandte Abschnitte
 [Erstellen eines benutzerdefinierten Debugmoduls](../../extensibility/debugger/creating-a-custom-debug-engine.md) Beschreibt, wie eine DE mit dem Interpreter oder Betriebssystem zusammenarbeitet, um Debugdienste bereitzustellen.
