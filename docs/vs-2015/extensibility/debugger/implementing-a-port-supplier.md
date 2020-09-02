---
title: Implementieren eines Port Anbieters | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ffa6daa20c08bd236657c88e762b2f453554cb74
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152676"
---
# <a name="implementing-a-port-supplier"></a>Implementieren eines Portanbieters
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ein Port Lieferant liefert Ports für die Anforderung an den Sitzungs-Debug-Manager (SDM). Beim Debuggen auf einen nicht-DCOM-Computer muss ein Port Lieferant implementiert werden, oder es muss ein neues Gerät unterstützt werden. Wenn Sie z. b. das Debuggen auf einem Mobiltelefon bereitstellen möchten, können Sie einen Port Anbieter implementieren, der Ports bereitstellt, die eine Verbindung mit dem Mobiltelefon herstellen (z. b. über IR oder eine Zell Verbindung) und die Prozesse und Programme auflisten, die auf dem Telefon ausgeführt werden.  
  
 Für das Debuggen von Programmen auf Windows-basierten Computern (einschließlich Remote Debuggen) stellt Visual Studio Port Lieferanten für systemeigene und CLR-Prozesse (Common Language Runtime) bereit, sodass in diesen Fällen kein eigener Port Lieferant implementiert werden muss.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Implementieren und Registrieren eines Portanbieters](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md)  
 Erläutert, wie die SDM mit dem Port Lieferanten und seinen Ports interagiert.  
  
 [Schnittstellen für erforderliche Portanbieter](../../extensibility/debugger/required-port-supplier-interfaces.md)  
 Dokumentiert die Schnittstellen, die implementiert werden müssen, um einen Port Lieferanten zu erhalten.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md)  
 Beschreibt die wichtigsten Konzepte der debuggingarchitektur.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Visual Studio Debugger-Erweiterbarkeit](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
