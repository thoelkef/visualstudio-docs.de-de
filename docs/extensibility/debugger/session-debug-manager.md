---
title: Sitzungs-Debug-Manager | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- session debug manager, unifying session views
- session debug manager, broadcasting
- debugging [Debugging SDK], session debug manager
- session debug manager
- session debug manager, debug engine multiplexing
- session debug manager, delegating
ms.assetid: fbb1928d-dddc-43d1-98a4-e23b0ecbae09
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 953b4e948ef5e21531a3e73bceed3a363ed3cec5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712887"
---
# <a name="session-debug-manager"></a>Sitzungsdebug-Manager
Der Session Debug Manager (SDM) verwaltet eine beliebige Anzahl von Debugmodulen (DE), die eine beliebige Anzahl von Programmen in mehreren Prozessen auf einer beliebigen Anzahl von Computern debuggen. Das SDM ist nicht nur ein Debugmodul-Multiplexer, sondern bietet auch eine einheitliche Ansicht der Debugsitzung für die IDE.

## <a name="session-debug-manager-operation"></a>Sitzungsdebug-Manager-Vorgang
 Der Session Debug Manager (SDM) verwaltet die DE. Es können mehrere Debug-Engine auf einem Computer gleichzeitig ausgeführt werden. Um die DEs zu multiplexen, umschließt das SDM eine Reihe von Schnittstellen aus den DEs und macht sie der IDE als eine einzige Schnittstelle.

 Um die Leistung zu erhöhen, werden einige Schnittstellen nicht multiplexiert. Stattdessen werden sie direkt von der DE verwendet, und Aufrufe zu diesen Schnittstellen werden nicht über das SDM. Schnittstellen, die mit Speicher-, Code- und Dokumentkontexten verwendet werden, werden beispielsweise nicht multiplexiert, da sie auf eine bestimmte Anweisung, einen Arbeitsspeicher oder ein Dokument in einem bestimmten Programm verweisen, das von einer bestimmten DE gedebugbel wird. Kein anderes DE muss in diese Kommunikationsebene einbezogen werden.

 Dies gilt nicht für alle Kontexte. Aufrufe der Kontextschnittstelle für die Ausdrucksauswertung durchlaufen das SDM. Während der Ausdrucksauswertung umschließt das SDM die [IDebugExpression2-Schnittstelle,](../../extensibility/debugger/reference/idebugexpression2.md) die es der IDE gibt, da es bei der Auswertung dieses Ausdrucks mehrere DEs umfassen kann, die Programme im gleichen Prozess debuggen, die möglicherweise auf demselben Thread ausgeführt werden.

 Das SDM fungiert in der Regel als Delegierungsmechanismus, kann jedoch als Broadcast-Mechanismus fungieren. Während der Ausdrucksauswertung fungiert das SDM beispielsweise als Broadcast-Mechanismus, um alle DEs darüber zu informieren, dass sie Code in einem angegebenen Thread ausführen können. Wenn das SDM ein Stoppereignis empfängt, wird es an die Programme gesendet, die nicht mehr ausgeführt werden sollen. Wenn ein Schritt aufgerufen wird, sendet das SDM an die Programme, die weiterhin ausgeführt werden können. Haltepunkte werden auch an jeden DE gesendet.

 Das SDM verfolgt nicht das aktuelle Programm, den Thread oder den Stapelrahmen. Die Prozess-, Programm- und Threadinformationen werden in Verbindung mit bestimmten Debugereignissen an das SDM gesendet.

## <a name="see-also"></a>Weitere Informationen
- [Debug-Engine](../../extensibility/debugger/debug-engine.md)
- [Debugger-Komponenten](../../extensibility/debugger/debugger-components.md)
- [Debuggerkontexte](../../extensibility/debugger/debugger-contexts.md)
