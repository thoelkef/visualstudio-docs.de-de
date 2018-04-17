---
title: Implementieren einen Port Lieferanten | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: b0743f307dc579f6197880b0b89acaf2db0dda08
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="implementing-a-port-supplier"></a>Implementieren einen Port Lieferanten
Ein Port gelieferte Ports auf Anforderung an die Sitzung Debug-Manager (SDM). Ein Port Lieferant muss implementiert werden, beim Debuggen von einem nicht-DCOM-Computer oder ein neues Gerät unterstützt werden muss. Beispielsweise könnten Sie zum Debuggen auf einem Mobiltelefon zu gewährleisten, einen Port Lieferanten implementieren, der Ports, die an das Mobiltelefon (z. B. mithilfe von IR- oder eine Zelle Verbindung) verbinden und listet die Prozesse und Programme bereitstellt, die auf dem Telefon ausgeführt.  
  
 Visual Studio bietet für das Debuggen von Programmen auf Windows-basierten Computern (einschließlich des Remotedebuggens) Port Lieferanten beim einheitlichen und Prozesse der Common Language Runtime (CLR), daher keine Notwendigkeit besteht, um Ihren eigenen Anschlusslieferanten in diesen Fällen zu implementieren.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Implementieren und Registrieren eines Portanbieters](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md)  
 Erläutert, wie die SDM mit Port Lieferanten und ihrer Ports interagiert.  
  
 [Schnittstellen für erforderliche Portanbieter](../../extensibility/debugger/required-port-supplier-interfaces.md)  
 Dokumentiert die Schnittstellen, die implementiert werden müssen, um einen Port Lieferanten zu erhalten.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md)  
 Beschreibt die wichtigsten Konzepte für das Debuggen Architektur.  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio Debugger-Erweiterbarkeit](../../extensibility/debugger/visual-studio-debugger-extensibility.md)