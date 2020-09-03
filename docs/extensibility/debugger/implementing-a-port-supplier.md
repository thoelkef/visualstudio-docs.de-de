---
title: Implementieren eines Port Anbieters | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738559"
---
# <a name="implement-a-port-supplier"></a>Implementieren eines Port Anbieters
Ein Port Lieferant liefert Ports für die Anforderung an den Sitzungs-Debug-Manager (SDM). Ein Port Lieferant muss implementiert werden, wenn ein Debuggen auf einen nicht-DCOM-Computer oder ein neues Gerät unterstützt wird. Wenn Sie z. b. das Debuggen auf einem Mobiltelefon bereitstellen möchten, können Sie einen Port Lieferanten einrichten, der Ports bereitstellt, die eine Verbindung mit dem Mobiltelefon herstellen (z. b. über IR oder eine Zell Verbindung) und die Prozesse und Programme auflisten, die auf dem Telefon ausgeführt werden.

 Für das Debuggen von Programmen auf Windows-basierten Computern (einschließlich Remote Debuggen) stellt Visual Studio Port Lieferanten für systemeigene und CLR-Prozesse (Common Language Runtime) bereit, sodass Sie in diesen Fällen keinen eigenen Port Lieferanten einrichten müssen.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Implementieren und Registrieren eines Port Anbieters](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md) Erläutert, wie die SDM mit dem Port Lieferanten und seinen Ports interagiert.

 [Erforderliche Port Lieferanten Schnittstellen](../../extensibility/debugger/required-port-supplier-interfaces.md) Dokumentiert die Schnittstellen, die Sie implementieren müssen, um einen Port Lieferanten zu erhalten.

## <a name="related-sections"></a>Verwandte Abschnitte
 [Debugger-Konzepte](../../extensibility/debugger/debugger-concepts.md) Beschreibt die wichtigsten Konzepte der debuggingarchitektur.

## <a name="see-also"></a>Weitere Informationen
 [Erweiterbarkeit von Visual Studio-Debugger](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
