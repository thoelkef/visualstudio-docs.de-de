---
title: Portieren von Lieferanten | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e90871927c30399dea4691381baa749db2b3e8bf
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58958328"
---
# <a name="port-suppliers"></a>Portanbieter
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Im Hinblick auf die Debugger-Architektur eine **anschlusslieferant**:  
  
- Von einem Server enthalten ist, und bietet von Ports für die Anforderung für diesen Server.  
  
- Können hinzufügen und entfernen Sie die Ports auf dem Server enthält.  
  
- Alle Ports, die sie mit dem Server bereitgestellt wurde, können aufgezählt werden.  
  
- Wird durch dargestellt eine [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) -Schnittstelle, die mit Visual Studio über die Registrierung registriert ist. Diese Schnittstelle abgerufen werden kann, durch den Aufruf [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md).  
  
  [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] bietet eine Standard-anschlusslieferant und einen Standardport. Wenn ein benutzerdefinierter Port implementiert werden muss, muss ein benutzerdefinierten Port Lieferanten ebenfalls implementiert werden, um diese benutzerdefinierte Ports angeben.  
  
## <a name="see-also"></a>Siehe auch  
 [Server](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Ports](../../extensibility/debugger/ports.md)   
 [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
