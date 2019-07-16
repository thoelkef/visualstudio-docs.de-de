---
title: Implementieren eines Portanbieters | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dd5ba2a96b94cce65dc901a523232b1c3e0a45b9
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349988"
---
# <a name="implement-a-port-supplier"></a>Implementieren eines portanbieters
Ein portanbieters liefert Ports bei Anforderung an die sitzungsbasierter Debug-Manager (SDM). Ein portanbieters muss implementiert werden, wenn Debuggen auf einem nicht-DCOM-Computer oder wenn ein neues Gerät unterstützen muss. Beispielsweise können um debugging für ein Mobiltelefon zu ermöglichen, Sie eines portanbieters einrichten, die Ports, die Verbindung mit dem Mobiltelefon (z. B. über IR oder einer Zelle Verbindung), und listet die Prozesse und Programme stellt, die auf dem Telefon ausgeführt.

 Für das Debuggen von Programmen auf Windows-basierten Computern (einschließlich Remotedebuggen) bietet Visual Studio Portanbieter für systemeigenen und Common Language Runtime (CLR)-Prozesse, daher keine Notwendigkeit besteht, um Ihre eigenen anschlusslieferant in diesen Fällen einzurichten.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Implementieren und registrieren ein portanbieters](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md) wird erläutert, wie das SDM mit Anschlusslieferanten und ihrer Ports interagiert.

 [Erforderliche Port Lieferanten Schnittstellen](../../extensibility/debugger/required-port-supplier-interfaces.md) dokumentiert die Schnittstellen, die Sie zum Abrufen eines portanbieters implementieren müssen.

## <a name="related-sections"></a>Verwandte Abschnitte
 [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md) beschreibt die wichtigsten Konzepte für das Debuggen Architektur.

## <a name="see-also"></a>Siehe auch
 [Visual Studio-Debugger-Erweiterbarkeit](../../extensibility/debugger/visual-studio-debugger-extensibility.md)