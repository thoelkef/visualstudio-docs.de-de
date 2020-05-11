---
title: Implementieren eines Hafenlieferanten | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8218e372ad3aece922811bc20cfd7650f33296f3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738559"
---
# <a name="implement-a-port-supplier"></a>Implementieren eines Portlieferanten
Ein Portlieferant liefert Ports auf Anfrage an den Sitzungsdebug-Manager (SDM). Ein Portlieferant muss beim Debuggen auf einen Nicht-DCOM-Computer oder wenn ein neues Gerät Unterstützung benötigt, implementiert werden. Um beispielsweise das Debuggen für ein Mobiltelefon bereitzustellen, können Sie einen Portanbieter einrichten, der Ports bereitstellt, die eine Verbindung zum Mobiltelefon herstellen (möglicherweise über IR oder eine Mobilfunkverbindung) und die auf dem Telefon ausgeführten Prozesse und Programme aufzählt.

 Für das Debuggen von Programmen auf Windows-basierten Computern (einschließlich Remotedebugging) stellt Visual Studio Portlieferanten für systemeigene und CLR-Prozesse (Common Language Runtime) bereit, sodass in diesen Fällen kein eigener Portlieferant eingerichtet werden muss.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Implementieren und Registrieren eines Hafenlieferanten](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md) Erläutert, wie das SDM mit dem Portanbieter und seinen Ports interagiert.

 [Erforderliche Port-Lieferanten-Schnittstellen](../../extensibility/debugger/required-port-supplier-interfaces.md) Dokumentiert die Schnittstellen, die Sie implementieren müssen, um einen Portlieferanten zu erhalten.

## <a name="related-sections"></a>Verwandte Abschnitte
 [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md) Beschreibt die wichtigsten Architekturkonzepte für das Debuggen.

## <a name="see-also"></a>Weitere Informationen
 [Erweiterbarkeit des Visual Studio-Debuggers](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
