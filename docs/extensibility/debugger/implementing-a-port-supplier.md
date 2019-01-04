---
title: Implementieren eines Portanbieters | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cd068f9c669b898ac3d29dadccffb6edd1e0c783
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53985523"
---
# <a name="implement-a-port-supplier"></a>Implementieren eines portanbieters
Ein portanbieters liefert Ports bei Anforderung an die sitzungsbasierter Debug-Manager (SDM). Ein portanbieters muss implementiert werden, wenn Debuggen auf einem nicht-DCOM-Computer oder wenn ein neues Gerät unterstützen muss. Beispielsweise können um debugging für ein Mobiltelefon zu ermöglichen, Sie eines portanbieters einrichten, die Ports, die Verbindung mit dem Mobiltelefon (z. B. über IR oder einer Zelle Verbindung), und listet die Prozesse und Programme stellt, die auf dem Telefon ausgeführt.  
  
 Für das Debuggen von Programmen auf Windows-basierten Computern (einschließlich Remotedebuggen) bietet Visual Studio Portanbieter für systemeigenen und Common Language Runtime (CLR)-Prozesse, daher keine Notwendigkeit besteht, um Ihre eigenen anschlusslieferant in diesen Fällen einzurichten.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Implementieren und Registrieren eines portanbieters](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md)  
 Erläutert, wie das SDM mit Anschlusslieferanten und ihrer Ports interagiert.  
  
 [Erforderliche Port Lieferanten-Schnittstellen](../../extensibility/debugger/required-port-supplier-interfaces.md)  
 Beschreibt die Schnittstellen, die Sie implementieren müssen, um eines portanbieters zu erhalten.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md)  
 Beschreibt die wichtigsten Konzepte für das Debuggen Architektur an.  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio-Debugger-Erweiterbarkeit](../../extensibility/debugger/visual-studio-debugger-extensibility.md)