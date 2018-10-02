---
title: Implementieren eines Portanbieters | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5d14c2642d30ee46df0cd1b766540ae0b135e4d4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47523319"
---
# <a name="implementing-a-port-supplier"></a>Implementieren eines Portanbieters
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Implementieren eines Portanbieters](https://docs.microsoft.com/visualstudio/extensibility/debugger/implementing-a-port-supplier).  
  
Ein portanbieters liefert Ports bei Anforderung an die sitzungsbasierter Debug-Manager (SDM). Ein portanbieters muss implementiert werden, wenn auf einen nicht-DCOM-Computer zu debuggen oder ein neues Gerät unterstützt werden muss. Um debugging für ein Mobiltelefon zu gewährleisten, können Sie z. B. ein portanbieters implementieren, das Ports, die das Handy (z. B. mithilfe von IR- oder einer Zelle Verbindung) verbinden, und listet die Prozesse und Programme bereitstellt, die auf dem Telefon ausgeführt.  
  
 Für das Debuggen von Programmen auf Windows-basierten Computern (einschließlich Remotedebuggen) bietet Visual Studio Portanbieter für systemeigenen und Common Language Runtime (CLR)-Prozesse, daher keine Notwendigkeit besteht, Ihre eigenen anschlusslieferant in diesen Fällen zu implementieren.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Implementieren und Registrieren eines Portanbieters](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md)  
 Erläutert, wie das SDM mit Anschlusslieferanten und ihrer Ports interagiert.  
  
 [Schnittstellen für erforderliche Portanbieter](../../extensibility/debugger/required-port-supplier-interfaces.md)  
 Beschreibt die Schnittstellen, die zum Abrufen eines portanbieters implementiert werden müssen.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md)  
 Beschreibt die wichtigsten Konzepte für das Debuggen Architektur an.  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio Debugger-Erweiterbarkeit](../../extensibility/debugger/visual-studio-debugger-extensibility.md)

